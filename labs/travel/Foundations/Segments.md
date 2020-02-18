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
            <td valign="top"><br>In this lab, you will learn how to create a segment based on a profile attribute/characteristic that has been mapped within unified profile
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
<ol>
      <li>In the left navigation, select 'Segments' if you are not already there.</li>
<li>In the upper right corner, select 'Create Segment'.</li>
<li>In the right pane within the 'Create Segment' interface, enter the segment name 'Female Segment' following by your Student Number (e.g. 'Female Segment 001'). Enter the same value in the Description field.</li>
<li>If the 'Streaming' toggle is not active, activate it.</li>
<li>In the left pane, drill down the 'XDM Individual Profile' under Attributes by clicking on it.</li>
<li>Scroll the resulting list until you locate 'Person'.</li>
<li>Click on 'Person' to expand the object. This will display information at the field level. One of the fields you should see is 'Gender'.</li>
<li>Drag 'Gender' over to the segment builder area.</li>
<li>Click on the list arrow to the right of 'Gender' equals and select 'Female'.</li>
<li>In the Segment properties pane, select the ‘Refresh estimate’ link.</li>
<li>Save your segment</li>
</ol>
NOTE: Estimate link may not show results if attribute or selection is statistically small and not recognized across datset scans 
<br>
<br>
<br>


Lab 6.2 - Segmentation - Profile Experience Event Segmentation
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>Similar to the prior lab, in this lab you will build a customer segment based on the unified experience event data (from EE Schemas/Datasets) that are streaming into plartform</td>
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
<ol>
 <li>In the left navigation, select 'Segments' if you are not already there.</li>
<li>In the upper right corner, select 'Create Segment'.</li>
<li>In the right pane within the 'Create Segment' interface, enter the segment name 'Account Creation Abandon' following by your Student Number (e.g. 'Account Creation Abandon 001'). Enter the same value in the Description field.</li>
<li>If the 'Streaming' toggle is not active, activate it.</li>
<li>In the left pane, drill down the 'XDM ExperienceEvent' under Evemts by clicking on it.</li>
<li>Scroll the resulting list until you locate 'Experience'.</li>
<li>Click on 'Experience' to expand the object. </li>
<li>Click on 'Analytics' to expand the object</li>
<li>Click on 'Event 1 to 100' to expand the object.</li>
<li>Click on 'Account Creation: Step 1'. This will display the field value for this event.</li>
<li>Drag the field to the Segment Canvas.</li>   
<li>In the left pane, click on the 'Event 1 to 100' link to display the event list again</li>
<li>Click on 'Account Creation: Step 2'. This will display the field value for this event.</li>     
<li>Drag the field to the right of the existing event in the Segment Canvas.</li>
<li>In the left pane, click on the 'Event 1 to 100' link to display the event list again</li>
<li>Click on 'Account Creation: Step 3'. This will display the field value for this event.</li>     
<li>Drag the field to the right of the last (second) event in the Segment Canvas.</li>
<li>You should now see three events positioned horizontally in the Segment Canvas. We're going to configure each event with a rule next.</li>
<li>Click on the leftmost event. You will see the rule editor activate below. Enter '1' in the Number field to modify the condition.</li>
<li>Click on the middle event. You will see the rule editor activate below. Enter '1' in the Number field to modify the condition.</li>
<li>Click on the last event. Click on the arrow to the right of 'equals' and select 'does not exist' from the list to modify the condition.</li>
<li>In the Segment properties pane, select the ‘Refresh estimate’ link.</li>
<li>Save your segment</li>
</ol>    
 
<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/README.md#lab-agenda)
 
 
