

```sql
SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day,
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Count(DISTINCT enduserids._experience.aaid.id) AS Visitor_Count 
FROM   media_demo_data_postvalues
WHERE _acp_year = 2019
      AND _acp_month = 11  
      AND _acp_day = 03
GROUP BY Day, Hour
ORDER BY Hour;
```


output
---------------------------------------


```
    Day     | Hour | Visitor_Count
------------+------+---------------
 2019-11-03 | 00   |           381
 2019-11-03 | 01   |           746
 2019-11-03 | 02   |           392
 2019-11-03 | 03   |           405
 2019-11-03 | 04   |           526
 2019-11-03 | 05   |           647
 2019-11-03 | 06   |           724
 2019-11-03 | 07   |           855
 2019-11-03 | 08   |           968
 2019-11-03 | 09   |          1111
 2019-11-03 | 10   |          1217
 2019-11-03 | 11   |          1321
 2019-11-03 | 12   |          1428
 2019-11-03 | 13   |          1253
 2019-11-03 | 14   |          1278
 2019-11-03 | 15   |          1444
 2019-11-03 | 16   |          1551
 2019-11-03 | 17   |           652
 2019-11-03 | 18   |           626
 2019-11-02 | 20   |           408
 2019-11-02 | 21   |           343
 2019-11-02 | 22   |           353
 2019-11-02 | 23   |           383
(23 rows)
```


||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


```sql
SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day,
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Count(concat(enduserids._experience.aaid.id, 
                    _experience.analytics.session.num,
                    _experience.analytics.session.depth)) AS Count 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11  
       AND _acp_day = 03
GROUP BY Day, Hour
ORDER BY Hour;
```

output
-------------

```
    Day     | Hour | Count
------------+------+-------
 2019-11-03 | 00   |  2807
 2019-11-03 | 01   |  5691
 2019-11-03 | 02   |  2826
 2019-11-03 | 03   |  3079
 2019-11-03 | 04   |  3387
 2019-11-03 | 05   |  3677
 2019-11-03 | 06   |  4040
 2019-11-03 | 07   |  4327
 2019-11-03 | 08   |  4617
 2019-11-03 | 09   |  4984
 2019-11-03 | 10   |  5251
 2019-11-03 | 11   |  5517
 2019-11-03 | 12   |  5852
 2019-11-03 | 13   |  4686
 2019-11-03 | 14   |  4831
 2019-11-03 | 15   |  5115
 2019-11-03 | 16   |  5413
 2019-11-03 | 17   |  3591
 2019-11-03 | 18   |  3732
 2019-11-02 | 20   |  2748
 2019-11-02 | 21   |  2803
 2019-11-02 | 22   |  2859
 2019-11-02 | 23   |  2856
(23 rows)
```

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

```sql
SELECT concat(enduserids._experience.aaid.id, 
              '-#', 
              _experience.analytics.session.num) AS aaid_sess_key, 
       Count(timestamp) AS Count 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019 
       AND _acp_month = 11  
       AND _acp_day = 03
GROUP BY aaid_sess_key
ORDER BY Count DESC
LIMIT 10;
```

output
--------------------


```
            aaid_sess_key             | Count
--------------------------------------+-------
 200BD34B09230A64-374B6B58AEFC9907-#1 |   100
 2AB0B961AEE71181-5FE1FCE3922D30B5-#1 |   100
 295021997B6DD958-33D19E691267C847-#1 |   100
 69366435D4FE83C6-6C0680022920D184-#1 |   100
 6FE8B140E05591BA-487271197F6FD253-#2 |   100
 2880834B37F60F35-3D6A3A4456A56854-#1 |   100
 263BD756A3EFC3DF-22670DC8036DF2F-#1  |   100
 3F8F644986886A50-140EB3DD3B082952-#1 |   100
 4D2A7B5DD7ABB456-3C2A4025E208342D-#1 |   100
 132C887F3BA2CD1-15DB4B250F17DA47-#1  |   100
(10 rows)
```

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


```sql
SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10;
```
======================================================================== output

      Page_Name      | Page_Views
---------------------+------------
 home                |     6253.0
 purchase: step 1    |     4504.0
 purchase: step 2    |     3265.0
 app: launch         |     2534.0
 voice: app launch   |     2484.0
 purchase: thank you |     2295.0
 search results      |     1541.0
 app: navigation     |     1447.0
 app: category 1     |     1349.0
 voice: error        |     1233.0
(10 rows)

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


SELECT enduserids._experience.aaid.id AS aaid, 
       Count(timestamp) AS Count
FROM   {target_table}
WHERE  _acp_year = {target_year}
       AND _acp_month = {target_month}
       AND _acp_day = {target_day}
GROUP BY enduserids._experience.aaid.id
ORDER BY Count DESC
LIMIT  10;

++++++++++++++++++++++++++++++++++++++++++++++++++++++++ new version

SELECT enduserids._experience.aaid.id AS aaid, 
       Count(timestamp) AS Count
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY enduserids._experience.aaid.id
ORDER BY Count DESC
LIMIT  10;

=======================================================================

               aaid                | Count
-----------------------------------+-------
 6F57DB1C7670D14E-6F20959A389F2EB9 |   109
 2AB0B961AEE71181-5FE1FCE3922D30B5 |   100
 263BD756A3EFC3DF-22670DC8036DF2F  |   100
 69366435D4FE83C6-6C0680022920D184 |   100
 295021997B6DD958-33D19E691267C847 |   100
 498F0EF71185E2B7-76219CC01E691A55 |   100
 200BD34B09230A64-374B6B58AEFC9907 |   100
 240C64AB4DB131F9-743BB6758BE440D9 |   100
 6FE8B140E05591BA-487271197F6FD253 |   100
 53A5F54261F35AA3-1F9A299123ACB5DA |   100
(10 rows)

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


SELECT concat(placeContext.geo.stateProvince, ' - ', placeContext.geo.city) AS state_city, 
       Count(timestamp) AS Count
FROM   {target_table}
WHERE  _acp_year = {target_year}
       AND _acp_month = {target_month}
       AND _acp_day = {target_day}
GROUP BY state_city
ORDER BY Count DESC
LIMIT  10;

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT concat(placeContext.geo.stateProvince, ' - ', placeContext.geo.city) AS state_city, 
       Count(timestamp) AS Count
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY state_city
ORDER BY Count DESC
LIMIT  10;

============================================================================

    state_city    | Count
------------------+-------
 ca - san jose    | 17548
 va - ashburn     |  1719
 ny - new york    |  1271
 tx - houston     |   666
 wa - redmond     |   660
 la - monroe      |   651
 dc - washington  |   616
 tpe - taipei     |   568
 tx - san antonio |   553
 gd - shenzhen    |   519
(10 rows)

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems.sku) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   {target_table}
       WHERE  _acp_year = {target_year}
              AND _acp_month = {target_month}
              AND _acp_day = {target_day}
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems.sku) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

==========================================================================

ERROR 

ERROR:  ErrorCode: 08P01 sessionId: 606e5b2a-3796-4b61-8d53-847258930cf7 queryId: dc6282b8-eac6-4c3f-9a8e-0d24f0a574f8 Unknown error encountered. Reason: [Field "sku" does not exist.
Available fields: ]

NEED TO REVIST -- wrong in example code!

productListItems[].items

Version 2 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

