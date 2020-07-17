Lab  - Activation of a Segment to a Destination 
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this exercise, we’ll share a segment created in a previous lab with the Google Ad Manager destination configured in AEP.</br>
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>Google Ad Manager Destination</td>
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
            <td valign="middle" height="70">2</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2020-07-17</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Instructions:
-----------------
1.	In the left navigation of AEP, select Destinations > Browse.
2.	Click ‘Adobe Americas POT 5’. 

![Demo](./images/act_browse.png)

3.	Once you select the destination, click on ‘Edit Activation’. This takes you to the Activate flow.

![Demo](./images/act_edit.png)
 
4.	In the Activate destination wizard > Select Segments step, select the checkbox for your version of the “Call Center Order” segment you created in the previous lab.

![Demo](./images/act_segment_step1.png)
 
5.	Select Next in the upper top corner of the workflow

![Demo](./images/act_segment_schedule_step2.png)

6.	On the Segment Schedule page, you can see the start date for sending data to the destination. Some destinations will display the frequency of sending data to the destination. Since we're activating a segment to Google, this will be sent to the destination once per day, and this is the only option for this destination.
7.	Click on ‘Next’ in the upper top corner of the workflow

![Demo](./images/act_segment_review_step3.png)

8.	On the Review page, you can see a summary of your selection. Please do not select 'Finish' for your segment in the lab; rather, select 'Cancel' to exit out the activation workflow.

<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/retail/README.md#lab-agenda)
