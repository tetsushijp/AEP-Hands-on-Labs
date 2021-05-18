Lab 6.1 - Segmentation - Profile Attribute Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a basic segment using a single field in Call Center ExperienceEvent.
</br>
<br>A marketer wants to create a basic segment for customers who report Account security issues with a Call Center representative.</br>
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>none</td>
     </tr>
</tbody>
</table>
</td>
</div>

<div align="right">
<td style="border: none;" valign="top">

<table>
<tbody valign="top">
      <tr>
            <td valign="middle" height="70"><b>section</b></td>
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_segments.png?raw=true" alt="Segments"></td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Instructions:
-----------------
1.	Navigate to Segment Builder in the left navigation

      <kbd><img src="./images/segmenthome.png"  /></kbd>

2.    Click "Create segment" on the top right.

      <kbd><img src="./images/createsegment.png"  /></kbd>

3.	Click the gear icon to the right of Fields in the left pane

      <kbd><img src="./images/segmentfieldsgear.png"  /></kbd>

4.	Verify ‘Show full XDM schema’ is selected, and if not, select it
           
      <kbd><img src="./images/segment_gear.png"  /></kbd>
      
5.	Click on the gear icon again to hide the setting

      <kbd><img src="./images/segmentfieldsgearclose.png"  /></kbd>

6.	Select ‘Events’ under Fields

      <kbd><img src="./images/segmentevents.png"  /></kbd>

7.	Click on ‘XDM ExperienceEvent’ under Browse Classes

      <kbd><img src="./images/segment_xdm_ee.png"  /></kbd>
      
8.	Click on ‘Adobedemoamericas 270’ to expand the objects below that namespace
      
      <kbd><img src="./images/segment_xdm_pot1.png"  /></kbd>

9.	Click on ‘callcenterDetails’
   
      <kbd><img src="./images/segment_xdm_calldetails.png"  /></kbd>      

10.	Drag the ‘callSelectedReason’ field over to the Segment canvas
            
      <kbd><img src="./images/segment_fsi_callselectedreason.png"  /></kbd>    
      
11.	In the text box to the right of equals, type “Account Security Issue” and press ‘Enter’
           
      <kbd><img src="./images/segment_fsi_account_security_issue.png"  /></kbd>  

12.	Enter the segment name “Call Center Account Security” followed by your Student ID (e.g. “Call Center Account Security 025”)
	<br>Enter the same value as the description
      
      <kbd><img src="./images/segment_fsi_segmentname.png"  /></kbd>       
           
13.	Save the Segment
           
      <kbd><img src="./images/segment_fsi_save.png"  /></kbd>  
      
NOTE: Estimate link may not show results if qualified profiles are statistically small and not recognized across datset scans 
<br>
<br>
<br>


Lab 6.2 - Segmentation - Profile Attribute with Experience Event Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a segment using both a Profile Attribute and ExperienceEvents. </br>
     <br>A marketer wants to create a segment of female customers that performed IRA (Traditional or Roth) transactions with a broker in the last 24 hours.</br>
     </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>none</td>
     </tr>
</tbody>
</table>
</td>
</div>

<div align="right">
<td style="border: none;" valign="top">

<table>
<tbody valign="top">
      <tr>
            <td valign="middle" height="70"><b>section</b></td>
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_segments.png?raw=true" alt="Segments"></td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Instructions:
-----------------
1.	Navigate to Segment Builder in the left navigation

      <kbd><img src="./images/segmenthome.png"  /></kbd>

2.    Click "Create segment" on the top right.

      <kbd><img src="./images/createsegment.png"  /></kbd>

3.	Click the gear icon to the right of Fields in the left pane

      <kbd><img src="./images/segmentfieldsgear.png"  /></kbd>

4.	Verify ‘Show full XDM schema’ is selected, and if not, select it
           
      <kbd><img src="./images/segment_gear.png"  /></kbd>
      
5.	Click on the gear icon again to hide the setting

      <kbd><img src="./images/segmentfieldsgearclose.png"  /></kbd>

6. 	Select ‘Attributes’ under Fields

	<kbd><img src="./images/segmentattributes.png"  /></kbd>

7.	Click on the ‘XDM Individual Profile’ object under Browse Attributes

	<kbd><img src="./images/segmentattributes_xdm.png"  /></kbd>

8.	Click on ‘Person’ 

	<kbd><img src="./images/segmentattributes_xdm_person.png"  /></kbd>

9.	Drag the ‘Gender’ field to the Segment canvas

	<kbd><img src="./images/segmentattributes_xdm_person_gender.png"  /></kbd>

10.	Start entering ‘Female’ in the text box and when the value displays, select it and press Enter. The ‘Gender’ field is an enum field to limit the values stored in that field.
	<kbd><img src="./images/segment_travel_me_gender.png"  /></kbd>

11.	Select ‘Events’ under Fields

       <kbd><img src="./images/segmentevents.png"  /></kbd>
       
12.	Click on ‘XDM ExperienceEvent’ under Browse Classes

      <kbd><img src="./images/segment_xdm_ee.png"  /></kbd>
      
13.	Click on ‘Adobedemoamericas 270’ to expand the objects below that namespace
      
       <kbd><img src="./images/segment_xdm_pot1.png"  /></kbd>

14.	Click on 'transactionDetails'

	<kbd><img src="./images/segment_transactiondetails.png"  /></kbd>

