Lab - Segmentation - Simple ExperienceEvent Segmentation
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
      <br>On an ongoing basis, a hotelier wants to create a basic segment for customers who make a booking with a Call Center representative. This segment will be added to other segments for other marketing events.</br>
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
2.	Click the gear icon to the right of Fields in the left pane
3.	Verify ‘Show full XDM schema’ is selected, and if not, select it

      ![Demo](./images/segment_gear.png)

4.	Click on the gear icon again to hide the setting
5.	Select ‘Events’ under Fields
6.	Click on ‘XDM ExperienceEvent’ under Browse Classes
7.	Click on ‘Adobeamericaspot 3’ to expand the objects below that namespace
8.	Click on ‘Call Details’
9.	Drag the ‘Call Selected Reason’ field over to the Segment canvas

![Demo](./images/segment_travel_callselectedreason.png)

10.	In the text box to the right of equals, type “Reservation Place Booking” and press ‘Enter’

![Demo](./images/segment_travel_reservationbooking.png)

11.	Ensure ‘Streaming’ is enabled in the right pane
12.	Enter the segment name “Call Center Reservation Booking” followed by your Student ID (e.g. “Call Center “Reservation Booking 005”
13.	Enter the same value as the description
14.	Save the Segment

![Demo](./images/segment_travel_reservationbookingsave.png)
      
NOTE: Estimate link may not show results if qualified profiles are statistically small and not recognized across datset scans 
<br>
<br>
<br>


Lab - Segmentation - Multi-Entity Sequential Segmentation
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
      <br>This month, a hotelier wants to email a spa package offer to existing female customers who have viewed or begun an online booking for their Lily Suites property but have not booked the property after an hour of either online event.</br></td>
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
2.	Click the gear icon to the right of Fields in the left pane
3.	Verify ‘Show full XDM schema’ is selected
4.	Click on the gear icon again to hide the setting
5.	Select ‘Attributes’ under Fields
6.	Click on the ‘XDM Individual Profile’ object under Browse Attributes
7.	Click on ‘Person’ 
8.	Drag the ‘Gender’ field to the Segment canvas
9.	Start entering ‘Female’ in the text box and when the value displays, select it and press Enter. The ‘Gender’ field is an enum field to limit the values stored in that field.

![Demo](./images/segment_travel_me_gender.png)

10.	Next, select ‘Events’ under Fields in the left pane
11.	Under ‘Event Types’ locate the ‘Product Views’ event and drag that to the segment canvas below the Profile attribute just added
12.	Under ‘Events’ in the left pane, locate ‘Checkouts’ and drag that to the segment canvas below the ‘Product Views’ event so that they are vertically stacked.
13.	Update the operator to ‘Or’ between ‘Product Views’ and ‘Checkouts’

![Demo](./images/segment_travel_me_prodviewcheckout.png)

14.	Under ‘Events in the left pane, locate ‘Purchases’ and drag that to the segment canvas to the right of the ‘Product Views’ and ‘Purchase’ events

![Demo](./images/segment_travel_me_purchase.png)

15.	Click on ‘Product Views’ in the segment canvas. A container will appear below to Include and XDM ExperienceEvent
16.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display
17.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Product Views’
18.	Enter ‘prd1030’ in the text box to the right of SKU = and press ‘Enter’

![Demo](./images/segment_travel_me_pvsku.png)

19.	Click on ‘Checkouts’ in the segment canvas. A container will appear below to Include and XDM ExperienceEvent
20.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display
21.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Checkouts’
22.	Enter ‘prd1030’ in the text box to the right of SKU = and press ‘Enter’
23.	Click on ‘Purchases’ in the segment canvas. A container will appear below to Include and XDM ExperienceEvent
24.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display
25.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Purchases’
26.	Enter ‘prd1030’ in the text box to the right of SKU = and press ‘Enter’
27.	Change the container operator to ‘Exclude’ for ‘Purchases’

![Demo](./images/segment_travel_me_purchasesku.png)

28.	At the top of the ‘Events’ canvas, update the time value to ‘This month’
29.	In the middle, update the time value to ‘After 1 Hour’ between the ‘Product Views’ and ‘Checkouts’ and ‘Purchases’.

![Demo](./images/segment_travel_me_purchasetime.png)

30.	Ensure ‘Streaming’ is enabled in the right pane
31.	Enter the segment name “Lily Suites High Intent Female Bookers” followed by your Student ID (e.g. “Lily Suites High Intent Female Bookers 005”
32.	Enter the same value as the description
33.	Save the Segment

![Demo](./images/segment_travel_me_save.png)

 
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
      <br>On an ongoing basis, a hotelier wants to remarket to customers who have clicked through an email offer to any property, started the booking online within 3 days, but have not booked the hotel room within 1 day.</br></td>
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
2.	Click the gear icon to the right of Fields in the left pane
3.	Verify ‘Show full XDM schema’ is selected
4.	Click on the gear icon again to hide the setting
5.	In the left pane, select ‘Events’ under Fields
6.	In the search box, enter ‘Marketing Channel’

![Demo](./images/segments_travel_dyn_mchannel.png)

7.	Under ‘Browse Classes’, drag ‘Marketing Channel (eVar1)’ to the segment canvas.
8.	In the left pane, clear out the Search box
9.	Under ‘Event Types’, locate ‘Checkouts, and drag this to the segment canvas to the right of the ‘Any’ event
10.	In the left pane, locate ‘Purchases’ and drag this to the segment canvas to the right of the ‘Checkouts’ event.
11.	Click on ‘Any’ in the segment canvas
12.	Type ‘Email’ in the text box to the right of ‘Marketing Channel (eVar1)’ equals and press Enter

![Demo](./images/segments_travel_dyn_mchannel_email.png)

13.	Click on ‘Checkouts in the segment canvas
14.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display
15.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Checkouts’
16.	Change the operator to “exists”

![Demo](./images/segments_travel_dyn_prodlistitemmenu.png)
![Demo](./images/segments_travel_dyn_skuexists.png)

17.	In the left pane, click on ‘XDM ExperienceEvent’ and ‘Product list items’ in the resulting display
18.	Select the ‘SKU’ field and drag that into the ‘XDM ExperienceEvent’ container for ‘Purchases’
19.	In the left pane, click on the Events link. You should see ‘Browse Classes’, ‘Event Types’ and ‘Browse Variables’ sections appear

![Demo](./images/segments_travel_dyn_browsevarmenu.png)

20.	Locate ‘Checkouts1 | Product list items1’ and drag this to the right of ‘SKU equals’ in the ‘XDM Event Container’. Release one the dynamic variable is positioned over the second box displays and drop. The resulting statement should be ‘SKU equals Checkouts1 | Product list items1 XDM ExperienceEvent > Product list items > SKU’


21.	Change the ‘XDM ExperienceEvent’ container for ‘Purchases1’ to ‘Exclude’

![Demo](./images/segments_travel_dyn_skuexists.png)

22.	In the segment canvas, update the time value between ‘Any’ and ‘Checkouts’ to ‘Within 3 days’
23.	Next, update the time value between ‘’Any’ and ‘Purchases’ to ‘Within 1 day’
34.	Ensure ‘Streaming’ is enabled in the right pane
35.	Enter the segment name “Email Channel Online Reservation Abandoners” followed by your Student ID (e.g. “Email Channel Online Reservation Abandoners 005”
36.	Enter the same value as the description
24.	Save the Segment





Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/README.md#lab-agenda)
 
 