================================

                                                                                           Product_SKU                                                                                           | Total_Product_Views
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------
 (prd1009,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp E)")",NULL,NULL)")",NULL,NULL)                   |                15.0
 (prd1006,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)")",NULL,NULL)     |                15.0
 (prd1019,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp E)")",NULL,NULL)")",NULL,NULL)                   |                12.0
 (prd1009,"("("("(::hash::0,::hash::0,Shoppable Media,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp E)")",NULL,NULL)")",NULL,NULL)          |                 9.0
 (prd1013,"("("("(::hash::0,::hash::0,Shoppable Media,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp G)")",NULL,NULL)")",NULL,NULL)          |                 8.0
 (prd1004,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)")",NULL,NULL)     |                 8.0
 (prd1006,"("("("(::hash::0,::hash::0,Cross-Sell,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)")",NULL,NULL) |                 8.0
 (prd1026,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp C)")",NULL,NULL)")",NULL,NULL)                   |                 8.0
 (prd1006,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp A)")",NULL,NULL)")",NULL,NULL)                   |                 8.0
 (prd1002,"("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp C)")",NULL,NULL)")",NULL,NULL)                   |                 8.0
(10 rows)


Version 3 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems.quantity) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

================================

 Product_SKU | Total_Product_Views
-------------+---------------------
             |              9777.0
(1 row)


Version 4 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems._experience) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

================================

                                                                                  Product_SKU                                                                                   | Total_Product_Views
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)")          |               244.0
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp C)")",NULL,NULL)")                        |               202.0
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp B - Most Viewed)")",NULL,NULL)")              |               187.0
 ("("("(::hash::0,::hash::0,Cross-Sell,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)")      |               167.0
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp E)")",NULL,NULL)")                        |               164.0
 ("("("(::hash::0,::hash::0,Shoppable Media,::hash::0,::hash::0,Recommendation Test,::hash::0,::hash::0,::hash::0,Recommendation Test: Exp A - Recently Viewed)")",NULL,NULL)") |               145.0
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp A)")",NULL,NULL)")                        |               123.0
 ("("("(::hash::0,::hash::0,Browse,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp P)")",NULL,NULL)")                        |               115.0
 ("("("(::hash::0,::hash::0,Cross-Sell,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp E)")",NULL,NULL)")                    |               110.0
 ("("("(::hash::0,::hash::0,Shoppable Media,::hash::0,::hash::0,Details Page MVT Test,::hash::0,::hash::0,::hash::0,Details Page MVT Test: Exp C)")",NULL,NULL)")               |               110.0
(10 rows)


Version 5 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems._experience.analytics.items) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

================================

ERROR going into other values....

Version 6 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems.items) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

================================

priceTotal

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


SELECT Purchase_ID, 
       Round(Sum(Product_Items.priceTotal * Product_Items.quantity), 2) AS Total_Order_Revenue 
FROM   (SELECT commerce.`order`.purchaseid AS Purchase_ID, 
               Explode(productlistitems)   AS Product_Items 
        FROM   {target_table} 
        WHERE  commerce.`order`.purchaseid IS NOT NULL 
               AND _acp_year = {target_year} 
               AND _acp_month = {target_month}  
               AND _acp_day = {target_day}) 
GROUP BY Purchase_ID 
ORDER BY total_order_revenue DESC 
LIMIT  10;

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Purchase_ID, 
       Round(Sum(Product_Items.priceTotal * Product_Items.quantity), 2) AS Total_Order_Revenue 
FROM   (SELECT commerce.`order`.purchaseid AS Purchase_ID, 
               Explode(productlistitems)   AS Product_Items 
        FROM   media_demo_data_postvalues
        WHERE  commerce.`order`.purchaseid IS NOT NULL 
               AND _acp_year = 2019 
               AND _acp_month = 11
               AND _acp_day = 03 )
GROUP BY Purchase_ID 
ORDER BY total_order_revenue DESC 
LIMIT  10;

===========================================================================

     Purchase_ID      | Total_Order_Revenue
----------------------+---------------------
 cid:1572815155410    |          2272158.48
 cid:1572784399629    |           1930813.0
 14707890962721362573 |          1865207.18
 6021771892721362573  |          1865207.18
 cid:1572791668504    |           937643.25
 cid:1572824096852    |            525559.9
 cid:1572787091676    |           260452.23
 2696676371269724307  |            227677.4
 19615863161269724307 |           227284.95
 cid:1572778701317    |           222325.24
(10 rows)

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

SELECT _experience.analytics.customdimensions.evars.{target_evar} AS {target_evar},
       Count(_experience.analytics.customdimensions.evars.{target_evar}) AS Instances
FROM   {target_table_post_values}
WHERE  _experience.analytics.customdimensions.evars.{target_evar} IS NOT NULL 
        AND _acp_year = {target_year} 
        AND _acp_month = {target_month}  
        AND _acp_day = {target_day}
GROUP BY _experience.analytics.customdimensions.evars.{target_evar} 
ORDER BY instances DESC 
LIMIT  10;


++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


SELECT _experience.analytics.customdimensions.evars.evar9 AS evar9,
       Count(_experience.analytics.customdimensions.evars.evar9) AS Instances
FROM   media_demo_data_postvalues
WHERE  _experience.analytics.customdimensions.evars.evar9 IS NOT NULL 
        AND _acp_year = 2019
        AND _acp_month = 11 
        AND _acp_day = 03
GROUP BY _experience.analytics.customdimensions.evars.evar9
ORDER BY instances DESC 
LIMIT  10;

=============================================================================

      evar9       | Instances
------------------+-----------
 crmid:8931378835 |       159
 crmid:5865354734 |       152
 crmid:2831519378 |       134
 crmid:5041118628 |       123
 crmid:1751760248 |       102
 crmid:1016305465 |       101
 crmid:2090574642 |       100
 crmid:3924764509 |       100
 crmid:1845033212 |       100
 crmid:9508220862 |       100
(10 rows)


|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day, 
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Sum(_experience.analytics.event1to100.{target_event}.value) AS Event_Count
FROM   {target_table}
WHERE  _experience.analytics.event1to100.{target_event}.value IS NOT NULL 
        AND _acp_year = {target_year} 
        AND _acp_month = {target_month}  
        AND _acp_day = {target_day}
GROUP BY Day, Hour
ORDER BY Hour;




+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day, 
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Sum(_experience.analytics.event1to100.event59.value) AS Event_Count
FROM   media_demo_data_postvalues
WHERE  _experience.analytics.event1to100.event59.value IS NOT NULL 
        AND _acp_year = 2019 
        AND _acp_month = 11 
        AND _acp_day = 03
GROUP BY Day, Hour
ORDER BY Hour;


==============================================================================

    Day     | Hour | Event_Count
------------+------+-------------
 2019-11-03 | 00   |        15.0
 2019-11-03 | 01   |        23.0
 2019-11-03 | 02   |        15.0
 2019-11-03 | 03   |        12.0
 2019-11-03 | 04   |        12.0
 2019-11-03 | 05   |        13.0
 2019-11-03 | 06   |        12.0
 2019-11-03 | 07   |        17.0
 2019-11-03 | 08   |        11.0
 2019-11-03 | 09   |        16.0
 2019-11-03 | 10   |        20.0
 2019-11-03 | 11   |        16.0
 2019-11-03 | 12   |        24.0
 2019-11-03 | 13   |        10.0
 2019-11-03 | 14   |        11.0
 2019-11-03 | 15   |        17.0
 2019-11-03 | 16   |         8.0
 2019-11-03 | 17   |        10.0
 2019-11-03 | 18   |        14.0
 2019-11-02 | 20   |         8.0
 2019-11-02 | 21   |         7.0
 2019-11-02 | 22   |        10.0
 2019-11-02 | 23   |         9.0
(23 rows)


###################################################################


SELECT _experience.analytics.customDimensions.lists.list1 AS listvar01,
       Count(_experience.analytics.customDimensions.lists.list1) AS Instances
FROM   media_demo_data_postvalues
WHERE  _experience.analytics.customDimensions.lists.list1 IS NOT NULL 
        AND _acp_year = 2019
        AND _acp_month = 11 
        AND _acp_day = 03
GROUP BY _experience.analytics.customDimensions.lists.list1
ORDER BY instances DESC 
LIMIT  10;

