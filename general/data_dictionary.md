
THIS SECTION IS NOT YET DONE -- but this gives you a picture of the data dictionary page for the marketer....
 
Welcome Marketer / DBarchitect / Soon-To-Be AEP Genius...
-----------------------------
You are wearing many hats at a leading Media Company, likely not too dissimalar to your day-to-day responsibilites in the real world.  You've been tasked to both deploy and understand how to build out the upon your AEP deployment -- the deployment has already started so the system should be considered ".  This guide/document here (meant to be reviewed before your HOL session) will give you a detailed look and analysis of the data you're currently loading into your system.

OBJECTIVES:
==============
  - Become familiar with the data sources
  - Understand mixins + schemas
  - Gain new insights into your HOL deployment with AEP
  
SOURCES:
=================
The data below is what has already been loaded in your system.  Please (blah blah blah blah)...



CRM Data - version 001 - removed define column (I sort of like this)
-----------------------------

 - please note the supperscripts for clicks to links, I'm digging that
 
 

| Number | FieldName         | DataType<sup>[info](#here)</sup>  | Mixin + Path <sup>[info](#here)</sup> | Example | 
|--------|-------------------|-----------------------|---------------------------------------|---------------------|
| 01     | crmid             |  string               | {{tenantid}}.identification.CRMID     | crmid:3572904408    |
| 02     | email             |  string               | {{tenantid}}.identification.Email     | leese1838@yahoo.com |
| 03     | first_name        |  string               | person.name.firstName                 | Roscoe              |
| 04     | last_name         |  string               | person.name.lastName                  | Lawrence            |
| 05     | gender            |  enum (string)        | person.gender                         | female              |
| 06     | mobile_telephone  |  string               | mobilePhone.number                    | 531-075-8094        |
| 07     | city              |  string               | homeAddress.city                      | Wauwatosa           |
| 08     | country           |  string               | homeAddress.country                   | United States       |
| 09     | zip               |  string               | homeAddress.postalCode                | 88430               |
| 10     | state             |  string               | homeAddress.stateProvince             | Hawaii              |
| 11     | street_address    |  string               | homeAddress.street1                   | 744 Fratessa        |
| 12     | birthday          |  string (date)        | person.birthDate                      | 8/17/1972           |
| 13     | genre<sup>1</sup> |  string               | interestProfileDetails.interestGenre  | Sci-Fi              |




CRM Data - version 002 - added Notes column (small links would go here to "more info about X")
-----------------------------



| Number | FieldName         | DataType<sup>[info](#here)</sup>  | Mixin + Path <sup>[info](#here)</sup> | Example | Notes |
|--------|-------------------|-----------------------|---------------------------------------|---------------------|-----|
| 01     | crmid             |  string               | {{tenantid}}.identification.CRMID     | crmid:3572904408    |  -  |
| 02     | email             |  string               | {{tenantid}}.identification.Email     | leese1838@yahoo.com |  -  |
| 03     | first_name        |  string               | person.name.firstName                 | Roscoe              |  -  |
| 04     | last_name         |  string               | person.name.lastName                  | Lawrence            |  -  |
| 05     | gender            |  enum (string)        | person.gender                         | female              |  -  |
| 06     | mobile_telephone  |  string               | mobilePhone.number                    | 531-075-8094        |  -  |
| 07     | city              |  string               | homeAddress.city                      | Wauwatosa           |  -  |
| 08     | country           |  string               | homeAddress.country                   | United States       |  -  |
| 09     | zip               |  string               | homeAddress.postalCode                | 88430               |  -  |
| 10     | state             |  string               | homeAddress.stateProvince             | Hawaii              |  -  |
| 11     | street_address    |  string               | homeAddress.street1                   | 744 Fratessa        |  -  |
| 12     | birthday          |  string (date)        | person.birthDate                      | 8/17/1972           |  -  |
| 13     | genre<sup>1</sup> |  string               | interestProfileDetails.interestGenre  | Sci-Fi              | [1](https://google.com)|


CRM Data - version 001 - this would be the "extra notes" area -- help explaining stuff (when needed)
-----------------------------


<table>
<tr>
<th>Argument</th>
<th>Description</th>
</tr>
<tr>
<td>appDir</td>
<td>The top level directory that contains your app. If this option is used then
it assumed your scripts are in</td>
</tr>
<tr>
<td>baseUrl</td>
<td>By default, all modules are located relative to this path. If baseUrl is not
explicitly set, then all modules are loaded relative to the directory that holds
the build file. If appDir is set, then baseUrl should be specified as relative
to the appDir.</td>
</tr>
<tr>
<td>dir</td>
<td>The directory path to save the output. If not specified, then the path will
default to be a directory called "build" as a sibling to the build file. All
relative paths are relative to the build file.</td>
</tr>
<tr>
<td>modules</td>
<td>List the modules that will be optimized. All their immediate and deep
dependencies will be included in the module's file when the build is done. If
that module or any of its dependencies includes i18n bundles, only the root
bundles will be included unless the locale: section is set above.</td>
</tr>
</table>




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



Subscription Data
-----------------------------------

#### Info

This has some data aBOUT X Y Z

#### Table

#### JSON Preview

```json
{
  "_id": "c263737f-84d8-11ea-8271-b88a60e194fb",
  "timestamp": "2020-03-17T06:11:13.000Z",
  "eventType": "subscription - website",
  "_adobeamericaspot2": {
    "identification": {
      "CRMID": "crmid:9999463"
    },
    "subscriptionDetails": {
      "subscriptionID": "subscriptionid:852331",
      "subscriptionSKU": "prd1004",
      "subscriptionName": "Live Streaming Plan: Month-to-Month",
      "subscriptionType": "Live Streaming Plan",
      "subscriptionLength": "Month-to-Month",
      "subscriptionPayment": "Mastercard",
      "subscriptionMethod": "website",
      "subscriptionAmount": 277.8,
      "subscriptionFlag": 1
    },
    "accountDetails": {
      "accountCurrentContractMonth": "7",
      "accountOriginChannel": "website",
      "accountStatus": "renewed"
    }
  }
}
```



#### CSV Preview

```
id,eventtype,subscriptionid,crmid,timestamp,accountstatus,subscriptionsku,subscriptionname,subscriptiontype,subscriptionlength,subscriptionpayment,subscriptionmethod,subscriptionamount,subscriptionflag,accountcurrentcontractmonth,accountoriginchannel
c2632694-84d8-11ea-9d0a-b88a60e194fb,subscription - website,subscriptionid:587524,crmid:9999463,2020-03-28T00:15:33.000Z,renewed,prd1118,Basic Plan: Annual,Basic Plan,Annual,Visa,website,452.25,1,16,website
c263737f-84d8-11ea-8271-b88a60e194fb,subscription - website,subscriptionid:852331,crmid:9999463,2020-03-17T06:11:13.000Z,renewed,prd1004,Live Streaming Plan: Month-to-Month,Live Streaming Plan,Month-to-Month,Mastercard,website,277.8,1,7,website
...
```


CRM Data
-----------------------------------

#### Info

This has some data aBOUT X Y Z

#### Table

here

#### JSON Preview

```json
{
  "_id": "d369d2b4-84d8-11ea-ac05-b88a60e194fb",
  "_adobeamericaspot2": {
    "identification": {
      "CRMID": "crmid:9994161",
      "Email": "macrobiotus1938@gmail.aephandson.com"
    },
    "interestProfileDetails": {
      "interestGenre": "Action"
    }
  },
  "personalEmail": {
    "address": "macrobiotus1938@gmail.aephandson.com"
  },
  "person": {
    "name": {
      "firstName": "Shenika",
      "lastName": "Caldwell"
    },
    "gender": "female",
    "birthDate": "1955-12-15"
  },
  "mobilePhone": {
    "number": "725-328-9492"
  },
  "homeAddress": {
    "city": "Dolton",
    "country": "United States",
    "postalCode": "71523",
    "stateProvince": "Missouri",
    "street1": "866 Taraval"
  }
}


```

#### CSV Preview

```
crmid,email,first_name,last_name,gender,mobile_telephone,city,country,zip,state,street_address,birthday,genre
crmid:9999463,deceive1927@outlook.aephandson.com,Porfirio,Morris,male,248-153-0606,Burton,United States,45224,Kansas,891 Essex,1943-08-21,Fantasy
crmid:9999425,barite2000@yandex.aephandson.com,Leo,Dejesus,,847-223-9855,Melbourne,United States,74642,Iowa,803 Kamille,1989-12-15,Comedy
...
```


Reduced Web Data
-----------------------------------

#### Info

This has some data aBOUT X Y Z

#### Table

  here

#### JSON Preview--

```json

{
  "_id": "485ee26b-84d9-11ea-b95a-b88a60e194fb",
  "timestamp": "2020-03-30T07:29:59.000Z",
  "eventType": "web - pageview",
  "_adobeamericaspot2": {
    "identification": {
      "CRMID": "",
      "Cookie": "497A76D0301EB581-44F48C9F3F294CF4",
      "CRMIDCombo": "crmid:[497A76D0301EB581]"
    },
    "webProductDetails": [
      {
        "webProductSKU": "prd1188",
        "webProductName": "Premium Plan: Month-to-Month",
        "webProductType": "Premium Plan",
        "webProductLength": "Month-to-Month",
        "webProductFlag": 1
      }
    ],
    "webDetails": {
      "webFlag": 1,
      "webHitID": "2F40CFFB85158000-401286A4671D62F9",
      "webPagename": "purchase: step 2",
      "webUserPersona": "persona3",
      "webUserTier": "persona3"
    }
  },
  "placeContext": {
    "geo": {
      "postalCode": "35410",
      "_schema": {
        "latitude": "38.32",
        "longitude": "27.13"
      }
    }
  }
}


```



Propensity Data
-----------------------------------

#### Info

This has some data aBOUT X Y Z

#### Table
  
 Hi there ppl

#### JSON Preview

```json
{
  "_id": "c2640fb6-84d8-11ea-8a50-b88a60e194fb",
  "timestamp": "2020-03-31T06:19:47.000Z",
  "_adobeamericaspot2": {
    "identification": {
      "CRMID": "crmid:9991105"
    },
    "propensityProfileDetails": {
      "propensityPremium": 7,
      "propensityHighSpeed": 5
    }
  }
}
```


#### CSV Preview

```
id,crmid,propensity_premium,propensity_high_speed
c263737e-84d8-11ea-b522-b88a60e194fb,crmid:9999463,2,7
c2639a8c-84d8-11ea-ac72-b88a60e194fb,crmid:9999463,7,4
...
```




Call Center Data
-----------------------------------

#### Info
This has some data aBOUT X Y Z

#### Table

#### JSON Preview

```json
{
  "_id": "bff3bc24-84d8-11ea-8079-b88a60e194fb",
  "timestamp": "2020-03-23T13:12:02.000Z",
  "eventType": "call - Payment Question",
  "_adobeamericaspot2": {
    "identification": {
      "CRMID": "crmid:8127612"
    },
    "callCenterDetails": {
      "callAgentID": "agentid:451",
      "callCenterName": "callcenter:4",
      "callEndtime": "2020-03-23T13:05:31.000Z",
      "callFlag": 1,
      "callID": "372889423",
      "callLength": 42,
      "callSelectedReason": "Payment Question",
      "callStarttime": "2020-03-23T13:12:02.000Z",
      "callSurveyScore": "9"
    }
  }
}
```


#### CSV Preview


```
id,eventtype,callstarttime,crmid,callid,callcentername,callagentid,callselectedreason,calllength,callendtime,callsurveyscore,callflag
bff31e58-84d8-11ea-86ac-b88a60e194fb,call - Subscription Open,2020-03-16T16:05:21.000Z,crmid:1199216,743688988,callcenter:4,agentid:447,Subscription Open,489,2020-03-16T16:05:36.000Z,,1
bff394b0-84d8-11ea-8d79-b88a60e194fb,call - Website Issue,2020-03-26T19:46:04.000Z,crmid:8420927,893399706,callcenter:6,agentid:617,Website Issue,568,2020-03-26T19:51:17.000Z,,1
bff3bc24-84d8-11ea-8079-b88a60e194fb,call - Payment Question,2020-03-23T13:12:02.000Z,crmid:8127612,372889423,callcenter:4,agentid:451,Payment Question,-42,2020-03-23T13:05:31.000Z,9,1
...
```

XDM - Data Type Definitions
------------------------------


| XDM type  | Range                                                     | JSON Schema type | JSON Schema format |
| --------- | --------------------------------------------------------- | ---------------- | ------------------ |
| string    | unlimited                                                 | string           |                    |
| number    | ±2.23×10^308 to ±1.80×10^308 (IEEE 64-bit floating point) | number           |                    |
| long      | (-2^53 + 1) - (2^53 - 1) (54-bit signed integer\*)        | integer          |                    |
| int       | -2^31 - 2^31 (32-bit signed integer)                      | integer          |                    |
| short     | -2^15 - 2^15 (16-bit signed integer)                      | integer          |                    |
| byte      | -2^7 - 2^7 (8-bit signed integer)                         | integer          |                    |
| boolean   | { true, false }                                           | boolean          |                    |
| date      | n/a                                                       | string           | date\*\*           |
| date-time | n/a                                                       | string           | date-time\*\*      |
| map       | n/a                                                       | object           |                    |



For more info, please look (here)[https://github.com/adobe/xdm/blob/master/docs/data_types.md]

Doug Notes:
 - The above examples would be for each data source (not shown yet, its being drafted right now)
 - I'd add the "id" , "eventtype" and "timestamp" as built-ins to the schema
 - I'm gonna add schema and mixin screenshots to show how things are composed
 - I'm going to explain the Mixin + Path with a screenshot (so it helps show what that means)
 - I'm going to add the real mixin, schema and dataset names and IDs -- helpful for query service
 
 **Pulkit -- please let me know what else you think would be rad here!**
