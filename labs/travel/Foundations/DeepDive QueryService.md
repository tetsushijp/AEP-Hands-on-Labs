# Exercise  - Queries, queries, queries,... and Data analysis

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
from   travel_demo_data_midvalues
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
 2020-02-18 |        40791
 2020-02-17 |        29814
 2020-02-16 |         3482
 2020-02-15 |        59161
 2020-02-14 |        44334
 2020-02-13 |        60469
 2020-02-12 |        59922
 2020-02-11 |        60461
 2020-02-10 |        75166
 2020-02-09 |       102264
(10 rows)

all=> 
```

### Top 5 pages viewed

What are the top 5 pages viewed?

**SQL**

```sql
select web.webPageDetails.name, count(*)
from   travel_demo_data_midvalues
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
-----------------------+----------
 home                  |    59777
 OptinToLoyaltyProgram |    37338
 LoyaltyProgramPage    |    35502
 purchase: step 1      |    33348
 ViewProductDetailPage |    30345
(5 rows)

all=>  
```



### Identify visitors (CRM ID and email address) who are looking for help (visit page => help)

**SQL**

```sql
SELECT DISTINCT
   rd._adobeamericaspot3.identification.CRMID AS CRMIDs,
   crm._adobeamericaspot3.identification.Email as emailAddress
FROM
   reduced_web_ee_dataset AS rd,
   crm_profile_dataset AS crm
WHERE
   crm._adobeamericaspot3.identification.CRMID = rd._adobeamericaspot3.identification.CRMID
AND rd._adobeamericaspot3.webDetails.webPagename = 'help' 
AND rd._adobeamericaspot3.identification.CRMID IS NOT NULL
LIMIT 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all-> limit 10;
     CRMIDs       |      emailAddress
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
            select a.endUserIDs._experience.mcid.id as ecid,
                   a.timestamp,
                   web.webPageDetails.name as webPage,
                    SESS_TIMEOUT(timestamp, 60 * 30) 
                       OVER (PARTITION BY a.endUserIDs._experience.mcid.id
                             ORDER BY timestamp 
                             ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) 
                  AS session
            from   travel_demo_data_midvalues AS a
            where  a.endUserIDs._experience.mcid.id in ( 
                select b.endUserIDs._experience.mcid.id
                from   travel_demo_data_midvalues AS b
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
         webPage         |        webPage_2        | webPage_3 |        webPage_4        | journeys
-------------------------+-------------------------+-----------+-------------------------+----------
 home                    | search results          | help      |                         |        8
 home                    | feedback                | help      |                         |        3
 home                    | edit account details    | help      |                         |        3
 home                    | search results          | help      | articles                |        2
 home                    | update info             | help      | service: service41      |        1
 home                    | location search results | help      |                         |        1
 home                    | search results          | help      | help: helpid1046        |        1
 download: downloadid100 | subscription            | help      | download: downloadid149 |        1
 home                    | feedback                | help      | about us                |        1
 events                  | event details           | help      | service: service24      |        1
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
       from   travel_demo_data_midvalues

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
----------------------------------------+---------+--------------------------
 63823469114126614642345387152201006684 | help    |                      -90
 80754420904774428733506250839143369594 | help    |                      -90
 88377604148053432058816409689492601363 | help    |                      -97
 74984852109255501757734972488849276412 | help    |                     -116
 82687578684200753625403502085298173658 | help    |                     -201
 60824733890573918241826149831006075370 | help    |                     -873
 83087872889918868816169465668534057534 | help    |                   -13225
 64901031099876963442816840090228734226 | help    |                   -24569
 55022787637403064897181537130490186992 | help    |                   -47743
 72553521774911701091274051601998328318 | help    |                  -324629
 69409466322272568198835567698333577467 | help    |                  -381146
 77778980049255480192820597476957991241 | help    |                  -389988
 46681180103771127030304438795340301462 | help    |                  -390858
 50028126323920080091412027150929606017 | help    |                  -445806
 57977164580347900913210460396295142277 | help    |                  -635993

all=> 
```


### What region are customers visiting from?

Lets include the geographical info, like longitude, lattitude, city, countrycode, captured by the Adobe Experience Platform in order to get some geographical insights about churning customers.

**SQL**

```sql
select distinct crm._adobeamericaspot3.crmid,
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
       from   travel_demo_data_midvalues

       where  web.webPageDetails.name in ('help', 'contact us')
) r
, profile_dataset crm
where crm._adobeamericaspot3.crmid = r.crmid
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


Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/README.md#lab-agenda)

