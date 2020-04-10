CRM Data
-----------------------------

| Number | FieldName  | DataType  | Mixin            | Example          | Definition                           |
|--------|------------|-----------|------------------|------------------|--------------------------------------|
| 1      | crmid      | string    | identification   | crmid:3572904408 | account ID for the user              |
| 2      | email  |  leese1838@yahoo.com  |
| 3      | first_name  |  Roscoe |
| 4      | last_name  |  Lawrence  |
| 5      | gender  |  female  |
| 6      | mobile telephone  |  531-075-8094  |
| 7      | city  |  Wauwatosa  |
| 8      | country  |  United States  |
| 9      | zip  |  88430  |
| 10     | state  |  Hawaii  |
| 11     | street address  |  744 Fratessa  |
| 12     | birthday  |  8/17/1972  |
| 13     | historicalpoints  |  504  |



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
