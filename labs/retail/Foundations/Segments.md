Lab 1 - Segmentation - Simple ExperienceEvent Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a basic segment using a single field in Call Center ExperienceEvent.</br>
      <br>On an ongoing basis, a retailer wants to create a basic segment for customers who place an order with a Call Center representative. This segment will be added to other segments for other marketing events.</br>
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
      <!--
      ![Demo](./images/segment_gear.png)
      -->
      
      <kbd><img src="./images/segment_gear.png"  /></kbd>
      
5.	Click on the gear icon again to hide the setting

      <kbd><img src="./images/segmentfieldsgearclose.png"  /></kbd>

6.	Select ‘Events’ under Fields

      <kbd><img src="./images/segmentevents.png"  /></kbd>

7.	Click on ‘XDM ExperienceEvent’ under Browse Classes

      <kbd><img src="./images/segment_xdm_ee.png"  /></kbd>
      
8.	Click on ‘Adobeamericaspot 5’ to expand the objects below that namespace
      
      <kbd><img src="./images/segment_xdm_pot5.png"  /></kbd>

9.	Click on ‘callcenterDetails’
   
      <kbd><img src="./images/segment_xdm_calldetails.png"  /></kbd>      

10.	Drag the ‘callSelectedReason’ field over to the Segment canvas
      <!--
      ![Demo](./images/segment_travel_callselectedreason.png)
      -->
      
      <kbd><img src="./images/segment_retail_callselectedreason.png"  /></kbd>    
      
11.	In the text box to the right of equals, type “Place Order” and press ‘Enter’
      <!--
      ![Demo](./images/segment_travel_reservationbooking.png)
      -->
      
      <kbd><img src="./images/segment_retail_placeorder.png"  /></kbd>  

12.	Ensure ‘Streaming’ is enabled in the right pane

      <kbd><img src="./images/segment_retail_streaming.png"  /></kbd>  

13.	Enter the segment name “Call Center Order” followed by your Student ID (e.g. “Call Center Order 025”)
	<br>Enter the same value as the description
      
      <kbd><img src="./images/segment_retail_segmentname.png"  /></kbd>       
           
14.	Save the Segment
      <!--
      ![Demo](./images/segment_travel_reservationbookingsave.png)
      -->
      
      <kbd><img src="./images/segment_retail_ordersave.png"  /></kbd>  
      
NOTE: Estimate link may not show results if qualified profiles are statistically small and not recognized across datset scans 
<br>
<br>
<br>


Lab 2 - Segmentation - Multi-Entity Sequential Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a segment using both a Profile Attribute and ExperienceEvents using a Sequential Segment that compares multiple event conditions</br>
      <br>This month, a retailer wants to email a promotional discount offer to existing female customers who have viewed or begun an online order for their premier product but have not ordered the item after an hour of either online event.</br></td>
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

4.	Verify ‘Show full XDM schema’ is selected and if not, select it

      <kbd><img src="./images/segment_gear.png"  /></kbd>

5.	Click on the gear icon again to hide the setting
    
      <kbd><img src="./images/segmentfieldsgearclose.png"  /></kbd>

6.	Select ‘Attributes’ under Fields

	<kbd><img src="./images/segmentattributes.png"  /></kbd>

7.	Click on the ‘XDM Individual Profile’ object under Browse Attributes

	<kbd><img src="./images/segmentattributes_xdm.png"  /></kbd>

8.	Click on ‘Person’ 

	<kbd><img src="./images/segmentattributes_xdm_person.png"  /></kbd>

9.	Drag the ‘Gender’ field to the Segment canvas

	<kbd><img src="./images/segmentattributes_xdm_person_gender.png"  /></kbd>

10.	Start entering ‘Female’ in the text box and when the value displays, select it and press Enter. The ‘Gender’ field is an enum field to limit the values stored in that field.
      <!--
      ![Demo](./images/segment_travel_me_gender.png)
      -->
     
     <kbd><img src="./images/segment_travel_me_gender.png"  /></kbd>
      
11.	Next, select ‘Events’ under Fields in the left pane

	<kbd><img src="./images/segmentevents.png"  /></kbd>

12.	Under ‘Event Types’ locate the ‘Product Views’ event and drag that to the segment canvas below the Profile attribute just added

	<kbd><img src="./images/segmentevent_prodview.png"  /></kbd>

13.	Under ‘Events’ in the left pane, locate ‘Checkouts’ and drag that to the segment canvas below the ‘Product Views’ event so that they are vertically stacked.

	<kbd><img src="./images/segmentevent_checkout.png"  /></kbd>

14.	Update the operator to ‘Or’ between ‘Product Views’ and ‘Checkouts’
      <!--
      ![Demo](./images/segment_travel_me_prodviewcheckout.png)
      -->
      <kbd><img src="./images/segment_travel_me_prodviewcheckout.png"  /></kbd>
      