===========================================================


           listvar01                                                                                                                                                                                                                                                                                                                                                                                   | Instances
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------
 ("{(adid-113|),(adid-147|),(adid-169|),(adid-187|),(adid-103|),(adid-126|),(adid-189|),(adid-171|),(adid-179|),(adid-157|),(adid-130|),(adid-166|),(adid-136|),(adid-110|),(adid-188|),(adid-163|),(adid-108|),(adid-111|),(adid-159|),(adid-164|),(adid-182|),(adid-196|),(adid-155|),(adid-150|),(adid-137|),(adid-148|),(adid-195|),(adid-131|),(adid-118|),(adid-123|),(adid-117|),(adid-158|),(adid-127|),(adid-105|),(adid-109|),(adid-149|),(adid-125|),(adid-193|),(adid-184|),(adid-176|),(adid-106|),(adid-100|),(adid-104|),(adid-146|),(adid-173|),(adid-120|),(adid-172|),(adid-144|)}")                                                                                                                                                                         |        19
 ("{(adid-169|),(adid-156|),(adid-159|),(adid-103|),(adid-167|),(adid-191|),(adid-179|),(adid-145|),(adid-154|),(adid-128|),(adid-152|),(adid-182|),(adid-190|),(adid-120|),(adid-183|),(adid-105|),(adid-116|)}")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |        18
 ("{(adid-143|),(adid-150|),(adid-189|),(adid-184|),(adid-121|),(adid-131|),(adid-182|),(adid-196|),(adid-166|),(adid-128|),(adid-148|),(adid-167|),(adid-175|),(adid-103|),(adid-113|),(adid-119|),(adid-130|),(adid-147|),(adid-151|),(adid-126|),(adid-111|),(adid-163|),(adid-159|),(adid-195|),(adid-142|),(adid-154|),(adid-141|),(adid-114|),(adid-124|),(adid-110|),(adid-127|),(adid-118|),(adid-115|),(adid-138|),(adid-122|),(adid-116|),(adid-106|),(adid-145|),(adid-135|),(adid-155|),(adid-188|),(adid-123|),(adid-105|),(adid-176|),(adid-109|),(adid-100|),(adid-107|),(adid-174|),(adid-179|),(adid-149|),(adid-146|),(adid-172|),(adid-101|),(adid-102|),(adid-187|),(adid-117|),(adid-139|),(adid-183|),(adid-165|),(adid-164|),(adid-193|),(adid-170|)}") |        17
 ("{(adid-105|),(adid-139|),(adid-100|),(adid-150|),(adid-163|),(adid-179|),(adid-190|),(adid-193|),(adid-116|),(adid-195|),(adid-153|),(adid-176|),(adid-124|),(adid-128|),(adid-182|),(adid-123|),(adid-171|),(adid-166|),(adid-132|),(adid-172|),(adid-169|),(adid-198|),(adid-155|),(adid-158|),(adid-142|),(adid-165|),(adid-177|),(adid-109|),(adid-148|),(adid-154|),(adid-103|),(adid-168|),(adid-118|),(adid-188|),(adid-115|),(adid-127|),(adid-174|),(adid-133|),(adid-106|),(adid-159|),(adid-134|),(adid-143|),(adid-170|),(adid-145|),(adid-141|),(adid-131|),(adid-189|),(adid-104|)}")                                                                                                                                                                         |        17
 ("{(adid-186|),(adid-169|),(adid-118|),(adid-138|),(adid-159|),(adid-109|),(adid-107|),(adid-105|),(adid-168|),(adid-163|),(adid-103|),(adid-117|),(adid-134|),(adid-177|),(adid-101|),(adid-155|),(adid-113|),(adid-172|),(adid-175|),(adid-102|),(adid-131|),(adid-145|),(adid-100|),(adid-187|),(adid-166|),(adid-146|),(adid-112|),(adid-149|),(adid-151|),(adid-190|),(adid-154|),(adid-171|),(adid-182|),(adid-189|),(adid-141|),(adid-129|)}")                                                                                                                                                                                                                                                                                                                         |        16


 MODIFY!!!


SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems._experience) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_postvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;





SELECT _experience.analytics.customDimensions.lists.list1 AS listvar01,
       Count(_experience.analytics.customDimensions.lists.list1) AS Instances
FROM   media_demo_data_postvalues
WHERE  _experience.analytics.customDimensions.lists.list1 IS NOT NULL 
        AND _acp_year = 2019
        AND _acp_month = 11 
        AND _acp_day = 03
GROUP BY _experience.analytics.customDimensions.lists.list1
ORDER BY instances DESC 
LIMIT  10;



SELECT listvar01, Instances
FROM  (SELECT Explode(_experience.analytics.customDimensions.lists.list1.list) AS listvar01,
           Sum(_experience.analytics.customDimensions.lists.list1.list) AS Instances
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03 )
GROUP BY listvar01
ORDER BY Instances DESC
LIMIT  10;


SELECT Explode(_experience.analytics.customDimensions.lists.list1) AS listvar01 
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
LIMIT  10;



WORKS (a bit)..................................................................................
SELECT Explode(_experience.analytics.customDimensions.lists.list1.list) AS listvar01
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03
LIMIT  10;



_experience.analytics.customDimensions.lists.list1.value



))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))

SELECT endUserIds._experience.mcid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_FIRST_TOUCH(timestamp, 'Paid First', marketing.trackingCode)
      OVER(PARTITION BY endUserIds._experience.mcid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS first_touch
FROM experience_events
ORDER BY endUserIds._experience.mcid.id, timestamp ASC
LIMIT 10

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

SELECT endUserIds._experience.mcid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_FIRST_TOUCH(timestamp, 'Paid First', marketing.trackingCode)
      OVER(PARTITION BY endUserIds._experience.mcid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS first_touch
FROM media_demo_data_postvalues
ORDER BY endUserIds._experience.mcid.id, timestamp ASC
LIMIT 10;


=========================

 id |       timestamp       |       trackingcode        |                           first_touch
----+-----------------------+---------------------------+------------------------------------------------------------------
    | 2019-10-23 20:00:08.0 | soc_referral: Twitter:t12 | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:16.0 | soc:10065-a               | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:17.0 | sms:10099-a               | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:17.0 | da:10003-c                | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:17.0 | sem:10006-a               | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:20.0 | pdcid:10063-c             | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:25.0 | pdcid:10081-a             | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:34.0 | nat_search:Yahoo:kwd62    | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:35.0 | pdcid:10043-b             | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
    | 2019-10-23 20:00:50.0 | sem:10006-a               | (Paid First,soc_referral: Twitter:t12,2019-10-23 20:00:08.0,1.0)
(10 rows)



_++++++++++++++++++++++++++++++++++++_+_+_+_+_+_+__+_+


SELECT listvar01,
     Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(_experience.analytics.customDimensions.lists.list1.list) AS listvar01,
           Count(1) AS Product_Views
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 03 )
GROUP BY listvar01
ORDER BY Product_Views DESC
LIMIT  10;


===================================


SELECT 
    date_format( from_utc_timestamp(timestamp, 'EDT') , 'yyyy-MM-dd') as Day,
   SUM(web.webPageDetails.pageviews.value) as pageViews,
   SUM(_experience.analytics.event1to100.event1.value) as A,
   SUM(_experience.analytics.event1to100.event2.value) as B,
   SUM(_experience.analytics.event1to100.event3.value) as C,
   SUM(
     CASE 
        WHEN _experience.analytics.customDimensions.evars.evar1 = 'parkas' 
        THEN 1 
        ELSE 0 
      END) as viewedParkas
  FROM your_analytics_table 
  WHERE _ACP_YEAR = 2018 AND _ACP_MONTH = 3 
  GROUP BY Day 
  ORDER BY Day ASC, pageViews DESC;

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT date_format( from_utc_timestamp(timestamp, 'EDT') , 'yyyy-MM-dd') as Day,
SUM(web.webPageDetails.pageviews.value) as pageViews,
SUM(_experience.analytics.event1to100.event11.value) as A,
SUM(_experience.analytics.event1to100.event20.value) as B,
SUM(_experience.analytics.event1to100.event33.value) as C,
SUM(
     CASE 
        WHEN _experience.analytics.customDimensions.evars.evar33 = 'a' 
        THEN 1 
        ELSE 0 
      END) as population_a
FROM media_demo_data_midvalues 
WHERE _ACP_YEAR = 2019 AND _ACP_MONTH = 11 
GROUP BY Day 
ORDER BY Day ASC, pageViews DESC;

^ this works fine

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SELECT Product_SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems.SKU) AS Product_SKU, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 4
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY Product_SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

