Lab Attendee Download Packages
====================================

| User     | ZIP  | GZ  |
|------------|---|---|
| All Attendees -- Please download this package (ZIP or GZ format) | [ZIP](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/fsi/assets/all_attendees_fsi.zip)  |  [GZ](https://github.com/adobe/AEP-Hands-on-Labs/raw/master/labs/fsi/assets/all_attendees_fsi.tar.gz)  |



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


Preview: Transactions data JSON
-----------------------------

```json
{ 
    "_id":"a11c7f74-4c74-11ea-9249-b88a60e194fb-1",
    "timestamp":"2020-01-25T16:17:48.000Z",
    "eventType":"transaction",
    "_adobeamericaspot1":{ 
        "CRMID":"crmid:7638102025",
        "orderDetails":{ 
            "currencyType":"USD",
            "orderID":"a11c7f74-4c74-11ea-9249-b88a60e194fb",
            "productCategory":"Retirement",
            "productName":"401k",
            "productSKU":"prd1175",
            "purchaseAmount":"121659.53"
        },
        "transactionDetails":{ 
            "branchID":"branchid:11134",
            "transactionID":"a11c7f74-4c74-11ea-9249-b88a60e194fb"
        }
    }
}
```


Preview: Transactions data
-----------------------------

| Number     | Header  | Example Data  |
|------------|---|---|
| 1  | id  |  82eb8fe8-492b-11ea-aea9-b88a60e194fb-1 |
| 2  | timestamp  |  2020-01-31T21:42:10.000Z  |
| 3  | crmid  |  crmid:6799807695 |
| 4  | orderid  |  82eb8fe8-492b-11ea-aea9-b88a60e194fb  |
| 5  | prod_sku  |  prd1155  |
| 6  | prod_name  |  CDs: 5 year  |
| 7  | prod_category  |  Investment  |
| 8  | prod_ownership |  Personal  |
| 9  | purchase_amt  |  224295.53  |
| 10  | units  | 1 |
| 11  | currency_type  |  USD |
| 12  | branchid  |  branchid:11054  |


Preview: Propensity data
-----------------------------

| Number     | Header  | Example Data  |  Notes |
|------------|---|---|---|
| 1  | id  |  82e99428-492b-11ea-b88f-b88a60e194fb-1-ps | unique row |
| 2  | crmid  |  crmid:8019712410  | unique account ID |
| 3  | propensity score credit cards  |  3 | 0-10 (10 is highest) |
| 4  | suggested credit card  |  Dividend Card | next best offer |
| 5  | propensity score_loan |  4 | 0-10 (10 is highest) |
| 6  | suggested loan |  Auto Loan  | next best offer |


Unlinked Profiles
----------------------------

Here's the list of [Unlinked Profiles](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi6/unlinked_fsi.md) used in the API exercises.