15.	Under ‘Events in the left pane, locate ‘Purchases’ and drag that to the segment canvas to the right of the ‘Product Views’ and ‘Purchase’ events
      <!--
      ![Demo](./images/segment_travel_me_purchase.png)
      -->
            
       <kbd><img src="./images/segment_travel_me_purchase.png"  /></kbd>
            
16.	Click on ‘Product Views’ in the segment canvas. A container will appear below to Include a XDM ExperienceEvent

	<kbd><img src="./images/segment_prodview_container.png"  /></kbd>

17.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display

	<kbd><img src="./images/segment_xdm_prodlist.png"  /></kbd>

18.	Select the 'SKU' field and drag it into the ‘XDM ExperienceEvent’ container for ‘Product Views’

	<kbd><img src="./images/segment_xdm_prodsku.png"  /></kbd>

19.	Enter ‘prd1030’ in the text box to the right of productSKU = and press ‘Enter’
      <!--
      ![Demo](./images/segment_travel_me_pvsku.png)
      -->
      
	<kbd><img src="./images/segment_travel_me_pvsku.png"  /></kbd>

20.	Click on ‘Checkouts’ in the segment canvas. A container will appear below to Include a XDM ExperienceEvent

	<kbd><img src="./images/segment_xdm_checkout_container.png"  /></kbd>

20.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display

	<kbd><img src="./images/segment_xdm_prodlist.png"  /></kbd>

21.	Select the 'SKU' field and drag it into the ‘XDM ExperienceEvent’ container for ‘Product Views’

	<kbd><img src="./images/segment_xdm_checkout_prodsku.png"  /></kbd>

22.	Enter ‘prd1030’ in the text box to the right of prodSKU = and press ‘Enter’

	<kbd><img src="./images/segment_xdm_checkout_prodsku_value.png"  /></kbd>

23.	Click on ‘Purchases’ in the segment canvas. A container will appear below to Include a XDM ExperienceEvent

	<kbd><img src="./images/segment_xdm_purchase_container.png"  /></kbd>

23.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display

	<kbd><img src="./images/segment_xdm_prodlist.png"  /></kbd>

24.	Select the 'SKU' field and drag it into the ‘XDM ExperienceEvent’ container for ‘Product Views’

	<kbd><img src="./images/segment_xdm_purchase_prodsku.png"  /></kbd>

25.	Enter ‘prd1030’ in the text box to the right of SKU = and press ‘Enter’

	<kbd><img src="./images/segment_xdm_purchase_container_sku_value.png"  /></kbd>

26.	Change the container operator to ‘Exclude’ for ‘Purchases’
      <!--
      ![Demo](./images/segment_travel_me_purchasesku.png)
      -->
      
      <kbd><img src="./images/segment_travel_me_purchasesku.png"  /></kbd>
            
26.	At the top of the ‘Events’ canvas, update the time value to ‘This month’
	
	<kbd><img src="./images/segment_events_container_month.png"  /></kbd>

27.	In the middle, update the time value to ‘After 1 Hour’ between the ‘Product Views’ or ‘Checkouts’ and ‘Purchases’.
      <!--
      ![Demo](./images/segment_travel_me_purchasetime.png)
      -->
      
      <kbd><img src="./images/segment_events_purchasetime.png"  /></kbd>      
      
28.	Ensure ‘Streaming’ is enabled in the right pane

	<kbd><img src="./images/segment_properties_streaming.png"  /></kbd> 
	
29.	Enter the segment name “Premier Product High Intent Female Purchasers” followed by your Student ID (e.g. “Premier Product High Intent Female Purchasers 005”).  Enter the same value as the description

	<kbd><img src="./images/segment_properties_name.png"  /></kbd>

30.	Save the Segment
      <!--
      ![Demo](./images/segment_travel_me_save.png)
      -->
      
      <kbd><img src="./images/segment_retail_ordersave.png"  /></kbd>       
      
 
<br>
<br>
<br>

Lab 3 - Segmentation - Dynamic Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll create a segment using Commerce ExperienceEvents and dynamic segmentation. Dynamic segmentation solves the scalability problems marketers traditionally face when building segments for marketing campaigns or other use cases where setting up multiple variations of the same segment was required.</br>
      <br>On an ongoing basis, a retailer wants to remarket to customers who have clicked through an email offer for an item, started the order online in the last 3 days, but have not ordered the item within 1 day.</br></td>
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
      <!--
      ![Demo](./images/segment_gear.png)
      -->
      
      <kbd><img src="./images/segment_gear.png"  /></kbd>
      
5.	Click on the gear icon again to hide the setting

      <kbd><img src="./images/segmentfieldsgearclose.png"  /></kbd>

6.	Select ‘Events’ under Fields

      <kbd><img src="./images/segmentevents.png"  /></kbd>
      
7.	In the search box, enter ‘evar1’
      <!--
      ![Demo](./images/segments_travel_dyn_mchannel.png)
      -->
      
      <kbd><img src="./images/segments_retail_search_evar1.png"  /></kbd>      
            
