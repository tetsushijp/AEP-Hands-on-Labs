**B2B Segmentation Exercise 3**
==========
Overview: Create a segment of all contacts who are directly involved on an opportunity at account "Devpoint" with an opportunity value > 500k  (Uses Opportunity Person Relation) 

1)	Navigate to Segments in the left navigation and select ‘Create Segment’ in the top right.
  
![Demo](./images/1_CreateSegmentButton.png)

2)	Click the gear icon to the right of Fields in the left pane and verify ‘Show full XDM schema’ is selected.
   
![Demo](./images/2_ShowFullXDM.png)

3)	Click the gear icon again to hide the setting.
  

4)	In the left pane, select ‘Attributes’ under Fields.
   
![Demo](./images/4_ClickAttrib.png)

5)	Click on ‘XDM Individual Profile’ under Browse Attributes. 
   
![Demo](./images/5_ClickIndivProfile.png)

6)	In the left pane, drill down through the folder structure to ‘B2B > Person Key > Opportunities > Opportunity Key > Opportunity > Account Key > Account’. This is accessing only opportunities that are directly associated with contacts, then traversing to account details. 
  
![Demo](./images/6_OpptyAcctName.png)
 
7)	Drag the ‘Account Name’ field on to the segment canvas.
  
![Demo](./images/7_dragacctname.png)
 
8)	In the text box to the right of ‘equals’, type “Devpoint” and press Enter.
  
![Demo](./images/8_acctname.png)
 
9)	In the folder tree on the left, back up 2 levels to ‘B2B > Person Key > Opportunities > Opportunity Key > Opportunity’.
  
![Demo](./images/9_opptyinfo.png)
 
10)	Drag the ‘Closed Flag’ field over to the segment canvas underneath the gray ‘Account Name’ containers where it says ‘Add attribute or audience’. 
  
![Demo](./images/10_dragclosedflag.png)

11)	To the right of ‘Closed Flag’ in the segment canvas, select ‘False’.
  
![Demo](./images/11_closedflagfalse.png)
 
12)	In the folder tree on the left, select the ‘Opportunity Amount’ folder. 
  
![Demo](./images/12_opptyamt.png)
 
13)	Drag the ‘Amount’ field over to the segment canvas underneath the gray ‘Closed Flag’ containers where it says ‘Add attribute or audience’.
  
![Demo](./images/13_dragamt.png)
 
14)	To the right of the ‘Amount’ field, change the operator to ‘is greater than’ and enter an amount of  500,000.
  
![Demo](./images/14_amt.png)
 
15)	Name your segment ‘Contacts involved in Opportunity at Devpoint’ followed by your lab attendee number. (Ex - Contacts involved in Opportunity at Devpoint 023)
  
![Demo](./images/15_nameit.png)
 
16)	Save the Segment by clicking Save in the top right
  
 

