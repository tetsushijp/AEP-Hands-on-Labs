
THIS SECTION IS NOT YET DONE -- but this gives you a picture of the data dictionary page for the marketer....
 
Welcome Marketer / DBarchitect / Soon-To-Be AEP Genius...
-----------------------------
You are wearing many hats at a leading Media Company, likely not too dissimalar to your day-to-day responsibilites today.  You've been tasked to both deploy and understand how to build out the upon your AEP deployment.  This guide/document here (meant to be reviewed before your HOL session) will give you a detailed look and analysis of the data you're currently loading into your system.

OBJECTIVES:
==============
  - Become familiar with the data sources
  - Understand mixins + schemas
  - New insights into your deployment
  
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


CRM Data - version 003 - junky old version -- table overflowing is annoying
-----------------------------



| Number | FieldName         | DataType              | Mixin + Path                          | Example             | Definition (when nessacary)          |
|--------|-------------------|-----------------------|---------------------------------------|---------------------|--------------------------------------|
| 01     | crmid             |  string               | {{tenantid}}.identification.CRMID     | crmid:3572904408    |  -                                   |
| 02     | email             |  string               | {{tenantid}}.identification.Email     | leese1838@yahoo.com |  -                                   |
| 03     | first_name        |  string               | person.name.firstName                 | Roscoe              |  -                                   |
| 04     | last_name         |  string               | person.name.lastName                  | Lawrence            |  -                                   |
| 05     | gender            |  enum (string)        | person.gender                         | female              |  -                                   |
| 06     | mobile_telephone  |  string               | mobilePhone.number                    | 531-075-8094        |  -                                   |
| 07     | city              |  string               | homeAddress.city                      | Wauwatosa           |  -                                   |
| 08     | country           |  string               | homeAddress.country                   | United States       |  -                                   |
| 09     | zip               |  string               | homeAddress.postalCode                | 88430               |  -                                   |
| 10     | state             |  string               | homeAddress.stateProvince             | Hawaii              |  -                                   |
| 11     | street_address    |  string               | homeAddress.street1                   | 744 Fratessa        |  -                                   |
| 12     | birthday          |  string (date)        | person.birthDate                      | 8/17/1972           |  -                                   |
| 13     | genre             |  string               | interestProfileDetails.interestGenre  | Sci-Fi              |  what TV genre the customer likes    |





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


Doug Notes:
 - The above examples would be for each data source (not shown yet, its being drafted right now)
 - I'd add the "id" , "eventtype" and "timestamp" as built-ins to the schema
 - I'm gonna add schema and mixin screenshots to show how things are composed
 - I'm going to explain the Mixin + Path with a screenshot (so it helps show what that means)
 - I'm going to add the real mixin, schema and dataset names and IDs -- helpful for query service
 
 **Pulkit -- please let me know what else you think would be rad here!**
