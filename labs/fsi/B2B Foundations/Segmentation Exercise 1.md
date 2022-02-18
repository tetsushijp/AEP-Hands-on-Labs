**B2B Segmentation Exercise 1**
==========
Exercise 1 - Create a segment for all contacts who have a position of "VP" who work at account "Yacero" and have visited the products webpage in the past 10 days.

1)	Navigate to Segment Builder in the left navigation

![Demo](./images/ClickSegments.png)

2)	Click ‘Create segment’ on the top right.

![Demo](./images/CreateSegmentButton.png)
 
3)	Click the gear icon to the right of Fields in the left pane

![Demo](./images/ClickGear.png)
 
4)	Verify ‘Show full XDM schema’ is selected, and if not, select it. Click on the gear icon again to hide the setting.

![Demo](./images/ShowFullXDM.png)
 
5)	Select ‘Attributes’ under Fields

![Demo](./images/ClickAttrib.png)
 
6)	 Click on ‘XDM Individual Profile’ under Browse Classes

![Demo](./images/ClickIndivProfile.png)
 
7)	Click on ‘Some Additional Person Work Details’ 

![Demo](./images/SomeAddWorkDetails.png)
 
8)	Drag the ‘Job Title’ field over to the Segment canvas

![Demo](./images/DragJobTitle.png)
 
9)	In the text box to the right of ‘equals’, type “VP” and press Enter to add the value to the list.

![Demo](./images/JobTitleVP.png)
 
10)	In the left pane, click ‘XDM Individual Profile’ to navigate back to the top level of the class.
![Demo](./images/ClicktoBacktoMainFolder.png)
 
11)	Now, drill down into the folder structure to get to Account level details by selecting ‘Person Components > Source Account Key > Account’. 

![Demo](./images/NavtoAcct.png)
 
12)	Drag the ‘Account Name’ field over to the Attributes section of the canvas, where it says ‘Add attribute or audience’.

![Demo](./images/AddAcctName.png)
 
13)	In the text box to the right of ‘equals’, type “Yacero” and press Enter to add the value to the list.

![Demo](./images/AddedAcctName.png)
 
14)	In the left pane, click ‘Events’ under Fields.

![Demo](./images/14_ClickEvent.png)
 
15)	Click ‘XDM Experience Event’ under Browse Classes

![Demo](./images/15_XDM_Event.png)
 
16)	Drill down into the folder structure to get to Web Details by selecting ‘Web > Web Page Details’.

![Demo](./images/16_WebPageDetails.png)
 
17)	Drag the ‘URL’ field over to the Events section of the canvas.

![Demo](./images/17_DragURL.png)
 
18)	Change the operator to "contains", and in the text box to the right, type “/products” and hit Enter.

![Demo](./images/18_addurlval2.png)
 
19)	At the top of the ‘Events’ canvas, update the time value to ‘In Last 7 Days’

![Demo](./images/19_InLast7Days2.png)
 
20)	Enter the segment name “VP Product Page Viewers at Yacero” followed by your lab attendee number. (Ex – “VP Product Page Viewers at Yacero 014”). 

![Demo](./images/20_Addname.png)
 
21)	Click ‘Save’ in the top right to save the segment.

![Demo](./images/21_save.png)
 
