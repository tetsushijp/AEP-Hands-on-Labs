**B2B DULE Exercise**
==========

Overview: Assign data governance label to data attributes in opportunity dataset such as opportunity amount and deal information. The use case is to prevent sensitive opportunity data from going out to destinations. 

1)	In the left navigation, select ‘Datasets’. Verify you are in the ‘Browse’ tab.
 
 ![Demo](./images/1_start.png)
 
2)	Click on the dataset named “B2B Opportunity Dataset”.
  
 ![Demo](./images/2_clickdataset.png)
 
3)	In the dataset viewer, select the ‘Data Governance’ tab.
  
 ![Demo](./images/3_datagov.png)
 
4)	In the Field search box, type “amount” and select the check box beside both “amount” fields (Expected Revenue and Opportunity Amount). Click ‘Edit governance labels’ in the top right dialog.
  
 ![Demo](./images/4_amount.png)
 
5)	In the ‘Edit governance labels’ pop up, expand ‘Contract Labels’. Select the check box beside ‘C2’ and click the ‘Save changes’ button.
  
 ![Demo](./images/5_label.png)
 
6)	Now that we have labeled our data, we need to create a Policy. On the left hand menu, navigate to ‘Policies’ under ‘Privacy’.  
 
 ![Demo](./images/6_policy.png)
 
7)	Under the ‘Browse’ tab, select ‘Create policy’.
 
 ![Demo](./images/7_createpolicy.png) 
 
8)	In the ‘Create Policy’ workflow, enter name “Custom Policy [attendee id]”. Under ‘Select governance labels’, select ‘C2’. On the right side, make sure ‘Contains all of the labels’ radio button is selected. Click ‘Next’ in the top right.
  
 ![Demo](./images/8_policyworkflow.png)
 
9)	Select ‘Export to Third Party’ and click the ‘Next’ button in the top right corner.
  
 ![Demo](./images/9_mktingaction.png)
 
10)	Review the policy and click ‘Finish’. 

 ![Demo](./images/10_finish.png)
