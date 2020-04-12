## Exercise 3 - Define Custom Actions

In this exercise, you'll create 2 custom Actions by making use of Journey Orchestration in combination with Adobe Experience Platform

Go to [https://experience.adobe.com/#/@adobeamericaspot1/home](https://experience.adobe.com/#/@adobeamericaspot5/home)

You'll see the `Adobe Experience Cloud`-homepage.

![Demo](./images/aec.png)

Click on `Journey Orchestration`.

![Demo](./images/aecjo.png)

Next, you'll see the `Journey Orchestration`-homepage.

![Demo](./images/aecjoh.png)

In the menu, click on `Actions`.

![Demo](./images/menuactions.png)

You'll then see the `Actions`-list.

<!---
![Demo](./images/acthome.png)
--->

<kbd><img src="./images/acthome.png"  /></kdb>

You'll define 2 actions:

- 1 Action that sends an SMS using an external application, Nexmo
- 1 Action that sends a text to a Slack channel

### Action: Send SMS using Nexmo

Nexmo is a 3rd party provider of SMS Messages. It has an easy-to-use API and we'll use Journey Orchestration to trigger their API.

Click `Add` to start adding your action.

![Demo](./images/add.png)

You'll see an empty Action popup.

<!---
![Demo](./images/emptyact.png)
--->

<kbd><img src="./images/emptyact.png"  /></kdb>

As a Name for the Action, use **smsNexmo{emailAddress}** and replace **{emailAddress}** with your your email name. E.g. **smsNexmoPuchadha**.

Add the Description: **Send SMS using Nexmo**.

<!---
![Demo](./images/nexmoname.png)
--->

<kbd><img src="./images/nexmoname.png"  /></kdb>

For the `URL Configuration`, copy and paste this URL:

- URL: `https://rest.nexmo.com/sms/json`
- Method: `POST`

Do not change the Header Fields.

<!---
![Demo](./images/nexmourl.png)
--->

<kbd><img src="./images/nexmourl.png"  /></kdb>

(For transparency, we're using an AWS API Gateway and AWS Lambda function that sits behind the above URL to handle the authentication and sending of SMSs to Nexmo.)

`Authentication` should be set to `No Authentication`.

<!---
![Demo](./images/nexmoauth.png)
--->

<kbd><img src="./images/nexmoauth.png"  /></kdb>

For the `Message Parameters`, you need to define which fields should be sent towards Nexmo. Logically, we want Journey Orchestration and Adobe Experience Platform to be the brain of personalization, so the SMS Message Text and the Mobile Number to send the SMS towards should be defined by Journey Orchestration and then sent to Nexmo for execution.

So for the `Message Parameters`, click the `Edit Payload`-icon.

<!---
![Demo](./images/nexmomsgp.png)
--->

<kbd><img src="./images/nexmomsgp.png"  /></kdb>

You'll then see an empty popup-window.

![Demo](./images/nexmomsgpopup.png)

Copy and paste the JSON below into the popup-window.

```json
{
  "to": {
    "toBeMapped": true,
    "dataType": "string",
    "label": "Mobile Number"
  },
  "text": {
    "toBeMapped": true,
    "dataType": "string",
    "label": "Message"
  },
  "api_key": "api_key",
  "api_secret": "api_secret",
  "from": "14155041161"
}
```

The api_key and api_secret values will be provided seperately

![Demo](./images/nexmomsgpopup1.png)

Click `Save`.

![Demo](./images/nexmomsgpopup2.png)

Scroll up and click `Save` one more time to save your custom Action.

<!---
![Demo](./images/nexmomsgpopup3.png)
--->

<kbd><img src="./images/nexmomsgpopup3.png"  /></kdb>

Your custom Action is now part of the `Actions`-list.

![Demo](./images/nexmodone.png)

Let's define your second action now.

You've now defined Events, Data Sources and Actions - let's consolidate all of that in 1 Orchestrated Journey.

---

Next Step: [Exercise 4 - Design a trigger-based Customer Journey](./Exercise4-Journey.md)