15.	Drag the ‘transactionMethod’ field over to the Segment canvas

	<kbd><img src="./images/segment_transactionmethod.png"  /></kbd>

16.	In the left pane, find 'transactionName' and drag it to the canvas below the 'transactionMethod' event so they are vertically stacked.  The AND operator should remain.

	<kbd><img src="./images/segment_transactionname.png"  /></kbd>

17.	In the segment canvas, select the 'transactionMethod' event. A container will appear below to configure the rule for the event.  In the text box to the right of equals, type “broker” and press ‘Enter’

	<kbd><img src="./images/transactionmethod_details.png"  /></kbd>

18.  In the segment canvas, select the 'transactionName' event.  In the event rule container, change the condition from equals to contains.  In the text box to the right of contains, type "IRA" and press 'Enter'

       <kbd><img src="./images/transactionname_details.png"  /></kbd>

19.  At the top of the ‘Events’ canvas, update the time value to ‘In last 24 Hour(s)’

   <kbd><img src="./images/segment_segment2_inlast.png"  /></kbd>

20.	Enter the segment name “Female IRA customer working with Broker” followed by your Student ID (e.g. “Female IRA customer working with Broker 025”)
	<br>Enter the same value as the description   
	
	<kbd><img src="./images/segment2_segmentname.png"  /></kbd>
           
21.	Save the Segment
           
      <kbd><img src="./images/segment_fsi_save.png"  /></kbd>  
 
<br>
<br>
<br>

# Lab 6.3 - Segmentation - Dynamic Segmentation

<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a segment using Commerce ExperienceEvents and dynamic segmentation. Dynamic segmentation solves the scalability problems marketers traditionally face when building segments for marketing campaigns or other use cases where setting up multiple variations of the same segment was required.</br>
      <br>On an ongoing basis, a financial institution wants to remarket to customers who have clicked through an email offer to a mortgage application, started filling out the online form, but have not completed the online form. </br><br><i>The financial institution uses the Checkout and Purchase events for the form events and uses the products variable to capture the form name.</i></br></td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>none</td>
     </tr>
</tbody>
</table>
</td>
</div>

<div align="right">
<td style="border: none;" valign="top">

<table>
<tbody valign="top">
      <tr>
            <td valign="middle" height="70"><b>section</b></td>
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_segments.png?raw=true" alt="Segments"></td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

## Instructions:

1. Navigate to Segment Builder in the left navigation and select Create segment.

   ![Demo](./images/segment_create.png)

2. Click the gear icon to the right of Fields in the left pane

3. Verify ‘Show full XDM schema’ is selected

   ![Demo](./images/segment_gear.png)

4. Click on the gear icon again to hide the setting

5. In the left pane, select ‘Events’ under Fields

6. In the search box, enter ‘eVar1’

   ![Demo](./images/segments_travel_dyn_mchannel.png)

7. Drag ‘eVar1’ to the segment canvas 

8. In the left pane, clear out the Search box

9. Under ‘Event Types’, locate ‘Checkouts’, and drag this to the segment canvas to the right of the ‘Any’ event

   ![Demo](./images/segments_travel_dyn_mchannel_email_checkout.png)

10. In the left pane, locate ‘Purchases’ and drag this to the segment canvas to the right of the ‘Checkouts’ event.

    ![Demo](./images/segments_travel_dyn_mchannel_email_purchase.png)

11. Click on ‘Any’ in the segment canvas

12. Type ‘Email’ in the text box to the right of ‘eVar1’ equals and press Enter

   ![Demo](./images/segments_travel_dyn_mchannel_any.png)

13. Click on ‘Checkouts' in the segment canvas

14. In the left pane, search for 'SKU'

15. Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Checkouts’

    ![Demo](./images/segments_travel_dyn_checkout_sku.png)

16. Change the operator to “exists”

    ![Demo](./images/segments_travel_dyn_skuexists.png)

17. Clear the search box. And Select 'Puchases' event.

18. Search for ‘SKU’ and drag that into the ‘XDM ExperienceEvent’ container for ‘Purchases’

    ![Demo](./images/segments_travel_dyn_purchase_sku.png)

19. Clear the search box

    ![Demo](./images/segments_travel_dyn_browsevarmenu.png)

20. Now, we are going to make this a dynamic segment. We will be using the SKU from previous events to make sure that that same SKU is being checked for the subsequent events in the segment. To make is easy for the users segment builder visualizes these parameters under 'Browse Variables' in the left panel.

    ![Demo](./images/segments_travel_dyn_browsevarmenu_highlight.png)

21. Select the 'Checkout Product List Items Varaibles amd drag and drop the SKU to the condition section that says 'Add to compare operants.

    ![Demo](./images/segments_travel_dyn_compare_operands.png)

22. The dynamic condition should now look like this

    ![Demo](./images/segments_travel_dyn_condition.png)

23. Change the ‘XDM ExperienceEvent’ container for ‘Purchases1’ to ‘Exclude’

    ![Demo](./images/segments_travel_dyn_purchases_exclude.png)

24. At the top of the ‘Events’ canvas, update the time value to ‘In last 24 Hour(s)’

25. Enter the segment name “Email Channel Online Application Abandoners”.

26. Enter the same value as the description

29. Save the Segment

    ![Demo](./images/segment_final.png)
<br>
<br>
<br>  
Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi6/README.md#lab-agenda)
 
 
