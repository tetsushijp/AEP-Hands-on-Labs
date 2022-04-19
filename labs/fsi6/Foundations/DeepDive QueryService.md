# Exercise  - Queries, queries, queries...and Data analysis

<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This will show examples of querying AEP data lake.
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

- Write queries for data analysis
- Write SQL queries combining web site and CRM data available in Adobe Experience Platform
- Learn about Adobe Defined Functions

## Lesson Context

In this exercises you will write queries to analyze product views, product funnels, churn etc.

All queries listed in this chapter will be executed in your **PSQL command-line interface**. You should copy (CTRL-c) the statement blocks indicated with **SQL** and paste (CTRL-v)them in the **PSQL command-line interface**. The **Query Result** blocks show the pasted SQL statement and the associated query result.

Please do not use Query Editor in AEP sandboxes to run these queries. They will not return the expected results.

## Exercise 1

Write basic queries for data analysis

### Top 5 pages viewed

What are the top 5 pages viewed?

**SQL**

```sql
select web.webPageDetails.name, count(*)
from   fsi_demo_data_pot_6_midvalues
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
       name          | count(1)
-------------------+----------
 home                |    83743
 purchase: step 1    |    45325
 purchase: step 2    |    33328
 search results      |    22272
 purchase: thank you |    21227
(5 rows)

all=>  
```



### Identify visitors (CRM ID and email address) who are looking for help (visit page => help)

**SQL**

```sql
select distinct _experience.analytics.customDimensions.eVars.eVar9, crm._adobedemoamericas270.identification.Email as emailAddress
from   fsi_demo_data_pot_6_midvalues aa,
crm_profile_dataset crm
where crm._adobedemoamericas270.identification.CRMID = aa._experience.analytics.customDimensions.eVars.eVar9
and web.webPageDetails.name = 'help' 
and _experience.analytics.customDimensions.eVars.eVar9 IS NOT NULL
limit 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all-> limit 10;
      evar9    |      emailAddress
------------------+-------------------------
 crmid:7085099 | tovarish1952@outlook.com
 crmid:4688992 | achaean1960@yahoo.com
 crmid:8575361 | colts2054@yandex.com
 crmid:2206049 | ragdoll1954@outlook.com
 crmid:2441715 | crureus1884@yahoo.com
 crmid:4594927 | woodpecker1915@yahoo.com
 crmid:8223201 | fiducial2045@live.com
 crmid:7386208 | levotartaric2025@gmail.com
 crmid:6483069 | achates1899@gmail.com
 crmid:3636957 | lanson2046@live.com
(10 rows)
all=> 
```

In the next set of queries we will extend the above query, in order to get a complete view on the customers and their behavior that have been visiting the "help" page. You will learn how to use the Adobe Defined Function to sessionize information, identify the sequence and timing of events. 

## Exercise 2

The majority of the business logic requires gathering the touchpoints for a customer and ordering them by time. This support is provided by Spark SQL in the form of window functions. Window functions are part of standard SQL and are supported by many other SQL engines.

### Adobe Defined Functions