FIXED CODE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

SELECT Product.SKU SKU,
       Sum(Product_Views) AS Total_Product_Views
FROM  (SELECT Explode(productlistitems) AS Product, 
              commerce.productviews.value   AS Product_Views 
       FROM   media_demo_data_midvalues
       WHERE  _acp_year = 2019
              AND _acp_month = 11
              AND _acp_day = 4
              AND commerce.productviews.value IS NOT NULL) 
GROUP BY SKU 
ORDER BY Total_Product_Views DESC
LIMIT  10;

^^^ Yippeee this works too!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!





~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SELECT sonic_dataset_adobeamericaspot2.subscription_status as AccountStatus,
       COUNT(timestamp) AS Events 
FROM   sonic_dataset
WHERE  _acp_year = 2019
       AND _acp_month = 11
LIMIT  10;

^ bad

, 


SELECT sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus,
       Count(sonic_dataset._adobeamericaspot2.subscription_status) AS Count
FROM   sonic_dataset
WHERE  _acp_year = 2019
GROUP BY AccountStatus 
ORDER BY Count DESC
LIMIT  10;

^ works

SELECT sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus
FROM   sonic_dataset
LIMIT  10;

^ works


SELECT sonic_dataset.timestamp as RawTimestamps
FROM   sonic_dataset
LIMIT  10;

^ works

SELECT date(sonic_dataset.timestamp) as DateRawTimestamps
FROM   sonic_dataset
LIMIT  10;

^ works


SELECT Substring(from_utc_timestamp(sonic_dataset.timestamp, 'America/New_York'), 1, 10) AS Day,
       sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus,
       Count(sonic_dataset._adobeamericaspot2.subscription_status) AS Count
FROM   sonic_dataset
WHERE  _acp_year = 2019
GROUP BY Day
ORDER BY Day;



LIMIT  10;





SELECT sonic_dataset._ACP_DAY AS Day,
       sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus,
       Count(sonic_dataset._adobeamericaspot2.subscription_status) AS Count
FROM   sonic_dataset
WHERE  _acp_year = 2019
GROUP BY Day
ORDER BY Day
LIMIT  10;


^^^^^^^^^^^^ not working




SELECT sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus,
       concat(sonic_dataset._ACP_YEAR,'-',sonic_dataset._ACP_MONTH,'-',sonic_dataset._ACP_DAY) as Date,
       count(sonic_dataset._adobeamericaspot2.subscription_status) as Count
FROM   sonic_dataset
GROUP BY AccountStatus
ORDER BY Date ASC, Count DESC;
LIMIT  10;

AccountStatus  |   Date        |   Count
========================================
ACTIVE         |   2019-10-11  |   100
INACTIVE       |   2019-10-11  |   30
ACTIVE         |   2019-10-12  |   230
INACTIVE       |   2019-10-12  |   740


concat(enduserids._experience.aaid.id, 
              '-#', 
              _experience.analytics.session.num) AS aaid_sess_key, 


MODIFICATIONS


SELECT sonic_dataset._adobeamericaspot2.subscription_status as AccountStatus,
       date(sonic_dataset.timestamp) as Date,
       count(sonic_dataset._adobeamericaspot2.subscription_status) as Count
FROM   sonic_dataset
GROUP BY AccountStatus, Date
ORDER BY Date ASC, Count DESC
LIMIT  10;

^^^^ cool, this works now




SELECT 
  b._adobeamericaspot2.subscription_status AS AccountStatus,
  SUM(a.web.webPageDetails.pageviews.value) AS PageViews
FROM media_demo_data_postvalues a 
     JOIN sonic_dataset b 
      ON a._experience.analytics.customdimensions.evars.evar9 = b._adobeamericaspot2.crmId
WHERE a._ACP_YEAR = 2019 
GROUP BY AccountStatus 
ORDER BY PageViews DESC
LIMIT 50;


^^^ this works




SELECT 
  b._adobeamericaspot2.crmId AS crmId,
  SUM(a.web.webPageDetails.pageviews.value) AS PageViews
FROM media_demo_data_postvalues a 
     JOIN sonic_dataset b 
      ON a._experience.analytics.customdimensions.evars.evar9 = b._adobeamericaspot2.crmId
WHERE a._ACP_YEAR = 2019 
GROUP BY crmId 
ORDER BY PageViews DESC
LIMIT 50;






####################################################################
####################################################################
########                                                    ########
########           Simple/Moderate Queries                  ########
########                                                    ########
####################################################################
####################################################################


====================================================================
=====                         Example #1                       =====
====================================================================


# SQL
####################################################################

SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day,
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Count(DISTINCT enduserids._experience.aaid.id) AS Visitor_Count 
FROM   media_demo_data_postvalues
WHERE _acp_year = 2019
      AND _acp_month = 11  
      AND _acp_day = 03
GROUP BY Day, Hour
ORDER BY Hour;





# OUTPUT
####################################################################

    Day     | Hour | Visitor_Count
------------+------+---------------
 2019-11-03 | 00   |           381
 2019-11-03 | 01   |           746
 2019-11-03 | 02   |           392
 2019-11-03 | 03   |           405
 2019-11-03 | 04   |           526
 2019-11-03 | 05   |           647
 2019-11-03 | 06   |           724
 2019-11-03 | 07   |           855
 2019-11-03 | 08   |           968
 2019-11-03 | 09   |          1111
 2019-11-03 | 10   |          1217
 2019-11-03 | 11   |          1321
 2019-11-03 | 12   |          1428
 2019-11-03 | 13   |          1253
 2019-11-03 | 14   |          1278
 2019-11-03 | 15   |          1444
 2019-11-03 | 16   |          1551
 2019-11-03 | 17   |           652
 2019-11-03 | 18   |           626
 2019-11-02 | 20   |           408
 2019-11-02 | 21   |           343
 2019-11-02 | 22   |           353
 2019-11-02 | 23   |           383
(23 rows)






====================================================================
=====                         Example #2                       =====
====================================================================



# SQL
####################################################################

SELECT Substring(from_utc_timestamp(timestamp, 'America/New_York'), 1, 10) AS Day,
       Substring(from_utc_timestamp(timestamp, 'America/New_York'), 12, 2) AS Hour, 
       Count(concat(enduserids._experience.aaid.id, 
                    _experience.analytics.session.num,
                    _experience.analytics.session.depth)) AS Count 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11  
       AND _acp_day = 03
GROUP BY Day, Hour
ORDER BY Hour;





# OUTPUT
####################################################################

    Day     | Hour | Count
------------+------+-------
 2019-11-03 | 00   |  2807
 2019-11-03 | 01   |  5691
 2019-11-03 | 02   |  2826
 2019-11-03 | 03   |  3079
 2019-11-03 | 04   |  3387
 2019-11-03 | 05   |  3677
 2019-11-03 | 06   |  4040
 2019-11-03 | 07   |  4327
 2019-11-03 | 08   |  4617
 2019-11-03 | 09   |  4984
 2019-11-03 | 10   |  5251
 2019-11-03 | 11   |  5517
 2019-11-03 | 12   |  5852
 2019-11-03 | 13   |  4686
 2019-11-03 | 14   |  4831
 2019-11-03 | 15   |  5115
 2019-11-03 | 16   |  5413
 2019-11-03 | 17   |  3591
 2019-11-03 | 18   |  3732
 2019-11-02 | 20   |  2748
 2019-11-02 | 21   |  2803
 2019-11-02 | 22   |  2859
 2019-11-02 | 23   |  2856
