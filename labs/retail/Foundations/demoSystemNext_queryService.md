# Exercise - Query Service

<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This will show a quick example of top cities in SQL
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>PSQL, if have not installed already follow instructions from <a href="https://www.adobe.io/apis/experienceplatform/home/query-service/connect.html#!api-specification/markdown/narrative/technical_overview/query-service/clients/psql.md">link here</a>
           </td>
     </tr>
</tbody>
</table>
</td>
</div>

<div align="right">
<td style="border: none;" valign="top">

<table>
<tbody valign="top">
      <tr>
            <td valign="middle" height="70"><b>section</b></td>
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_queries.png?raw=true" alt="Identities"></td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

## Objective

- Write queries for data analyses
- Write SQL queries combining web site and CRM data avialable in Adobe Experience Platform
- Learn about Adobe Defined Functions

## Lesson Context

In this exercises you will write queries to analyse product views, product funnels, churn etc.

All queries listed in this chapter will be executed in your **PSQL command-line interface**. You should copy (CTRL-c) the statement blocks indicated with **SQL** and paste (CTRL-v)them in the **PSQL command-line interface**. The **Query Result** blocks show the pasted SQL statement and the associated query result.

## Exercise 1

Write basic queries for data analysis

### Timestamp

Data captured in Adobe Experience Platform is time stamped. The "timestamp" attribute allows you to analyse data over time.

How many product views do we have on a daily basis?

**SQL**

```sql
select date_format( timestamp , 'yyyy-MM-dd') AS Day,
       count(*) AS productViews
from   demo_system_event_dataset_for_website_retail_v1_1
where  web.webPageDetails.pageViews.value = '1.0'
group by Day
order by day desc
limit 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
all-> limit 10;
    Day     | productViews
------------+--------------
 2020-04-01 |           52
 2020-03-31 |         1699
 2020-03-30 |         3716
 2020-03-29 |         1603
 2020-03-28 |         1891
 2020-03-27 |         1288
 2020-03-26 |         1574
 2020-03-25 |         2205
 2020-03-24 |         1667
 2020-03-23 |         2202
(10 rows)

all=>
```

### Top 5 pages viewed

What are the top 5 pages viewed?

**SQL**

```sql
select web.webPageDetails.name, count(*)
from   demo_system_event_dataset_for_website_retail_v1_1
where  web.webPageDetails.pageViews.value = '1.0'
group  by web.webPageDetails.name
order  by 2 desc
limit 5;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
all-> limit 5;
prod:all-> limit 5;
        name         | count(1)
---------------------+----------
 home                |     8751
 purchase: step 1    |     4718
 purchase: step 2    |     3399
 search results      |     2321
 purchase: thank you |     2155
(5 rows)

all=>
```

### Identify visitors (CRM ID and email address) who are looking for help (visit page => help)

**SQL**

```sql
select
aa._salesvelocity.identification.core.crmId,
crm._salesvelocity.identification.core.email as Email_Address
from
demo_system_event_dataset_for_website_retail_v1_1 aa,
demo_system_profile_dataset_for_crm_retail_v1_1 crm
where
crm._salesvelocity.identification.core.crmId = aa._salesvelocity.identification.core.crmId
and aa.web.webPageDetails.name = 'help'
and aa._salesvelocity.identification.core.crmId IS NOT NULL
limit 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all-> limit 10;
      evar9       |      emailAddress
------------------+-------------------------
 crmid:8969702846 | deceive2058@yahoo.com
 crmid:1704313209 | barbi1937@live.com
 crmid:2032196723 | sebasic1955@outlook.com
 crmid:6341221130 | larding1999@outlook.com
(4 rows)
all=>
```

In the next set of queries we will extend the above query, in order to get a complete view on the customers and their behavior that have been visiting the "Cancel Service" page. You will learn how to use the Adobe Defined Function to sessionize information, identify the sequence and timiong of events.

The majority of the business logic requires gathering the touchpoints for a customer and ordering them by time. This support is provided by Spark SQL in the form of window functions. Window functions are part of standard SQL and are supported by many other SQL engines.

### Adobe Defined Functions

