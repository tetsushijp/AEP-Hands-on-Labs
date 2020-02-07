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
1. In the left navigation, select ‘Attributes’ under ‘Fields’
2. Select ‘XDM Indvidual Profile’ under ‘Browse Attributes’
3. Select ‘Adobeamericaspot 2’ under ‘Attributes’ > ‘XDM Individual Profile’
4. Expand the ‘Student’ object
5. Once the fields display, drag ‘jobTitle’ over to the Segment Canvas.
6. Finish creating the segment where ‘jobTitle’ contains ‘manager’
7. In the Segment properties pane, select the ‘Refresh estimate’ link
8. Please do not save your segment

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
1. In the left navigation, select ‘Events’ under ‘Fields’
2. Select ‘XDM ExperienceEvent’ under ‘Browse Classes’
3. Select ‘Experience’ under ‘Events > XDM ExperienceEvent’
4. Select ‘Analytics’ under ‘Events > XDMExperienceEvent > Experience’
5. Expand ‘Event 1 to 100’
6. Expand ‘Account Creation: Step 1 (event33)’
7. Drag the field to the Segment Canvas
8. Modify the condition for this field to ‘exists’
9. In the left navigation, click on ‘Event 1 to 11’
10. Click on ‘Account Creation: Step 2 (event34)’
11. Drag the field to the Segment Canvas to the right of the existing event
12. Modify the condition for this field to ‘exists’
13. Expand ‘Event 1 to 100’
14. Click on ‘Accounts Created’
15. Drag the field to the Segment Canvas to the right of the second event
16. Modify the condition for this field to ‘does not exist’
17. In the Segment properties pane, select the ‘Refresh estimate’ link
18. Please do not save you segment


<br>
<br>
<br>

 RETURN LINK HERE
 
 