(23 rows)



====================================================================
=====                         Example #3                       =====
====================================================================



# SQL
####################################################################

SELECT concat(enduserids._experience.aaid.id, 
              '-#', 
              _experience.analytics.session.num) AS aaid_sess_key, 
       Count(timestamp) AS Count 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019 
       AND _acp_month = 11  
       AND _acp_day = 03
GROUP BY aaid_sess_key
ORDER BY Count DESC
LIMIT 10;





# OUTPUT
####################################################################

            aaid_sess_key             | Count
--------------------------------------+-------
 200BD34B09230A64-374B6B58AEFC9907-#1 |   100
 2AB0B961AEE71181-5FE1FCE3922D30B5-#1 |   100
 295021997B6DD958-33D19E691267C847-#1 |   100
 69366435D4FE83C6-6C0680022920D184-#1 |   100
 6FE8B140E05591BA-487271197F6FD253-#2 |   100
 2880834B37F60F35-3D6A3A4456A56854-#1 |   100
 263BD756A3EFC3DF-22670DC8036DF2F-#1  |   100
 3F8F644986886A50-140EB3DD3B082952-#1 |   100
 4D2A7B5DD7ABB456-3C2A4025E208342D-#1 |   100
 132C887F3BA2CD1-15DB4B250F17DA47-#1  |   100
(10 rows)




====================================================================
=====                         Example #3                       =====
====================================================================



# SQL
####################################################################


SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10;




# OUTPUT
####################################################################

      Page_Name      | Page_Views
---------------------+------------
 home                |     6253.0
 purchase: step 1    |     4504.0
 purchase: step 2    |     3265.0
 app: launch         |     2534.0
 voice: app launch   |     2484.0
 purchase: thank you |     2295.0
 search results      |     1541.0
 app: navigation     |     1447.0
 app: category 1     |     1349.0
 voice: error        |     1233.0
(10 rows)



####################################################################






####################################################################
####
#### Example #1
####




SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10; >> C:\AEP\Discovery\filehere.txt



\copy (SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10;

) To 'C:\AEP\Discovery\filehere.txt' With CSV



\copy (SELECT web.webpagedetails.name AS Page_Name, Sum(web.webpagedetails.pageviews.value) AS Page_Views FROM media_demo_data_postvalues WHERE  _acp_year = 2019 AND _acp_month = 11 AND _acp_day = 03 GROUP BY web.webpagedetails.name ORDER BY page_views DESC LIMIT  10) To 'C:\AEP\Discovery\filehere.txt' With CSV


\copy (SELECT web.webpagedetails.name AS Page_Name, Sum(web.webpagedetails.pageviews.value) AS Page_Views FROM media_demo_data_postvalues WHERE  _acp_year = 2019 AND _acp_month = 11 AND _acp_day = 03 GROUP BY web.webpagedetails.name ORDER BY page_views DESC LIMIT  10) To 'C:/AEP/Discovery/filehere2.txt' With CSV


copy (SELECT web.webpagedetails.name AS Page_Name, Sum(web.webpagedetails.pageviews.value) AS Page_Views FROM media_demo_data_postvalues WHERE  _acp_year = 2019 AND _acp_month = 11 AND _acp_day = 03 GROUP BY web.webpagedetails.name ORDER BY page_views DESC LIMIT  10) To 'C:/AEP/Discovery/filehere2.txt'


\t \a \g (SELECT web.webpagedetails.name AS Page_Name, Sum(web.webpagedetails.pageviews.value) AS Page_Views FROM media_demo_data_postvalues WHERE  _acp_year = 2019 AND _acp_month = 11 AND _acp_day = 03 GROUP BY web.webpagedetails.name ORDER BY page_views DESC LIMIT  10) To 'C:/AEP/Discovery/filehere3.txt With CSV

 With CSV


 -t -A -F"," -c "select * from users" > output.csv



SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10; \g 'C:/AEP/Discovery/filehere4.txt'

^ works!



\f ',' \a \o 'C:/AEP/Discovery/filehere7.txt'
SELECT web.webpagedetails.name AS Page_Name, 
       Sum(web.webpagedetails.pageviews.value) AS Page_Views 
FROM   media_demo_data_postvalues
WHERE  _acp_year = 2019
       AND _acp_month = 11
       AND _acp_day = 03
GROUP BY web.webpagedetails.name 
ORDER BY page_views DESC 
LIMIT  10;



(SELECT web.webpagedetails.name AS Page_Name, Sum(web.webpagedetails.pageviews.value) AS Page_Views FROM media_demo_data_postvalues WHERE  _acp_year = 2019 AND _acp_month = 11 AND _acp_day = 03 GROUP BY web.webpagedetails.name ORDER BY page_views DESC LIMIT  10) \f ',' \a \o 'C:/AEP/Discovery/filehere4.txt'
















**********************************************************************

