## Exercise 4 - Design a trigger-based Customer Journey

In this exercise, you'll create an Orchestrated Journey by making use of Journey Orchestration in combination with Adobe Experience Platform

1. Go to [https://experience.adobe.com/#/@adobeamericaspot5/home](https://experience.adobe.com/#/@adobeamericaspot5/home)

   You'll see the `Adobe Experience Cloud`-homepage.

   ![Demo](./images/aec.png)

2. Click on `Journey Orchestration`.

   ![Demo](./images/aecjo.png)

   Next, you'll see the `Journey Orchestration`-homepage, which shows all existing Journeys.

   ![Demo](./images/aecjoh.png)

3. Click `Create` to start creating your Journey.

   ![Demo](./images/jocreate.png)

   You'll then see a new, blank Journey.

   <!---
   ![Demo](./images/jonew.png)
   --->

   <kbd><img src="./images/jonew.png"  /></kdb>

4. Name the Journey **Subscription Page Abandonment emailAddress** and replace **emailAddress** with LDAP. In this example, the Journey Name is **Subscription Page Abandonment puchadha**. No other values must be set at this moment.

   <!---
   ![Demo](./images/joname.png)
   --->

   <kbd><img src="./images/joname.png"  /></kdb>

   Click `OK`.

   ![Demo](./images/jonameok.png)

5. On the left side of your screen, have a look at `Events`. You should see your previously create Event on that list. Select it, then drag and drop it on the Journey Canvas.

   ![Demo](./images/joevents.png)

   Your Journey then looks like this:

   ![Demo](./images/jo1.png)

6. Next, click on `Orchestration`.

   ![Demo](./images/jo2.png)

   You now see `Orchestration`-capabilities.

   ![Demo](./images/jo3.png)

7. Select `Wait`, then drag and drop it on the Journey Canvas, and update Amount of time tp 10 minutes.

   <!---
   ![Demo](./images/jo4.png)
   --->

   <kbd><img src="./images/jo4.png"  /></kdb>

8. Click `OK`.

   ![Demo](./images/jowaitok.png)

9. Select `Condition`, then drag and drop it on the Journey Canvas.

   ![Demo](./images/jocond1.png)

10. Click on the `Edit`-icon for the expression of Path1.

    <!---
    ![Demo](./images/jo6.png)
    --->

    <kbd><img src="./images/jo6.png"  /></kdb>

    You'll then see an empty `Simple Editor`-screen.

    ![Demo](./images/jo7.png)

    Our query will be a bit more advanced, so we'll need the `Advanced Mode`.

11. Click `Advanced Mode`.

    ![Demo](./images/jo8.png)

    You'll then see the `Advanced Editor` which allows code entry. Paste it in `count(#{ExperiencePlatform.ExperienceEvents.experienceevent.all(currentDataPackField.eventType =="subcribed" and currentDataPackField.timestamp > nowWithDelta(-1, "days"))._id}) > 0`

    You'll then see this.

    ![Demo](./images/jo10.png)

12. Click `OK`.

    ![Demo](./images/jook.png)

13. Rename the path from path1 to 'subscribed'

    <!---
    ![Demo](./images/jopath1name.png)
    --->

    <kbd><img src="./images/jopath1name.png"  /></kdb>

14. Next, check the other cases checkbox. This will add a fallback path if none of the previous paths are true for the profile. label this Path `did not subscribe`
    <!---
    ![Demo](./images/joc2.png)
    --->

    <kbd><img src="./images/joc2.png"  /></kdb>

15. Click `OK`.

    ![Demo](./images/jook.png)

16. Drag and drop the end activity for the subscribed path. We wont be communicating to profiles that have converted.

    <kbd><img src="./images/joc1end.png"  /></kdb>

17. Next, we will be adding in Actions

    #### Add Actions for did not subscribe Path

    We'll attempt to send an SMS message to our customer.

    Your Journey will then look like this.

    ![Demo](./images/joa8.png)

18. Click on `Actions` as indicated in the screenshot.

    Select the smsNexmoemailAddress - action (your emailAddress), then drag and drop it after the condition you just added.

    ![Demo](./images/joa9.png)

    You'll see a popup.

    <!---
    ![Demo](./images/joa10.png)
    --->

    <kbd><img src="./images/joa10.png"  /></kdb>

19. Navigate to the `Action Parameters`.

    <!---
    ![Demo](./images/joa11.png)
    --->

    <kbd><img src="./images/joa11.png"  /></kdb>

20. Click on the `Edit`-icon for the Action Parameter `Mobile PhoneNumber`.

    ![Demo](./images/joa12.png)

    In the popup, you'll see, click on `Advanced Mode`.

    ![Demo](./images/jo8.png)

    Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

    `#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}`

    ![Demo](./images/joa14.png)

21. Click `OK`.

22. Click on the `Edit`-icon for the Action Parameter `Message`.

    <!---
    ![Demo](./images/joa15.png)
    --->

    <kbd><img src="./images/joa15.png"  /></kdb>

    You'll see a popup with the `Simple Mode Editor`.

    ![Demo](./images/joasm.png)

    In the popup, you'll see, click on `Advanced Mode`.

    ![Demo](./images/jo8.png)

23. Paste this code in the `Advanced Mode Editor`. Click `OK`.

    `"Hi "+ #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} +", dont miss out on exclusive offers on your subscribtion."`

    ![Demo](./images/joa16.png)

24. Click `OK`.

    ![Demo](./images/joocok.png)

25. Click `OK`.

    <!---
    ![Demo](./images/joa17.png)
    --->

    <kbd><img src="./images/joa17.png"  /></kdb>

26. Select `Wait`, then drag and drop it on the Journey Canvas, and update Amount of time to 30 minutes.

   <!---
   ![Demo](./images/jo4.png)
   --->

<kbd><img src="./images/jowait2.png"  /></kdb>

28. Click `OK`.

    ![Demo](./images/jowaitok.png)

29. Select `Condition`, then drag and drop it on the Journey Canvas.

    ![Demo](./images/jocond2.png)

30. Click on the `Edit`-icon for the expression of Path1.

    <kbd><img src="./images/jo6.png"  /></kdb>

    You'll then see an empty `Simple Editor`-screen.

    ![Demo](./images/jo7.png)

    Our query will be a bit more advanced, so we'll need the `Advanced Mode`.

31. Click `Advanced Mode`.

    ![Demo](./images/jo8.png)

    You'll then see the `Advanced Editor` which allows code entry. Paste it in `#{getPropensityScoreemailAddress.propensityScoreemailAddress.propensityScore} >= 6` (replace emailAddress)

    You'll then see this.

    ![Demo](./images/jocond2exp.png)

32. Click the dynamic val :customerID in the top rigth. This is the place where we will pass in the customerID value to retrive the score

    ![Demo](./images/jocond2expdyval.png)

33. Pass in the ECID value by copy pasting this expression it in `@{subscriptionPageViewPuchadha._adobeamericaspot2.identification.ECID}`

    ![Demo](./images/jocond2expdyval2.png)

34. Click `OK`.

    ![Demo](./images/jook.png)

35. Rename the path from path1 to 'likely to subscribe'

    <!---
    ![Demo](./images/jopath1name.png)
    --->

    <kbd><img src="./images/jopropscrpathname.png"  /></kdb>

36. Next, check the other cases checkbox. This will add a fallback path if none of the previous paths are true for the profile. label this Path `low propensity to subscribe`
    <!---
    ![Demo](./images/joc2.png)
    --->

    <kbd><img src="./images/jopropscrpathname2.png"  /></kdb>

37. Click `OK`.

    ![Demo](./images/jook.png)

38. Drag and drop the end activity for the subscribed path. We wont be communicating to profiles that have converted.

    <kbd><img src="./images/jopropscrpathnameend.png"  /></kdb>

39. In the left menu, go back to `Actions`, select the Action `slackNotification`, then drag and drop it after

    <!---
    ![Demo](./images/joa18.png)
    --->

    <kbd><img src="./images/joa18.png"  /></kdb>

40. Go to `Action Parameters` and click the `Edit`-icon for the parameter `Message`.

    <!---
    ![Demo](./images/joa19.png)
    --->

    <kbd><img src="./images/joa19.png"  /></kdb>

    In the popup window, click `Advanced Mode`.

    ![Demo](./images/joa20.png)

41. Select the below code, copy it, and paste it in the `Advanced Mode Editor`.

    `@{subscriptionPageViewPuchadha._adobeamericaspot2.identification.ECID} + "Likely to suncscribe. Place an Outbound call to - " + #{ExperiencePlatform.ProfileFieldGroup.profile.homePhone.number}`

    ![Demo](./images/joa21.png)

42. Click `OK`.

    ![Demo](./images/joocok.png)

43. Click `OK`.

    <!---
    ![Demo](./images/joa22.png)
    --->

    <kbd><img src="./images/joa22.png"  /></kdb>

44. In the left menu, go to `Orchestration`, select `End`, then drag and drop `End` after the `SlackMessase`-Action.

    <!---
    ![Demo](./images/joapath223.png)
    --->

    <kbd><img src="./images/joapath223.png"  /></kdb>

    Your Journey is now fully configured.

    ![Demo](./images/jodone.png)

45. Click `Publish`.

    ![Demo](./images/jopublish.png)

46. Click `Publish`.

    ![Demo](./images/jopublish1.png)

    Your Journey is now published.

    ![Demo](./images/jopublish2.png)

---