8.	Under ‘Browse Classes’, drag ‘eVar1’ to the segment canvas.  (Be sure it follows this path:  XDM ExperienceEvent > Experience > Analytics > Custom Dimensions > eVars > eVar1)

	<kbd><img src="./images/segments_retail_evar1.png"  /></kbd>     

9.	In the left pane, clear out the Search box

	<kbd><img src="./images/segments_retail_search_evar1_clear.png"  /></kbd> 

10.	Under ‘Event Types’, locate ‘Checkouts, and drag this to the segment canvas to the right of the ‘Any’ event

	<kbd><img src="./images/segments_retail_xdm_checkouts.png"  /></kbd> 

11.	In the left pane, locate ‘Purchases’ and drag this to the segment canvas to the right of the ‘Checkouts’ event.

	<kbd><img src="./images/segments_retail_xdm_purchases.png"  /></kbd> 

12.	Click on ‘Any’ in the segment canvas

	<kbd><img src="./images/segments_retail_events_any.png"  /></kbd> 

13.	Type ‘Email’ in the text box to the right of ‘Marketing Channel (eVar1)’ equals and press Enter
      <!--
      ![Demo](./images/segments_travel_dyn_mchannel_email.png)
      -->
      
      <kbd><img src="./images/segments_retail_dyn_mchannel_email.png"  /></kbd>       
          
14.	Click on ‘Checkouts' in the Events canvas

	<kbd><img src="./images/segments_retail_events_checkouts.png"  /></kbd>       

15.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display

	<kbd><img src="./images/segment_xdm_prodlist.png"  /></kbd>

16.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Checkouts’

	<kbd><img src="./images/segment_3_xdm_checkouts_prodsku.png"  /></kbd>

17.	Change the operator to “exists”     
      <!--
      ![Demo](./images/segments_travel_dyn_skuexists.png)
      -->
      <kbd><img src="./images/segments_travel_dyn_skuexists.png"  /></kbd>          

18.	Click on ‘Purchases' in the Events canvas	

	<kbd><img src="./images/segments_retail_events_purchase.png"  /></kbd>    

19.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display

	<kbd><img src="./images/segment_xdm_prodlist.png"  /></kbd>

20.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Purchases’

	<kbd><img src="./images/segment_3_xdm_purchases_prodsku.png"  /></kbd>

21.	In the left pane, click on the Events link. 
      <!--
      ![Demo](./images/segments_travel_dyn_browsevarmenu.png)
      -->
      <kbd><img src="./images/segments_retail_dyn_backtobrowsemenu.png"  /></kbd>  
      
      You should see ‘Browse Classes’, ‘Event Types’ and ‘Browse Variables’ sections appear
      
      <kbd><img src="./images/segments_travel_dyn_browsevarmenu.png"  /></kbd>  
      
21.	Click on ‘Checkouts1 | Product list items1’

	<kbd><img src="./images/segments_retail_browsevarmenu_checkouts.png"  /></kbd>  

22.	Select the 'SKU' field and drag this to the right of ‘SKU equals’ in the ‘XDM Event Container’ for the Purchases event. Release once the dynamic variable is positioned over the second box displays and drop. 

	<kbd><img src="./images/segments_retail_browsevarmenu_checkouts_sku.png"  /></kbd>  

The resulting statement should be ‘SKU equals Checkouts1 | Product list items1 SKU XDM ExperienceEvent > Product list items > SKU’

   <kbd><img src="./images/segments_retail_xdm_purchase_dyn_checkoutsku.png"  /></kbd> 

22.	Change the ‘XDM ExperienceEvent’ container for ‘Purchases1’ to ‘Exclude’
      <!--
      ![Demo](./images/segments_travel_dyn_skuexists.png)
      -->

      <kbd><img src="./images/segments_retail_xdm_purchase_excludesku.png"  /></kbd>  
      
23.	In the segment canvas, update the time value between ‘Any’ and ‘Checkouts’ to ‘Within 3 days’

	<kbd><img src="./images/segments_retail_event_time1.png"  /></kbd>  

24.	Next, update the time value between ‘Checkouts’ and ‘Purchases’ to ‘Within 1 day’

	<kbd><img src="./images/segments_retail_event_time2.png"  /></kbd> 

25.	Ensure ‘Streaming’ is enabled in the right pane

	<kbd><img src="./images/segment_properties_streaming.png"  /></kbd>

26.	Enter the segment name “Email Channel Online Order Abandoners” followed by your Student ID (e.g. “Email Channel Online Order Abandoners 025”).  Enter the same value as the description

	<kbd><img src="./images/segment_properties_name3.png"  /></kbd>
	
27.	Save the Segment

	<kbd><img src="./images/segment_retail_ordersave.png"  /></kbd>   

<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/README.md#lab-agenda)
 
 