Adobe has added a set of **Adobe Defined Functions** to the standard SQL syntax that allow you to better understand your experience data. In the next couple of queries you will learn about these ADF functions. You can find more information and the complete list via
[Adobe Experience League](https://experienceleague.adobe.com/docs/experience-platform/query/sql/adobe-defined-functions.html?lang=en#sql).

[//]: <> (broken link removed -> Adobe IO https://www.adobe.io/apis/experienceplatform/home/services/query-service/query-service.html#!acpdr/end-user/markdown/query-service/qs-queries-adobefunctions.md)

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
            select a.endUserIDs._experience.mcid.id as ecid,
                   a.timestamp,
                   web.webPageDetails.name as webPage,
                    SESS_TIMEOUT(timestamp, 60 * 30) 
                       OVER (PARTITION BY a.endUserIDs._experience.mcid.id
                             ORDER BY timestamp 
                             ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) 
                  AS session
            from   fsi_demo_data_pot_6_midvalues a
            where  a.endUserIDs._experience.mcid.id in ( 
                select b.endUserIDs._experience.mcid.id
                from   fsi_demo_data_pot_6_midvalues b
                where web.webPageDetails.name = 'help' 
				and b.endUserIDs._experience.mcid.id IS NOT NULL
            )
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
prod:all-> LIMIT 10;
 webPage 	   |         webPage_2          | webPage_3 |  webPage_4   | journeys
---------+----------------------------+-----------+--------------+--------------------
 home              | search results             | help      |              |        5
 home              | no location search results | help      |              |        4
 home              | edit account details       | help      |              |        4
 home              | update info                | help      | home         |        2
 home              | location search results    | help      | home         |        2
 home              | no location search results | help      | home         |        2
 home              | location search results    | help      |              |        2
 home              | tool: toolid22             | help      | articles     |        1
 location check in | service: service47         | help      |              |        1
 home              | service: service21         | help      | articles     |        1
(10 rows)
    

all=> 
```

### How much time do we have before a visitor calls the call center after visiting the "help" Page?

To answer this kind of query will we will use ``TIME_BETWEEN_NEXT_MATCH()`` Adobe Defined Function.

> Time-between previous or next match functions provide a new dimension, which measures the time that has elapsed since a particular incident.

**SQL**

```sql
select * from (
       select endUserIDs._experience.mcid.id as ecid,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='contact us', 'seconds')
              OVER(PARTITION BY endUserIDs._experience.mcid.id
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_us_after_seconds
       from   fsi_demo_data_pot_6_midvalues
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
prod:all-> limit 15;
                  ecid                  | webPage | contact_us_after_seconds
----------------------------------------+---------+----------------------------------
 65139124502948298803156531614258643756 | help    |                              -30
 66649610981445196224711646938596094441 | help    |                              -32
 68027651042594513463568912382624709949 | help    |                              -32
 76019626396529976292754170790284444840 | help    |                              -33
 75424204192345402470780614687917362522 | help    |                              -34
 76661521527769628166173448974936881688 | help    |                              -35
 91245401846255640644822288611808489972 | help    |                              -35
 69677910881601865524265215490043957204 | help    |                              -35
 70659556872747905387373988802185902326 | help    |                              -35
 63393373519022880338680665558865694006 | help    |                              -38
 89306763251445058691877169000356427088 | help    |                              -38
 68237579106120709922948600328313093565 | help    |                              -39
 90099710327187435702263514843195947829 | help    |                              -40
 71546782836375830748486573904035494034 | help    |                              -40
 86442452057742483562513748727810666739 | help    |                              -41
(15 rows)


all=> 
```


### What region are customers visiting from?

Lets include the geographical info, like longitude, lattitude, city, countrycode, captured by the Adobe Experience Platform in order to get some geographical insights about churning customers.

**SQL**

```sql
select distinct crm._adobedemoamericas270.identification.CRMID,
       r.city,
       r.countrycode,
       r.lat as latitude,
       r.lon as longitude,
       r.contact_us_after_seconds as seconds_to_contact_us       
from (
       select endUserIDs._experience.mcid.id ecid,
			_experience.analytics.customDimensions.eVars.eVar9 as crmid,
              placeContext.geo._schema.latitude lat,
              placeContext.geo._schema.longitude lon,
              placeContext.geo.city,
              placeContext.geo.countryCode,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='contact us', 'seconds')
              OVER(PARTITION BY endUserIDs._experience.mcid.id
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_us_after_seconds
       from   fsi_demo_data_pot_6_midvalues
       where  web.webPageDetails.name in ('help', 'contact us')
) r
, crm_profile_dataset crm
where crm._adobedemoamericas270.identification.CRMID = r.crmid
and r.webPage = 'help'
and  contact_us_after_seconds is not null
order by seconds_to_contact_us desc
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
 prod:all-> limit 15;
      crmid       |        city         | countrycode |      latitude       |      longitude      | seconds_to_contact_us
------------------+---------------------+-------------+---------------------+---------------------+-------------------------------
 crmid:2133727185 | monterrey           | MX          |  25.667099999999998 | -100.33699999999999 |                            -1
 crmid:8254082663 | perth               | AU          |            -31.9472 |             115.863 |                           -16
 crmid:9754491833 | antwerp             | BE          |             51.2288 |              4.4284 |                           -17
 crmid:3428751886 | copenhagen          | DK          |             55.6862 |             12.5891 |                           -30
 crmid:1886227231 | neuruppin           | DE          |             52.9225 |  12.806099999999999 |                           -34
 crmid:3304427019 | ogaki               | JP          |  35.387699999999995 |             136.629 |                           -41
 crmid:3002654182 | guayaquil           | EC          | -2.2044699999999997 |            -79.8962 |                           -43
 crmid:1853909148 | hong kong           | HK          |             22.2759 |             114.167 |                           -45
 crmid:5068058590 | rabat               | MA          |             34.0121 |            -6.83754 |                           -45
 crmid:2234687986 | chiba               | JP          |  35.626599999999996 |             140.065 |                           -46
 crmid:5994452115 | ?                   | EU          |              53.973 |               22.39 |                           -48
 crmid:5502020663 | parana              | AR          |            -31.7333 |            -60.5333 |                           -51
 crmid:5079558609 | zilina              | SK          |  49.223499999999994 |             18.7393 |                           -55
 crmid:6572225118 | les sables-d'olonne | FR          |                46.5 |            -1.80225 |                           -61
 crmid:2257033580 | budapest            | HU          |             47.4966 |             19.0114 |                           -67
(15 rows)

all=> 
```

### More SQL examples?

 - [Sample Analytics PSQL Queries](https://experienceleague.adobe.com/docs/experience-platform/query/samples/adobe-analytics.html?lang=en#samples)



## Lab Completed
Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi6/README.md#lab-agenda)

