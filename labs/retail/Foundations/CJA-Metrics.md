Lab  - Build a CJA Dashboard
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This lab will show you how to utilize and create Metrics.
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
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_schemas.png?raw=true" alt="Identities"></td>
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

Before we begin:
1. Navigate to [https://experience.adobe.com](https://experience.adobe.com)
2. Login with provided credentials
3. Click on "Customer Journey Analytics" from the Quick Access bar, or navigate to 
4. Click "Projects" in the top navigation
5. Click "Create New Project"

Introduction to Analysis Workspace Interface:
-----------------
The left side rail contains the Panel menu (where new panels can be dragged to the project), the Visualization menu (where visualizations can be dragged to a panel), and the Components menu (where Dimensions, Metrics and Filters are found and can be dragged to the panel visualizations).
If you're familiar with Adobe Analytics Workspace Analysis, you'll notice several features in CJA have been renamed to align with industry standards. Some updated names include:
- Segments are now known as 'Filters'
- Virtual Report Suites are now known as 'Data Views'
- Classifications are now known as 'Lookup datasets'
- Customer attributes are now known as 'Profile datasets'
- Hit containers are now known as 'Event' containers
- Visit containers are now known as 'Session' containers
- Visitor containers are now known as 'Person' containers
-----

There are obviously metrics that come out of the box, but there will be a need to create new custom metrics that measure more specific types of things. That's where **Calculated Metrics** come into play. Calculated Metrics allow you to build off of the base metrics and create much more specific metrics.

Let's build some Calculated Metrics using the filters we just created.
We'll start with a metric we'll call "Web Sessions" that represents Sessions where Web pages were touched.

1. Click on the "+" to the right of Metrics in the Components menu to bring up the Calculated Metric Builder.
      - Name the Calculated Metric "Web Sessions"
      - Drag the Web Sessions filter into the Definition drop zone
      - Drag the "Sessions" metric into the drop zone. This is what we are counting within the Calculated Metric we are creating
      - Click Save

This formula will calculate the Sessions where a customer touched at least one page.

<kbd><img src="./images/CJA-metrics-builder-websessions.png"  /></kbd>

2. We'll do the same thing to create a “Call Sessions" metric:
      - Click on the "i" to the right of the “Web Sessions” metric that we just created
      - Click the pencil to edit that metric in the Calculated Metric builder

<kbd><img src="./images/CJA-metrics-editcalcmetric.png"  /></kbd>

3. Once you’re in the Calculated Metric builder settings:
      - Change the name of the Calculated Metric to "Call Sessions"
      - Click the "x" to the right of the “Web Sessions” filter in the formula to remove that filter
      - Drop the “Call Sessions” filter where the “Web Sessions” filter was to filter Sessions by Sessions where a Call exists.
      - Click **Save As** to save the “Call Sessions" metric (and to not override the Web Sessions Calculated Metric we just created)

<kbd><img src="./images/CJA-metrics-builder-callsessions.png"  /></kbd>

4. We'll do the same thing to create a “Cross-Channel Sessions" metric:
      - Click on the "i" to the right of the “Call Sessions” metric that we just created
      - Click the pencil to edit that metric in the Calculated Metric builder
      - Change the name of the Calculated Metric from "Call Sessions“ to “Cross-Channel Sessions”
      - Click the "x" to the right of the “Call Sessions” filter in the formula to remove that filter
      - Drop the “Cross-Channel Sessions” filter where the “Call Sessions” filter was to filter Sessions by Sessions where a Cross-Channel session exists
      - Click **Save As** to save the “Cross-Channel Sessions" metric (and to not override the Call Sessions Calculated Metric we just created)

<kbd><img src="./images/CJA-metrics-builder-crosschannelsessions.png"  /></kbd>

Now that we've built these metrics, we can do some more interesting analysis.
For example, a Dashboard could be created that uses these metrics to measure the number of Web Sessions, Call Sessions, and Cross-Channel Sessions we're getting. Let's build it.

5. Create a new panel below the last panel we just worked on, title it “Metrics”, ensure your date range for POT5 is March 18-30, 2020 and select Freeform table.
      - Create a table with the “Day” dimension and the new Calculated Metrics we just created (Web Sessions, Call Sessions & Cross-Channel Sessions):

<kbd><img src="./images/CJA-metrics-daytable.png"  /></kbd>

6. Create another table with the “Web page name” dimension (instead of the “Day” dimension) and the same new Calculated Metrics we just created:

<kbd><img src="./images/CJA-metrics-pagenametable.png"  /></kbd>

This is an interesting view of the data because it allows us to understand what pages customers view in the same sessions where they also call into the call center. This is starting to give us a view into the pages that may be worthy of optimizing if we want to try to reduce calls into the call center by increasing self-service functionality on the website. We can go a level deeper here.

Let say we want to be able to see what pages customers interact with in the sessions where they call into the call center, broken out by the various call reasons. We can use the “Call reason" dimension to do this.

7. The top call reason for POT5 is “Order Created”, so lets add that to the panel filter drop zone to filter by those call types:
      - In the Components menu, click on the arrow to the right of the “Call reason” dimension to see the items within that dimension
      - Click "Show items from last X months" until values show
      - Drag & drop “Order Created” into the filter drop zone

<kbd><img src="./images/CJA-metrics-addordercreated.png"  /></kbd>

All data is now bucketed into a “No value” page item in the table using the “Web page name" dimension.

The reason for this: when you drop a filter into the filter drop zone, it creates an **Event-based** filter by default. Because there are no instances where someone can have a "Page View" event and "Call" event in the same Event (that would be impossible), no actual values populate within the "Web page name" table view. Since we are trying to find the Sessions where someone had a specific call type and see the pages they touched in those sessions, we need to change this filter to be **Session-based** instead of Event-based.

8. Hover over the Call Reason filter in the table 
      - Click on the "i"
      - Then click the pencil icon to edit the Event-based virtual filter that was created by default

<kbd><img src="./images/CJA-metrics-editordercreated.png"  /></kbd>

This brings us into the Filter Builder with the details of the virtual filter loaded.

9. Change the level of the filter to "Include" **Sessions** instead of **Events**. This will make it a session-based filter.
      - Click Save and view the impact it has on the Panel

<kbd><img src="./images/CJA-metrics-editordercreated-session.png"  /></kbd>

We can now see the pages customers see in the sessions that they call with an "Order Created" reason

<kbd><img src="./images/CJA-metrics-ordercreated-sessionbased.png"  /></kbd>

