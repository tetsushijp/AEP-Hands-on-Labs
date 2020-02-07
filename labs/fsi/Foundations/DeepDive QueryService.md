# Exercise  - Queries, queries, queries,... and Data analysis

## Objective

- Write queries for data analyses
- Write SQL queries combining online, callcenter and loyalty data avialable in Adobe Experience Platform
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
from   fsi_demo_data_postvalues
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
 2020-02-06 |        16320
 2020-02-05 |        20822
 2020-02-04 |        20773
 2020-02-03 |        30356
 2020-02-02 |        20708
 2020-02-01 |        11211
 2020-01-31 |        11212
 2020-01-30 |        20636
 2020-01-29 |        20735
 2020-01-28 |        20818
(10 rows)

all=> 
```

### Top 5 products viewed

What are the top 5 products viewed?

**SQL**

```sql
select web.webPageDetails.name, count(*)
from   fsi_demo_data_postvalues
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
       name        | count(1)
-------------------+----------
 home              |   680022
 purchase: step 1  |   478634
 purchase: step 2  |   347305
 app: launch       |   324601
 voice: app launch |   318831
(5 rows)

all=>  
```



### Identify visitors (CRM ID and email address) who are looking for help (visit page => help)

**SQL**

```sql
select distinct _experience.analytics.customDimensions.eVars.eVar9, crm._adobeamericaspot1.emailId as emailAddress
from   fsi_demo_data_postvalues aa,
crm_dataset crm
where crm._adobeamericaspot1.CRMID = aa._experience.analytics.customDimensions.eVars.eVar9
and web.webPageDetails.name = 'help' 
and _experience.analytics.customDimensions.eVars.eVar9 IS NOT NULL
limit 10;;
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

## Exercise 2

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
            from   fsi_demo_data_postvalues a
            where  a.endUserIDs._experience.mcid.id in ( 
                select b.endUserIDs._experience.mcid.id
                from   fsi_demo_data_postvalues b
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
 webPage |         webPage_2          | webPage_3 |  webPage_4   | journeys
---------+----------------------------+-----------+--------------+----------
 home    | edit account details       | help      | home         |       17
 home    | search results             | help      | home         |       17
 home    | no location search results | help      |              |       12
 home    | feedback                   | help      | home         |       10
 home    | edit account details       | help      | subscription |        9
 home    | no location search results | help      | home         |        8
 home    | edit account details       | help      | articles     |        7
 home    | feedback                   | help      |              |        6
 home    | search results             | help      | subscription |        6
 home    | blogs                      | help      |              |        6
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
              AS contact_callcenter_after_seconds
       from   fsi_demo_data_postvalues
       where  web.webPageDetails.name in ('help', 'contact us')
	   
) r
where r.webPage = 'help' 
and  contact_callcenter_after_seconds is not null
and ecid IS NOT NULL
order by contact_callcenter_after_seconds desc
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
prod:all-> limit 15;
                  ecid                  | webPage | contact_callcenter_after_seconds
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


### From what region do the visit us?

Lets include the geographical info, like longitude, lattitude, city, countrycode, captured by the Adobe Experience Platform in order to get some geographical insights about churning customers.

**SQL**

```sql
select distinct crm._adobeamericaspot1.crmid,
       r.city,
       r.countrycode,
       r.lat as latitude,
       r.lon as longitude,
       r.contact_callcenter_after_seconds as seconds_to_contact_callcenter       
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
              AS contact_callcenter_after_seconds
       from   fsi_demo_data_postvalues
       where  web.webPageDetails.name in ('help', 'contact us')
) r
, crm_dataset crm
where crm._adobeamericaspot1.crmid = r.crmid
and r.webPage = 'help'
and  contact_callcenter_after_seconds is not null
order by seconds_to_contact_callcenter desc
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
 prod:all-> limit 15;
      crmid       |        city         | countrycode |      latitude       |      longitude      | seconds_to_contact_callcenter
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