SELECT endUserIds._experience.mcid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_FIRST_TOUCH(timestamp, 'Paid First', marketing.trackingCode)
      OVER(PARTITION BY endUserIds._experience.mcid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS first_touch
FROM media_demo_data_postvalues
ORDER BY endUserIds._experience.mcid.id, timestamp ASC
LIMIT 10;

************************************************************************

SELECT enduserids._experience.aaid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_FIRST_TOUCH(timestamp, 'Paid First', marketing.trackingCode)
      OVER(PARTITION BY enduserids._experience.aaid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS first_touch
FROM media_demo_data_postvalues
ORDER BY enduserids._experience.aaid.id, timestamp ASC
LIMIT 10;

************************************************************************

SELECT endUserIds._experience.mcid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH(timestamp, 'trackingCode', marketing.trackingCode)
      OVER(PARTITION BY endUserIds._experience.mcid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM experience_events
ORDER BY endUserIds._experience.mcid.id, timestamp ASC



SELECT enduserids._experience.aaid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH(timestamp, 'trackingCode', marketing.trackingCode)
      OVER(PARTITION BY enduserids._experience.aaid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
ORDER BY enduserids._experience.aaid.id, timestamp ASC
LIMIT 10;




!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

SELECT 
  page_name,
  SUM (time_between_previous_match) / COUNT(page_name) as average_minutes_since_registration
FROM
(
SELECT 
  endUserIds._experience.mcid.id as id, 
  timestamp, web.webPageDetails.name as page_name, 
  TIME_BETWEEN_PREVIOUS_MATCH(timestamp, web.webPageDetails.name='Account Registration|Confirmation', 'minutes')
    OVER(PARTITION BY endUserIds._experience.mcid.id
       ORDER BY timestamp
       ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
    AS time_between_previous_match
FROM experience_events
)
WHERE time_between_previous_match IS NOT NULL
GROUP BY page_name
ORDER BY average_minutes_since_registration
LIMIT 10



SELECT 
  page_name,
  (SUM (time_between_previous_match) * 100) / COUNT(page_name) as average_minutes_since_registration
FROM
(
SELECT 
  enduserids._experience.aaid.id as id, 
  timestamp, web.webPageDetails.name as page_name, 
  TIME_BETWEEN_PREVIOUS_MATCH(timestamp, web.webPageDetails.name='purchase: thank you', 'minutes')
    OVER(PARTITION BY enduserids._experience.aaid.id
       ORDER BY timestamp
       ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
    AS time_between_previous_match
FROM media_demo_data_postvalues
)
WHERE time_between_previous_match IS NOT NULL
GROUP BY page_name
ORDER BY average_minutes_since_registration
LIMIT 50;




SELECT 
  page_name,
  SUM (time_between_previous_match) / COUNT(page_name) as average_minutes_since_registration
FROM
(
SELECT 
  enduserids._experience.aaid.id as id, 
  timestamp, web.webPageDetails.name as page_name, 
  TIME_BETWEEN_PREVIOUS_MATCH(timestamp, web.webPageDetails.name='app: purchase confirmation', 'minutes')
    OVER(PARTITION BY enduserids._experience.aaid.id
       ORDER BY timestamp
       ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
    AS time_between_previous_match
FROM media_demo_data_postvalues
)
WHERE time_between_previous_match IS NOT NULL
GROUP BY page_name
ORDER BY average_minutes_since_registration
LIMIT 10;


&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
 Jacob SQL


•	Total Ad Impressions by Active/Non-Active Subscription:

SELET SUM(freewheel.[impression])   AS [Total_Impressions]
    , CASE
      WHEN sonic.[subscription_status] = ‘A’
      THEN CAST(1 as bit)
      ELSE CAST(0 as bit)
      END   AS [isActiveSubscription]
FROM sonic
INNER JOIN analytics aa
      ON sonic.[user_id] = aa.[sonic_id]
INNER JOIN freewheel
      ON freewheel.[mcmid] = aa.[mcid]

•	From Top-100, High-Impression Subscribers vs. Nonsubscribers, which advertisements have the highest total impression:


WITH cte_TopSubscribers AS (

SELECT TOP 100
  freewheel.[mcmid]
, SUM(freewheel.[impression]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IS NOT NULL
    AND sonic.[subscription_status] = ‘A’
ORDER BY [Total_Impressions] DESC

)
, cte_TopNonSubscribers AS (

SELECT TOP 100
  freewheel.[mcmid]
, SUM(freewheel.[impression]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IS NOT NULL
 AND sonic.[subscription_status] <> ‘A’
ORDER BY [Total_Impressions] DESC

)

SELECT  freewheel.[advertiser_name]
      , freewheel.[creative_name] AS [ad]
      , SUM(freewheel.[impressions]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IN (SELECT [mcmid] FROM cte_TopSubscribers UNION ALL SELECT [mcmid] FROM cte_TopNonSubscribers)







# solved

From our “Adults 25-54” segment, by brand, what is the average cost-per-ad seen by non-subscription users:

SELECT    AVG(freewheel.[cost_per]) AS [avg_ad_cost]
      , aa.[Brand]
FROM adobeanalytics aa
INNER JOIN audiencemanager am
      ON aa.[mcid] = am.[mcid] 
INNER JOIN freewheel
      ON aa.[mcid] = freewheel.[mcmid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE am.[Segement] = ‘Adults 25 to 54_Exelate_AAM116961’
  AND sonic.[subscription_status] <> ‘A’
  AND freewheel.[creative_id] IS NOT NULL


@@@@@@@@@@@@@@@@@ editted

From our “Adults 25-54” segment, by brand, what is the average cost-per-ad seen by non-subscription users:


sonic_dataset._adobeamericaspot2
freewheel_dataset._adobeamericaspot2
media_demo_data_postvalues

enduserids._experience.aaid.id



SELECT 
  b._adobeamericaspot2.subscription_status AS AccountStatus,
  SUM(a.web.webPageDetails.pageviews.value) AS PageViews
FROM media_demo_data_postvalues a 
     JOIN sonic_dataset b 
      ON a._experience.analytics.customdimensions.evars.evar9 = b._adobeamericaspot2.crmId
WHERE a._ACP_YEAR = 2019 
GROUP BY AccountStatus 
ORDER BY PageViews DESC
LIMIT 50;







SELECT    AVG(fd._adobeamericaspot2.cost_per) AS avg_ad_cost
      , aa.web.webPageDetails.siteSection AS WebSiteSection
FROM media_demo_data_postvalues aa
INNER JOIN freewheel_dataset fd
      ON aa._experience.analytics.customdimensions.evars.evar9 = fd._adobeamericaspot2.crmid
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.user_id
WHERE aa._experience.analytics.customDimensions.evars.evar33 = 'a'
  AND sd._adobeamericaspot2.subscription_status <> 'ACTIVE'
  AND fd._adobeamericaspot2.creative_id IS NOT NULL
LIMIT 10;



      aa.web.webPageDetails.siteSection AS WebSiteSection,





SELECT    SUM(fd._adobeamericaspot2.impression) AS avg_ad_cost,
      SUM(aa.web.webPageDetails.pageviews.value) AS PageViews,
      fd._adobeamericaspot2.crmid as crmid
FROM media_demo_data_postvalues aa
INNER JOIN freewheel_dataset fd
      ON aa._experience.analytics.customdimensions.evars.evar9 = fd._adobeamericaspot2.crmId
WHERE aa._ACP_YEAR = 2019 
GROUP BY crmid 
ORDER BY avg_ad_cost DESC
LIMIT 10;



^^^^ this works!




SELECT    SUM(fd._adobeamericaspot2.impression) AS avg_ad_cost,
      SUM(aa.web.webPageDetails.pageviews.value) AS PageViews,
      aa._experience.analytics.customdimensions.evars.evar10 as marketingChannel
FROM media_demo_data_postvalues aa
INNER JOIN freewheel_dataset fd
      ON aa._experience.analytics.customdimensions.evars.evar9 = fd._adobeamericaspot2.crmId
WHERE aa._ACP_YEAR = 2019 
GROUP BY marketingChannel 
ORDER BY avg_ad_cost DESC
LIMIT 10;


^^^^ this works!

web.webPageDetails.name



SELECT    SUM(fd._adobeamericaspot2.impression) AS avg_ad_cost,
      SUM(aa.web.webPageDetails.pageviews.value) AS PageViews,
      aa.web.webPageDetails.name as webPage
FROM media_demo_data_postvalues aa
INNER JOIN freewheel_dataset fd
      ON aa._experience.analytics.customdimensions.evars.evar9 = fd._adobeamericaspot2.crmId
WHERE aa._ACP_YEAR = 2019 
GROUP BY webPage 
ORDER BY avg_ad_cost DESC
LIMIT 10;


^^^^ this works!




SELECT    SUM(fd._adobeamericaspot2.impression) AS avg_ad_cost,
      SUM(aa.web.webPageDetails.pageviews.value) AS PageViews,
      aa.web.webPageDetails.siteSection as webSiteSection
FROM media_demo_data_postvalues aa
INNER JOIN freewheel_dataset fd
      ON aa._experience.analytics.customdimensions.evars.evar9 = fd._adobeamericaspot2.crmId
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE aa._ACP_YEAR = 2019 
  AND aa._experience.analytics.customDimensions.evars.evar33 = 'a'
  AND sd._adobeamericaspot2.subscription_status <> 'ACTIVE'
GROUP BY webSiteSection 
ORDER BY avg_ad_cost DESC
LIMIT 10;

^^^^ this works too!!! cool!

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$


•	From Top-100, High-Impression Subscribers vs. Nonsubscribers, which advertisements have the highest total impression:

;

WITH cte_TopSubscribers AS (

SELECT TOP 100
  freewheel.[mcmid]
, SUM(freewheel.[impression]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IS NOT NULL
    AND sonic.[subscription_status] = ‘A’
ORDER BY [Total_Impressions] DESC

)
, cte_TopNonSubscribers AS (

SELECT TOP 100
  freewheel.[mcmid]
, SUM(freewheel.[impression]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IS NOT NULL
 AND sonic.[subscription_status] <> ‘A’
ORDER BY [Total_Impressions] DESC

)

SELECT  freewheel.[advertiser_name]
      , freewheel.[creative_name] AS [ad]
      , SUM(freewheel.[impressions]) AS [Total_Impressions]
FROM freewheel
INNER JOIN adobeanalytics aa
      ON freewheel.[mcmid] = aa.[mcid]
INNER JOIN sonic
      ON aa.[sonic_id] = sonic.[user_id]
WHERE freewheel.[mcmid] IN (SELECT [mcmid] FROM cte_TopSubscribers UNION ALL SELECT [mcmid] FROM cte_TopNonSubscribers)



%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

•	From Top-100, High-Impression Subscribers vs. Nonsubscribers, which advertisements have the highest total impression:




WITH cte_TopSubscribers AS (

SELECT
  fd._adobeamericaspot2.crmId AS crmId
, SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IS NOT NULL
    AND sd._adobeamericaspot2.subscription_status = 'ACTIVE'
GROUP BY crmId
ORDER BY Total_Impressions DESC
LIMIT 100
)

, cte_TopNonSubscribers AS (

SELECT
  fd._adobeamericaspot2.crmId AS crmId
, SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IS NOT NULL
 AND sd._adobeamericaspot2.subscription_status <> 'ACTIVE'
GROUP BY crmId
ORDER BY Total_Impressions DESC
LIMIT 100
)

SELECT  fd._adobeamericaspot2.advertiser_name
      , fd._adobeamericaspot2.creative_name AS ad
      , SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IN (SELECT fd._adobeamericaspot2.crmId FROM cte_TopSubscribers UNION ALL SELECT fd._adobeamericaspot2.crmId FROM cte_TopNonSubscribers)
LIMIT 10;



GROUP BY fd._adobeamericaspot2.crmId;


hmmmmmmm



SELECT  fd._adobeamericaspot2.advertiser_name AS advertiserName
      , fd._adobeamericaspot2.creative_name AS ad
      , SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
GROUP BY advertiserName
ORDER BY Total_Impressions DESC
LIMIT 10;



_________________________________________________________________


SELECT
  fd._adobeamericaspot2.crmId AS crmID
, SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IS NOT NULL
    AND sd._adobeamericaspot2.subscription_status = 'ACTIVE'
GROUP BY crmID
ORDER BY Total_Impressions DESC;
LIMIT 100;

&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&


WITH cte_TopSubscribers AS (
SELECT
  fd._adobeamericaspot2.crmId AS crmId, 
  SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
...STUFF...
)
, cte_TopNonSubscribers AS (
SELECT
  fd._adobeamericaspot2.crmId AS crmId,
  SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
...STUFF...
)

SELECT  fd._adobeamericaspot2.advertiser_name
      , fd._adobeamericaspot2.creative_name AS ad
      , SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IN (SELECT fd._adobeamericaspot2.crmId FROM cte_TopSubscribers UNION ALL SELECT fd._adobeamericaspot2.crmId FROM cte_TopNonSubscribers)
LIMIT 10;


WITH TopSubscribers    AS (SELECT...),
     TopNonSubscribers AS (SELECT...)
     SELECT ( .... WHERE crmId IN 
           (SELECT crmId FROM TopSubscribers UNION ALL SELECT crmId FROM TopNonSubscribers))

*************************************************************************************************************************


WITH cte_TopSubscribers AS (

SELECT
  fd._adobeamericaspot2.crmId AS crmId
, SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IS NOT NULL
    AND sd._adobeamericaspot2.subscription_status = 'ACTIVE'
GROUP BY crmId
ORDER BY Total_Impressions DESC
LIMIT 100
)

, cte_TopNonSubscribers AS (

SELECT
  fd._adobeamericaspot2.crmId AS crmId
, SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IS NOT NULL
 AND sd._adobeamericaspot2.subscription_status <> 'ACTIVE'
GROUP BY crmId
ORDER BY Total_Impressions DESC
LIMIT 100;
)

SELECT  fd._adobeamericaspot2.advertiser_name
      , fd._adobeamericaspot2.creative_name AS ad
      , SUM(fd._adobeamericaspot2.impression) AS Total_Impressions
FROM freewheel_dataset fd
INNER JOIN media_demo_data_postvalues aa
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN sonic_dataset sd
      ON aa._experience.analytics.customdimensions.evars.evar9 = sd._adobeamericaspot2.crmId
WHERE fd._adobeamericaspot2.crmId IN (SELECT crmId FROM cte_TopSubscribers UNION ALL SELECT crmId FROM cte_TopNonSubscribers);

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>







SELECT SUM(fd._adobeamericaspot2.impression)   AS Total_Impressions
    , CASE
      WHEN sd._adobeamericaspot2.subscription_status = 'ACTIVE'
      THEN 1
      ELSE 0
      END  AS isActiveSubscription
FROM sonic_dataset sd
INNER JOIN media_demo_data_postvalues aa
      ON sd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN freewheel_dataset fd
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
GROUP BY isActiveSubscription
LIMIT 10;






SELECT SUM(fd._adobeamericaspot2.impression)   AS Total_Impressions
    , CASE
      WHEN sd._adobeamericaspot2.subscription_status = 'ACTIVE'
      THEN CAST(1 as bit)
      ELSE CAST(0 as bit)
      END   AS isActiveSubscription
FROM sonic_dataset sd
INNER JOIN media_demo_data_postvalues aa
      ON sd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
INNER JOIN freewheel_dataset fd
      ON fd._adobeamericaspot2.crmId = aa._experience.analytics.customdimensions.evars.evar9
LIMIT 10;



SELET SUM(freewheel.[impression])   AS [Total_Impressions]
    , CASE
      WHEN sonic.[subscription_status] = ‘A’
      THEN CAST(1 as bit)
      ELSE CAST(0 as bit)
      END   AS [isActiveSubscription]
FROM sonic
INNER JOIN analytics aa
      ON sonic.[user_id] = aa.[sonic_id]
INNER JOIN freewheel
      ON freewheel.[mcmid] = aa.[mcid]

      ==============

=================
for time
------------------------

SELECT 
    date_format( from_utc_timestamp( timestamp , 'PST') , 'yyyy-MM-dd') AS Day,
    SUM(web.webPageDetails.pageviews.value) AS pageViews
    FROM x2019_summit_platform_lab_2_postvalues_1
    GROUP BY Day
    ORDER BY Day ASC, pageViews DESC
    LIMIT 10;

---------------------------------------------------


try

SELECT
  CONCAT(endUserIDs._experience.aaid.id,_experience.analytics.session.num) AS visit_id,
  STRING TO ARRAY(explode(productListItems),",") AS Revenue
FROM
  media_demo_data_postvalues
WHERE
--Dates
  TIMESTAMP BETWEEN CAST('2019-06-04' AS TIMESTAMP) AND CAST('2019-06-05' AS TIMESTAMP) AND (_acp_year=2019 AND _acp_month = 06 AND _acp_day BETWEEN 04 AND 05)
  AND environment.domain != 'bestbuy.com'
  AND commerce.purchases.value IS NOT NULL

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


SELECT aa._experience.analytics.customdimensions.evars.evar9, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH(timestamp, 'trackingCode', marketing.trackingCode)
      OVER(PARTITION BY aa._experience.analytics.customdimensions.evars.evar9
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch

FROM media_demo_data_postvalues
ORDER BY enduserids._experience.aaid.id, timestamp ASC
LIMIT 10;


]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]


 	id	timestamp	trackingcode	sale_type	last_touch
1	1001BFBD88982890-7D64F1963B2905C7	10/27/2019, 3:58 PM	sms:10074-b	Invalid	(New Sale,Invalid,2019-10-22 21:08:19.0,1.0)
2	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:34 PM	da:10103-a	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
3	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:34 PM	da:10103-a	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
4	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:35 PM	da:10103-a	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
5	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:36 PM	da:10103-a	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
6	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:37 PM	prt:10108-c	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
7	1009C9FDD8546C7A-73720045CBDEDD53	11/6/2019, 4:39 PM	prt:10108-c	Invalid	(New Sale,Invalid,2019-10-29 07:07:05.0,1.0)
8	100B34E00934636B-16F9CB83256BEB1B	11/2/2019, 1:05 PM		Reinstate	(New Sale,Reinstate,2019-10-18 21:53:41.0,1.0)
9	100B34E00934636B-16F9CB83256BEB1B	11/2/2019, 1:06 PM		Reinstate	(New Sale,Reinstate,2019-10-18 21:53:41.0,1.0)
10	100B34E00934636B-16F9CB83256BEB1B	11/2/2019, 1:07 PM		Reinstate	(New Sale,Reinstate,2019-10-18 21:53:41.0,1.0)

-----------------------------------


SELECT t.*
  FROM (
        SELECT sales.timestamp,
               sales._adobeamericaspot2.price_currency,
               sales._adobeamericaspot2.price_amount,
               sales._adobeamericaspot2.subscription_id,
               ATTRIBUTION_LAST_TOUCH(aa.timestamp, 'CampaignId', marketing.trackingCode) OVER(PARTITION BY enduserids._experience.aaid.id
                                      ORDER BY aa.timestamp ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS last_touch,
               ROW_NUMBER() OVER(PARTITION BY sales._id ORDER BY sales.timestamp) row_num
          FROM sonic_dataset sales
         INNER JOIN media_demo_data_postvalues aa
                 ON aa._experience.analytics.customdimensions.evars.evar9 = sales._adobeamericaspot2.crmId
                  AND aa.timestamp <= sales.timestamp
          WHERE sales._adobeamericaspot2.sale_type = 'New Sale'
        ) t
    WHERE t.row_num = 1  
ORDER BY timestamp DESC
LIMIT 10;


https://www.adobe.io/apis/experienceplatform/home/services/query-service/query-service.html#!end-user/markdown/query-service/qs-clients-looker.md




SELECT t.*
  FROM (
                SELECT sales.timestamp,
                       sales._adobeamericaspot2.price_currency,
                       sales._adobeamericaspot2.price_amount,
                       sales._adobeamericaspot2.subscription_id,
                       ATTRIBUTION_LAST_TOUCH(aa.timestamp, 'SiteSection', web.webPageDetails.siteSection) OVER(PARTITION BY enduserids._experience.aaid.id
                                                                               ORDER BY aa.timestamp ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS last_touch,
                       ROW_NUMBER() OVER(PARTITION BY sales._id ORDER BY sales.timestamp) row_num
                  FROM sonic_dataset sales
                 INNER JOIN media_demo_data_postvalues aa
                         ON aa._experience.analytics.customdimensions.evars.evar9 = sales._adobeamericaspot2.crmId
                          AND aa.timestamp <= sales.timestamp
                  WHERE sales._adobeamericaspot2.subscription_status = 'TERMINATED'
        ) t
    WHERE t.row_num = 1  
ORDER BY timestamp DESC
   LIMIT 10;

++++++++++++++++++++++++++++++++++++++++++++++++++


select percentile_approx(cast(sales._adobeamericaspot2.price_amount as double), ARRAY(0.75))
from sonic_dataset sales


select percentile_approx(cast(sales._adobeamericaspot2.price_amount as double), ARRAY(0.1,0.2,0.3,0.4,0.5))
from sonic_dataset sales;


SELECT sales._adobeamericaspot2.crmId AS crmId,
       SUM(sales._adobeamericaspot2.price_amount) AS LifetimeValue
FROM sonic_dataset sales
WHERE SUM(sales._adobeamericaspot2.price_amount) > 8000
GROUP BY crmId
ORDER BY LifetimeValue
LIMIT 10;


SELECT sales._adobeamericaspot2.crmId AS crmId,
       SUM(sales._adobeamericaspot2.price_amount) AS LifetimeValue
FROM sonic_dataset sales
WHERE LifetimeValue > 16000
GROUP BY crmId
ORDER BY LifetimeValue DESC
LIMIT 10;






TTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTT


SELECT analyticsVisitor,
      session.is_new,
      session.timestamp_diff,
      session.num,
      session.depth
FROM (SELECT endUserIDs._experience.aaid.id as analyticsVisitor,
      SESS_TIMEOUT(timestamp, 60 * 30)
         OVER (PARTITION BY endUserIDs._experience.aaid.id
               ORDER BY timestamp
               ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
         AS session
 FROM media_demo_data_postvalues
 WHERE _ACP_YEAR = 2019
)
LIMIT 10;


pathing


SELECT 
  PageName,
  PageName_2,
  PageName_3,
  PageName_4,
  PageName_5,
  SUM(PageViews) as PageViews
FROM
(SELECT
  PageName,
  NEXT(PageName, 1, true)
    OVER(PARTITION BY VisitorID, session.num
          ORDER BY timestamp
          ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
    AS PageName_2,
  NEXT(PageName, 2, true)
    OVER(PARTITION BY VisitorID, session.num
          ORDER BY timestamp
          ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
    AS PageName_3,
  NEXT(PageName, 3, true)
     OVER(PARTITION BY VisitorID, session.num
          ORDER BY timestamp
          ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
    AS PageName_4,
  NEXT(PageName, 4, true)
     OVER(PARTITION BY VisitorID, session.num
          ORDER BY timestamp
          ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
    AS PageName_5,
  PageViews,
  session.depth AS SessionPageDepth
FROM
  (SELECT 
      endUserIds._experience.aaid.id as VisitorID,
     timestamp,
     web.webPageDetails.pageviews.value AS PageViews,
      web.webPageDetails.name AS PageName,
    SESS_TIMEOUT(timestamp, 60 * 30) 
      OVER (PARTITION BY endUserIDs._experience.aaid.id 
            ORDER BY timestamp 
            ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) 
    AS session
  FROM media_demo_data_postvalues
  WHERE _ACP_YEAR=2019)
)
WHERE SessionPageDepth=1
  AND PageName = 'home'
GROUP BY PageName, PageName_2, PageName_3, PageName_4, PageName_5
ORDER BY PageViews DESC
LIMIT 20;

============================


SELECT _experience.analytics.customdimensions.evars.evar9, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH(timestamp, 'trackingCode', marketing.trackingCode)
      OVER(PARTITION BY _experience.analytics.customdimensions.evars.evar9
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
WHERE _experience.analytics.customdimensions.evars.evar9 IS NOT NULL 
ORDER BY _experience.analytics.customdimensions.evars.evar9, timestamp ASC
LIMIT 10;



SELECT _experience.analytics.customdimensions.evars.evar9, timestamp, marketing.trackingCode,
    ATTRIBUTION_FIRST_TOUCH(timestamp, 'trackingCode', marketing.trackingCode)
      OVER(PARTITION BY _experience.analytics.customdimensions.evars.evar9
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
WHERE _experience.analytics.customdimensions.evars.evar9 IS NOT NULL 
ORDER BY _experience.analytics.customdimensions.evars.evar9, timestamp ASC
LIMIT 10;



SELECT endUserIds._experience.aaid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH_EXP_IF(timestamp, 'trackingCode', marketing.trackingCode, commerce.purchases.value IS NOT NULL, false)
      OVER(PARTITION BY endUserIds._experience.aaid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
ORDER BY endUserIds._experience.aaid.id, timestamp ASC
LIMIT 20;

################################################


SELECT endUserIds._experience.aaid.id, _experience.analytics.customdimensions.evars.evar9, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH_EXP_IF(timestamp, 'trackingCode', marketing.trackingCode, commerce.purchases.value IS NOT NULL, false)
      OVER(PARTITION BY endUserIds._experience.aaid.id
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
ORDER BY endUserIds._experience.aaid.id, timestamp ASC
LIMIT 100;



SELECT _experience.analytics.customdimensions.evars.evar9, endUserIds._experience.aaid.id, timestamp, marketing.trackingCode,
    ATTRIBUTION_LAST_TOUCH_EXP_IF(timestamp, 'trackingCode', marketing.trackingCode, commerce.purchases.value IS NOT NULL, false)
      OVER(PARTITION BY _experience.analytics.customdimensions.evars.evar9
           ORDER BY timestamp
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
      AS last_touch
FROM media_demo_data_postvalues
ORDER BY _experience.analytics.customdimensions.evars.evar9, timestamp ASC
LIMIT 100;
```
