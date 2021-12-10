Lab  - Fallout
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This lab will show you how to understand customer paths through Fallout
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>none
           </td>
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
            <td valign="middle" height="70">CJA</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.10</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2021-12-09</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>


Now that we've reviewed Flow visualizations, let's move on to Fallouts.


**FALLOUT**

The Fallout visualization is great for understanding customer paths when there are specific points or events you want to account for. For example, measuring a process on the site.

1. Create a new panel, title it “Fallout” and ensure your date range for POT5 is March 18-30, 2020. Select the Fallout visualization as the starting point of the panel.

<kbd><img src="../Foundations/images/CJA-fallout-newfallout.png"  /></kbd>

The Fallout visualization requires touchpoints in the process you want to measure fall-through as well as fall-out for.

2. From the Components menu, click on the arrow to the right of the “Web page name" dimension, click on “Show items from the last X months” until the values show up, and search for “account".
      - Drag "Purchase: step 1" into the Add Touchpoint drop zone

<kbd><img src="../Foundations/images/CJA-fallout-accountcreate-dragdrop.png"  /></kbd>

We can see that 38,061 people have started the process of online purchase.

4. Next,
      - Drag "Purchase: step 2" into the Add Touchpoint drop zone
      - Drag "Purchase: thank you" into the Add Touchpoint drop zone
      - 
<kbd><img src="../Foundations/images/CJA-fallout3.JPG"  /></kbd>

We can see that out of 38,061 people who started the account creation process, 19,246 made it to the end goal

5. Right-click on “step 3” in the Fallout and review all the options you have to drill deeper into analysis.
      - Of particular interest is the ability to see where people go next after Step 3, if they **fall-through** (make it to the Thank You page) or **fall-out** (don't make it to the Thank You page)

<kbd><img src="../Foundations/images/CJA-fallout-analysisoptions.png"  /></kbd>
_(no action needed on this view)_

Let's see how many of these people call into the call center.

6. Remove the last step in the fallout by clicking on the "x" to the right of the last step.
      - Now drag the "Calls" metric and drop it into the Touchpoint drop zone

<kbd><img src="./Foundations/images/CJA-fallout-callsadded1.png"  /></kbd>

  We can see that there are 3,788 people that make it to step 2 and then call into the call center


  
  
### This completes the Fallout excercise in CJA
Next we will review how to create [Cohort](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/retail/CJA/CJA-Cohort.md) tables

