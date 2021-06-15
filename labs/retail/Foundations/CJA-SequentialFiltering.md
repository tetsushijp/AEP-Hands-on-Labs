Lab  - Sequential Filtering
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This lab will show you how to analyze customer paths through Sequential Filtering      </td>
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
            <td valign="middle" height="70">2021-05-24</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>



We just reviewed the Cohorts lab, now let's review Sequential Filtering.


**SEQUENTIAL FILTERING**

Filters can be used to understand customers who follow a particular path or journey. Sequential Filters is a very powerful way of doing this.

1. Open the Filter Builder by clicking on the "+" to the right of Filters in the Components menu. This will bring you to the filter configuration screen

<kbd><img src="./images/CJA-sequentialfilter-filterbuilder.png"  /></kbd>

Let's say that we want to dig deeper into the Account Creation Process we were measuring with the Fallout visualization earlier.
We want to create a Filter that allows us to measure the People that hit Step 1 of the Account Creation process and then call within 1 day.

2. Lets configure the filter:
      - Drag the "Web page name" dimension from the Components menu into the drop zone
      - Type in "create account: step 1" into the select value field
      - Drag the "Calls" metric and drop it under the criteria for the "webPagename"
      - Change the "equals 1" for Calls to "exists"
      - Click on the "And" between the two and change it to "Then"
      - Click on the clock image to the right of "Then" and select "within"
      - Change the "Week(s)" to Day(s)
      - Change the Include from "Event" to Person"
      - Give the Filter a name of "Account Creation Start - Call within 1 Day“
      - Click “Save”

<kbd><img src="./images/CJA-sequentialfilter-step1calls.png"  /></kbd>

This filter will find people who hit the first step of the Account Creation process and made a call within 1 day

3. Now create a new panel below the last panel we just worked on, title it “Sequential Filtering”, ensure your date range for POT5 is March 18-30, 2020 and select the Freeform table.
      - Drag the “Call reason" dimension into the table
      - Drag the “People” metric into the table, twice so that they’re side by side (you’ll have 2 identical “People” metrics next to each other)
      - Now drag the new filter we just created underneath one the "People" metrics to "Filter" the metric by those people

<kbd><img src="./images/CJA-sequentialfilter-callsvsstep1calls.png"  /></kbd>

Now we can see the volume of Calls vs. the volume Calls that also made it to step 1 of the Account Creation process. This is a great way to understand what People who made it to step 1 are calling about.
      - We can see from our filter that most of them call about a Payment Issue or Account Password Help


### This completes the Sequential Filtering excercise in CJA
Next we will review how to create [Venn Visualizations](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/retail/Foundations/CJA-Venn.md)
