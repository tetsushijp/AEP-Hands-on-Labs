Lab Attendee Download Packages
====================================


| User     | ZIP  | GZ  |
|------------|---|---|
| All Attendees -- Please download this package (ZIP or GZ format) | [ZIP](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/travel/assets/all_attendees_travel.zip)  |  [GZ](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/travel/assets/all_attendees_travel.tar.gz)  |



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

Preview: Booking data JSON
-----------------------------

```json
{
  "_id": "a9825fb6-53cb-11ea-8004-b88a60e194fb",
  "timestamp": "2019-12-04T04:58:48.000Z",
  "eventType": "transaction",
  "_adobeamericaspot3": {
    "CRMID": "crmid:9805866820",
    "bookingDetails": {
      "hotelSKU": "prd1025",
      "hotelCheckInUnix": "1577681928",
      "hotelCheckOutUnix": "1578027528",
      "hotelCheckInTS": "2019-12-30T04:58:48+00:00",
      "hotelCheckOutTS": "2020-01-03T04:58:48+00:00",
      "hotelChain": "Grandeur Hotels",
      "hotelName": "Grandeur Hotels: Detroit",
      "hotelLocation": "Detroit",
      "hotelRoomType": "standard",
      "hotelRoomCount": "1",
      "hotelGuestAdultCount": "1",
      "hotelGuestChildCount": "0",
      "hotelNightCount": "4",
      "hotelRoomPrice": "135.52",
      "hotelFinalPrice": "542.08"
    },
    "orderDetails": {
      "orderID": "orderid:467812",
      "reservationid": "FEA-OL9U",
      "orderType": "service desk"
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

Here's the list of [Unlinked Profiles](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/unlinked_travel.md)
