B2P Hybrid Segment Exercise
=================
Synopsis: Create a hybrid segment including profiles who have an active personal savings account and work for account Yacero.

1)	From the Segments section, select the Browse tab, and click the ‘Create Segment’ button in the top right.  

![Demo](./images/1_createsegment.png)

2)	Click the gear icon to the right of Fields in the left pane.  

![Demo](./images/2_clickgear.png)

3)	Verify ‘Show full XDM schema’ is selected, and if not, select it. Click the gear icon again to hide the setting. 

![Demo](./images/3_showfullxdm.png)

4)	First we’ll be looking for a savings account transaction within the last 60 days. Start by clicking on ‘Events’ under ‘Fields’, then click ‘XDM Experience Event’. 

![Demo](./images/4_clickevents.png)

5)	Click on ‘Adobeamericaspot 1’ folder, then ‘transactionDetails’ folder, and drag ‘transactionName’ fields to the Events Canvas.  

![Demo](./images/5_dragtransname.png)

6)	In the text box under ‘Event Rules’, type ‘savings’ and hit Enter to add the value to the list.  

![Demo](./images/6_transname.png)

7)	In the ‘Events’ canvas select the ‘Any time’ time window selection, and select ‘Within (+/-)’. Change the days window to 60 days Before Today.  

![Demo](./images/7_timewindow.png)

8)	Now we need to add in some B2B elements to this segment. Start by clicking the Attributes tab on the left pane.  

![Demo](./images/8_attributes.png)

9)	In the folder tree, navigate to ‘XDM Individual Profile > Person Components > Source Account Key > Account’ to access the B2B Account fields.   

![Demo](./images/9_accountfields.png)

10)	Drag ‘Account Name’ field to the Attributes box in the Segment builder. 

![Demo](./images/10_accountnam.png)

11)	In the text box beside ‘Account Name’, type ‘Yacero’ and hit enter to add it to the list.  

![Demo](./images/11_yacero.png)

12)	In the Segment Properties window on the right side, name the segment ‘Active Savings Account who work at Yacero <sandbox#>’. Select ‘Save and Close’ to finish and save the segment. 

![Demo](./images/12_nameandfinish.png)
