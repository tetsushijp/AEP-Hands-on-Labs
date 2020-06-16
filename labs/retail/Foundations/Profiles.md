Lab 5.1 - Profiles - UPS Review
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>In this lab, you will look up your Customer Profile.
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
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_segments.png?raw=true" alt="Profiles"></td>
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

In Adobe Experience Platform there's a new feature of visualizing the entire real-time customer profile. This one feature is what all of our customer's have been trying to get for years: a single view of the customer.

Instructions:
-----------------
<ol>
<li>Log in to Adobe Experience Platform by going to this URL: https://platform.adobe.com</li>
<li>After logging in, you'll land on the homepage of Adobe Experience Platform.</li>
<li>Make sure you are in the 'Prod(VA7)' instance and not in your sandbox instance.</li>
<li>In the menu on the left side, go to Profiles.</li>
<li>Click on the 'Browse' tab. You will see a UI in which a namespace and an ID can be entered.</li>
      
      <kbd><img src="./images/profile_view.png"  /></kbd>
      
<li>Next, go to https://americaspot5-publish.adobedemo.com/content/ch_robinson/language-masters/en.html in a browser.</li>
<li>In the left margin, click on the “person” icon. This will display the X-ray panel from this website.</li>
<li>Expand the 'Real-time Customer Profile section'. </li>
<li>Observe the identities and their linkage to a namespace.</li>
<li>Copy the value for ECID</li>
<li>Go back to Profile view page in Experience Platform.</li>
<li>Select ECID from the Namespace dropdown and paste the value copied in the step above to view your Profile.</li>
</ol>


Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/media/README.md#lab-agenda)
