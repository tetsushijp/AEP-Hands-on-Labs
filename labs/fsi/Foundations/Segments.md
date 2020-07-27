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
      
8.	Click on ‘Adobeamericaspot 1’ to expand the objects below that namespace
      
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


Lab 6.2 - Segmentation - Profile Attribute with Experience Event Segmentation (Multi-Entity Segmentation)
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
      
13.	Click on ‘Adobeamericaspot 1’ to expand the objects below that namespace
      
      <kbd><img src="./images/.png"  /></kbd>

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

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi/README.md#lab-agenda)
 
 
