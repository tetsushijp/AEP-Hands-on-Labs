## Exercise 4 - Design a trigger-based Customer Journey

In this exercise, you'll create an Orchestrated Journey by making use of Journey Orchestration in combination with Adobe Experience Platform

Go to [https://experience.adobe.com/#/@adobeamericaspot5/home](https://experience.adobe.com/#/@adobeamericaspot5/home)

You'll see the `Adobe Experience Cloud`-homepage.

![Demo](./images/aec.png)

Click on `Journey Orchestration`.

![Demo](./images/aecjo.png)

Next, you'll see the `Journey Orchestration`-homepage, which shows all existing Journeys.

![Demo](./images/aecjoh.png)

Click `Create` to start creating your Journey.

![Demo](./images/jocreate.png)

You'll then see a new, blank Journey.

<!---
![Demo](./images/jonew.png)
--->

<kbd><img src="./images/jonew.png"  /></kdb>

You should first name your Journey.

As a Name for the Journey, use **Website Registration Journey emailAddress** and replace **emailAddress** with LDAP. In this example, the Journey Name is **Website Registration Journey puchadha**. No other values must be set at this moment.

<!---
![Demo](./images/joname.png)
--->

<kbd><img src="./images/joname.png"  /></kdb>

Click `OK`.

![Demo](./images/jonameok.png)

On the left side of your screen, have a look at `Events`. You should see your previously create Event on that list. Select it, then drag and drop it on the Journey Canvas.

![Demo](./images/joevents.png)

Your Journey then looks like this:

![Demo](./images/jo1.png)

Next, click on `Orchestration`.

![Demo](./images/jo2.png)

You now see `Orchestration`-capabilities.

![Demo](./images/jo3.png)

Select `Condition`, then drag and drop it on the Journey Canvas.

<!---
![Demo](./images/jo4.png)
--->

<kbd><img src="./images/jo4.png"  /></kdb>

You now have to define 2 conditions:

- It's Raining
- It's Clear

Let's define the first condition.

#### Condition 1: It's Raining

Click on the `Condition`.

<!---
![Demo](./images/jo5.png)
--->

<kbd><img src="./images/jo5.png"  /></kdb>

Click on the `Edit`-icon for the expression of Path1.

<!---
![Demo](./images/jo6.png)
--->

<kbd><img src="./images/jo6.png"  /></kdb>

You'll then see an empty `Simple Editor`-screen.

![Demo](./images/jo7.png)

Our query will be a bit more advanced, so we'll need the `Advanced Mode`.
Click `Advanced Mode`.

![Demo](./images/jo8.png)

You'll then see the `Advanced Editor` which allows code entry. Paste it in `##{weatherApiemailAddress.WeatherByZipemailAddress.weather.main} == 'Rain'` (replace emailAddress)

You'll then see this.

![Demo](./images/jo10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the zipCode in which the customer currently is.
The `zipCode` needs to be linked to the dynamic parameter `zip`.

Click the field `dynamic val: zip` as indicated in the screenshot.

<!---
![Demo](./images/jo11.png)
--->

<kbd><img src="./images/jo11.png"  /></kdb>

You then need to find the field that contains the current zip code of the customer in the AEP Data Sources. Here we are leveraging the unified profile data in AEP to get the profiles zip code.

You can navigate the field structure from the panel or simply paste the expression below into the expression text box.
`#{ExperiencePlatform.ProfileFieldGroup.profile.homeAddress.postalCode}`

![Demo](./images/jo12.png)

Click `OK`.

![Demo](./images/jook.png)

Rename the path from path1 to 'Raining'

<!---
![Demo](./images/jopath1name.png)
--->

<kbd><img src="./images/jopath1name.png"  /></kdb>

Next, we'll add the 2nd condition.

#### Condition 2: Its Clear

After having added the first condition, you'll see this screen.

<!---
![Demo](./images/joc2.png)
--->

<kbd><img src="./images/joc2.png"  /></kdb>

Click `Add Path`.

![Demo](./images/joadd.png)

Click on the `Edit`-icon for the expression of Path1.

<!---
![Demo](./images/jo6.png)
--->

<kbd><img src="./images/jo6.png"  /></kdb>

You'll then see an empty `Simple Editor`-screen.

![Demo](./images/jo7.png)

Our query will be a bit more advanced, so we'll need the `Advanced Mode`.
Click `Advanced Mode`.

![Demo](./images/jo8.png)

You'll then see the `Advanced Editor` which allows code entry. Paste it in `#{weatherApiemailAddress.WeatherByZipemailAddress.weather.main} == 'Clear'` (replace emailAddress)

You'll then see this.

![Demo](./images/jo14.png)

To retrieve the temperature as part of this Condition, you need to provide the zipCode in which the customer currently is.
The `zipCode` needs to be linked to the dynamic parameter `zip`.

Click the field `dynamic val: zip` as indicated in the screenshot.

<!---
![Demo](./images/jo11.png)
--->

<kbd><img src="./images/jo11.png"  /></kdb>

You then need to find the field that contains the current zip code of the customer in the AEP Data Sources. Here we are leveraging the unified profile data in AEP to get the profiles zip code.

You can navigate the field structure from the panel or simply paste the expression below into the expression text box.
`#{ExperiencePlatform.ProfileFieldGroup.profile.homeAddress.postalCode}`

![Demo](./images/jo12.png)

Click `OK`.

![Demo](./images/jook.png)

Rename the path from path1 to 'Clear'

<!---
![Demo](./images/jopath2name.png)
--->

<kbd><img src="./images/jopath2name.png"  /></kdb>

Hit Ok on the top right

![Demo](./images/joocok.png)

Next, we will be adding in Actions.

#### Add Actions for Raining Path

We'll attempt to send an SMS message to our customer.

Your Journey will then look like this. Click on `Actions` as indicated in the screenshot.

![Demo](./images/joa8.png)

Select the smsNexmoemailAddress - action (your emailAddress), then drag and drop it after the condition you just added.

![Demo](./images/joa9.png)

You'll see a popup.

<!---
![Demo](./images/joa10.png)
--->

<kbd><img src="./images/joa10.png"  /></kdb>

Navigate to the `Action Parameters`.

<!---
![Demo](./images/joa11.png)
--->

<kbd><img src="./images/joa11.png"  /></kdb>

Click on the `Edit`-icon for the Action Parameter `Mobile PhoneNumber`.

![Demo](./images/joa12.png)

In the popup, you'll see, click on `Advanced Mode`.

![Demo](./images/jo8.png)

Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

`#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}`

![Demo](./images/joa14.png)

Click `OK`.

Click on the `Edit`-icon for the Action Parameter `Message`.

<!---
![Demo](./images/joa15.png)
--->

<kbd><img src="./images/joa15.png"  /></kdb>

You'll see a popup with the `Simple Mode Editor`.

![Demo](./images/joasm.png)

In the popup, you'll see, click on `Advanced Mode`.

![Demo](./images/jo8.png)

Paste this code in the `Advanced Mode Editor`. Click `OK`.

`"Hi "+ #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} +" don't let it rain on your investments, chat with our Advisors now."`

![Demo](./images/joa16.png)

Click `OK`.

![Demo](./images/joocok.png)

Click `OK`.

<!---
![Demo](./images/joa17.png)
--->

<kbd><img src="./images/joa17.png"  /></kdb>

In the left menu, go back to `Actions`, select the Action `slackNotification`, then drag and drop it after the `smsNexmoemailAddress`-Action (Replace emailAddress).

<!---
![Demo](./images/joa18.png)
--->

<kbd><img src="./images/joa18.png"  /></kdb>

Go to `Action Parameters` and click the `Edit`-icon for the parameter `Message`.

<!---
![Demo](./images/joa19.png)
--->

<kbd><img src="./images/joa19.png"  /></kdb>

In the popup window, click `Advanced Mode`.

![Demo](./images/joa20.png)

Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

`"Hi "+ #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} +" don't let it rain on your investments, chat with our Advisors now."`

![Demo](./images/joa21.png)

Click `OK`.

![Demo](./images/joocok.png)

Click `OK`.

<!---
![Demo](./images/joa22.png)
--->

<kbd><img src="./images/joa22.png"  /></kdb>

In the left menu, go to `Orchestration`, select `End`, then drag and drop `End` after the `textSlackLdap`-Action.

<!---
![Demo](./images/joa23.png)
--->

<kbd><img src="./images/joa23.png"  /></kdb>

#### Add Actions for Clear Weather Path

We'll attempt to send an SMS message to our customer.

Your Journey will then look like this. Click on `Actions` as indicated in the screenshot.

![Demo](./images/joapath21.png)

Select the smsNexmoemailAddress - action (your emailAddress), then drag and drop it after the condition you just added.

<!---
![Demo](./images/joapath22.png)
--->

<kbd><img src="./images/joapath22.png"  /></kdb>

You'll see a popup.

<!---
![Demo](./images/joa10.png)
--->

<kbd><img src="./images/joa10.png"  /></kdb>

Navigate to the `Action Parameters`.

<!---
![Demo](./images/joa11.png)
--->

<kbd><img src="./images/joa11.png"  /></kdb>

Click on the `Edit`-icon for the Action Parameter `Mobile PhoneNumber`.

![Demo](./images/joa12.png)

In the popup, you'll see, click on `Advanced Mode`.

![Demo](./images/jo8.png)

Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

`#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}`

![Demo](./images/joa14.png)

Click `OK`.

![Demo](./images/joaok.png)

Click on the `Edit`-icon for the Action Parameter `Message`.

<!---
![Demo](./images/joa15.png)
--->

<kbd><img src="./images/joa15.png"  /></kdb>

You'll see a popup with the `Simple Mode Editor`.

![Demo](./images/joasm.png)

In the popup, you'll see, click on `Advanced Mode`.

![Demo](./images/jo8.png)

Paste this code in the `Advanced Mode Editor`. Click `OK`.

`"Hi "+ #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} +" have a clear path to Retirement, chat with our Advisors now."`

![Demo](./images/joapath216.png)

Click `OK`.

![Demo](./images/joocok.png)

Click `OK`.

<!---
![Demo](./images/joapath217.png)
--->

<kbd><img src="./images/joapath217.png"  /></kdb>

In the left menu, go back to `Actions`, select the Action `slackNotification`, then drag and drop it after the `smsNexmoemailAddress`-Action (Replace emailAddress).

<!---
![Demo](./images/joapath218.png)
--->

<kbd><img src="./images/joapath218.png"  /></kdb>

Go to `Action Parameters` and click the `Edit`-icon for the parameter `Message`.

<!---
![Demo](./images/joa19.png)
--->

<kbd><img src="./images/joa19.png"  /></kdb>

In the popup window, click `Advanced Mode`.

![Demo](./images/joa20.png)

Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

`"Hi "+ #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} +" have a clear path to Retirement, chat with our Advisors now."`

![Demo](./images/joapath221.png)

Click `OK`.

![Demo](./images/joaok.png)

Click `OK`.

<!---
![Demo](./images/joapath222.png)
--->

<kbd><img src="./images/joapath222.png"  /></kdb>

In the left menu, go to `Orchestration`, select `End`, then drag and drop `End` after the `textSlackLdap`-Action.

<!---
![Demo](./images/joapath223.png)
--->

<kbd><img src="./images/joapath223.png"  /></kdb>

Your Journey is now fully configured.

![Demo](./images/jodone.png)

Click `Publish`.

![Demo](./images/jopublish.png)

Click `Publish`.

![Demo](./images/jopublish1.png)

Your Journey is now published.

![Demo](./images/jopublish2.png)

---
