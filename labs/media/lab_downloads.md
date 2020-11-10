Lab Attendee Download Packages
====================================

| User     | ZIP  | GZ  |
|------------|---|---|
| All Attendees -- Please download this package (ZIP or GZ format) | [ZIP](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/media/assets/001_media.zip)  |  [GZ](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/media/assets/001_media.tar.gz)  |


File Notes
----------------------------
 - lab files will be refreshed on a monthly basis




Preview: CRM data
-----------------------------

| Number     | Header  | Example Data  |
|------------|---|---|
| 1  | crmid  |  crmid:3572904408  |
| 2  | email  |  leese1838@yahoo.com  |
| 3  | first_name  |  Roscoe |
| 4  | last_name  |  Lawrence  |
| 5  | gender  |  female  |
| 6  | mobile telephone  |  531-075-8094  |
| 7  | city  |  Wauwatosa  |
| 8  | country  |  United States  |
| 9  | zip  |  88430  |
| 10  | state  |  Hawaii  |
| 11  | street address  |  744 Fratessa  |
| 12  | birthday  |  8/17/1972  |
| 13  | historicalpoints  |  504  |

Preview: Order data JSON
-----------------------------

```json
{
  "_id": "3f91922c-78f6-11ea-ba64-b88a60e194fb",
  "timestamp": "2020-03-13 00:25:20",
  "eventType": "transaction",
  "_adobeamericaspot5": {
    "transactionFlag": "1",
    "CRMID": "crmid:1603337965",
    "productDetails": [
      {
        "productSKUCount": "1",
        "productUnitsCount": "2",
        "productSKU": "prd1111",
        "productName": "Graduate Tailored Leg Das Denim Pant",
        "productCategory": "Men",
        "productSubCategory": "Men: Clothing",
        "productSalePrice": "284.5",
        "productMarginPrice": "156.48",
        "productTotalPrice": "569.0",
        "productFlag": 1
      },
      {
        "productSKUCount": "2",
        "productUnitsCount": "4",
        "productSKU": "prd1122",
        "productName": "High-Waist Boot Cut Pant",
        "productCategory": "Women",
        "productSubCategory": "Women: Clothing",
        "productSalePrice": "438.95",
        "productMarginPrice": "280.93",
        "productTotalPrice": "1755.8",
        "productFlag": 1
      }
    ],
    "orderDetails": {
      "orderID": "orderid:247282",
      "orderSKUcount": "2",
      "orderFlag": 1,
    },
    "storeDetails": {
      "storeID": "store:352",
      "storeClerkID": "clerkid:35244",
      "storeZIP": "06880"
    }
  }
}
```


Preview: Bookings data
-----------------------------

| Number     | Header  | Example Data  |
|------------|---|---|
| 1 | id	| 0123f54c-53c9-11ea-bb46-b88a60e194fb |
| 2 | reservationid	| W4A-XR20 |
| 3 | orderid	| orderid:323451 |
| 4 | crmid	| crmid:7386299961 |
| 5 | timestamp	| 2019-12-13T02:26:57.000Z |
| 6 | orderType	| website |
| 7 | productsku	| prd1134 |
| 8 | hotelCheckInUnix	| 1576290417 |
| 9 | hotelCheckOutUnix	| 1576376817 |
| 10 | hotelCheckInTS	| 2019-12-14T02:26:57+00:00 |
| 11 | hotelCheckOutTS	| 2019-12-15T02:26:57+00:00 |
| 12 | hotelName	| Restful Nights: Montreal |
| 13 | hotelChain	| Restful Nights |
| 14 | hotelLocation	| Montreal |
| 15 | hotelRoomType	| standard |
| 16 | hotelRoomCount	| 1 |
| 17 | hotelGuestAdultCount	| 1 |
| 18 | hotelGuestChildCount	| 0 |
| 19 | hotelNightCount	| 1 |
| 20 | hotelRoomPrice	| 171.35 |
| 21 | hotelFinalPrice	| 171.35 |


Preview: Propensity data
-----------------------------

| Number     | Header  | Example Data  |  Notes |
|------------|---|---|---|
| 1  | id  |  01706742-53c9-11ea-a979-b88a60e194fb | unique row |
| 2  | crmid  |  crmid:8019712410  | unique account ID |
| 3  | propensity score room upgrade  |  3 | 0-10 (10 is highest) |
| 4  | propensity score extended nights |  4 | 0-10 (10 is highest) |



Unlinked Profiles
----------------------------

Here's the list of [Unlinked Profiles](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/media/unlinked.md)