Adobe has added a set of **Adobe Defined Functions** to the standard SQL syntax that allow you to better understand your experience data. In the next couple of queries you will learn about these ADF functions. You can find more information and the complete list via [Adobe IO](https://www.adobe.io/apis/experienceplatform/home/services/query-service/query-service.html#!acpdr/end-user/markdown/query-service/qs-queries-adobefunctions.md).

### What do people do on the site before reaching the "help" page as the 3rd page in a session?

With this query you will discover the first two Adobe Defined Functions **SESS_TIMEOUT** and **NEXT**

> The **SESS_TIMEOUT()** reproduces the visit groupings found with Adobe Analytics. It performs a similar time-based grouping, but customizable parameters.

> **NEXT()** and **PREVIOUS()** help you to understand how customers navigate your site.

**SQL**

```sql
SELECT
  webPage,
  webPage_2,
  webPage_3,
  webPage_4,
  count(*) journeys
FROM
  (
      SELECT
        webPage,
        NEXT(webPage, 1, true)
          OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_2,
        NEXT(webPage, 2, true)
          OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_3,
        NEXT(webPage, 3, true)
           OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_4,
        session.depth AS SessionPageDepth
      FROM (
            select a._salesvelocity.identification.core.ecid as ecid,
                   a.timestamp,
                   a.web.webPageDetails.name as webPage,
                    SESS_TIMEOUT(timestamp, 60 * 30)
                       OVER (PARTITION BY a._salesvelocity.identification.core.ecid
                             ORDER BY timestamp
                             ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
                  AS session
            from   demo_system_event_dataset_for_website_retail_v1_1 a
            where  a._salesvelocity.identification.core.ecid in (
                select b._salesvelocity.identification.core.ecid
                from   demo_system_event_dataset_for_website_retail_v1_1  b
                where b.web.webPageDetails.name = 'help'
				and b._salesvelocity.identification.core.ecid IS NOT NULL )
        )
)
WHERE SessionPageDepth=1
and   webpage_3 = 'help'
GROUP BY webPage, webPage_2, webPage_3, webPage_4
ORDER BY journeys DESC
LIMIT 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all->
      webPage      |         webPage_2          | webPage_3 |     webPage_4      | journeys
-------------------+----------------------------+-----------+--------------------+----------
 home              | location search results    | help      |                    |        2
 home              | search results             | help      |                    |        2
 sign in           | edit account details       | help      | service: service35 |        1
 home              | students                   | help      | service: service1  |        1
 lead form: step 1 | lead form: step 2          | help      | service: service1  |        1
 home              | blogs                      | help      | forum              |        1
 home              | feedback                   | help      | home               |        1
 home              | no location search results | help      | help: helpid1005   |        1
 home              | edit account details       | help      | service: service47 |        1
 home              | staff                      | help      | online chat        |        1
(10 rows)

all=>
```

### How much time do we have before a visitor calls the call center after visiting the "help" Page?

To answer this kind of query will we will use `TIME_BETWEEN_NEXT_MATCH()` Adobe Defined Function.

> Time-between previous or next match functions provide a new dimension, which measures the time that has elapsed since a particular incident.

**SQL**

```sql
select * from (
       select _salesvelocity.identification.core.ecid as ecid,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='contact us', 'seconds')
              OVER(PARTITION BY _salesvelocity.identification.core.ecid
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_us_after_seconds
       from   demo_system_event_dataset_for_website_retail_v1_1

       where  web.webPageDetails.name in ('help', 'contact us')

) r
where r.webPage = 'help'
and  contact_us_after_seconds is not null
and ecid IS NOT NULL
order by contact_us_after_seconds desc
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all->
               ecid                | webPage | contact_us_after_seconds
-----------------------------------+---------+--------------------------
 1695A01BBF285DEF-5027C02779607912 | help    |                      -35
 1366412EE238A6E1-63F15875707E2BCD | help    |                  -727929
 17EBD5EF8FBD92B1-17A21820C7F1D046 | help    |                 -1170316
 11DAE916DDDC1EE2-134FB3D00D20CFE2 | help    |                 -1379998

all=>
```
