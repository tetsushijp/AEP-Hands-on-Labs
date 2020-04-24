Lab  - Build an Orders schema (ExperienceEvent)
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This lab will show you how to construct a schema.
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
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Before we begin go to [https://platform.adobe.com/home](https://platform.adobe.com/home). Follow the instructions detailed below.

Instructions:
-----------------
1. In the left-hand menu, navigate to "Schemas"

      <!--
      ![Demo](./images/schemahome.png)
      -->
      
      <kbd><img src="./images/schemahome.png"  /></kbd> 
      
2. Click "Create Schema" on the top right

      <!--
      ![Demo](./images/schemacreate.png)
      -->
      
      <kbd><img src="./images/schemacreate.png"  /></kbd>
      
3. Click on "Untitled Schema" in the structure view

    <!---
    ![Demo](./images/schemaname.png)
    --->

    <kbd><img src="./images/schemaname.png"  /></kdb>


      
      
4. In the right-hand menu, name it "Subscription Schema &lt;your-assigned-number>" (Description is optional)
      
      <!--
      ![Demo](./images/schemaname1.png)
      -->
      
      <kbd><img src="./images/schemaname1.png"  /></kdb>

      
5. In the left-hand schema composition menu, click on the "Assign" button across from Class


    <!---
    ![Demo](./images/schemaclassassign.png)
    --->

    <kbd><img src="./images/schemaclassassign.png"  /></kdb>

      
      
    Here's where you can choose your base level schema behavior:
    - Time-based Events (ExperienceEvent)
    - Customer Snapshots (Profile)
     
      <!--
      ![Demo](./images/schemaclass.png)
      -->
      
      <kbd><img src="./images/schemaclass.png"  /></kdb>


      Note: There are other classes available out of the box that represent specific objects needed for Experience Modeling.

6. In this example, choose "XDM ExperienceEvent" and click "Assign class"

      <!--
      ![Demo](./images/schemaclass1.png)
      -->
      
      <kbd><img src="./images/schemaclass1.png"  /></kdb>
       
      
7. Now, click on the "Add" button across from "Mixins" on the left panel


    <!---
    ![Demo](./images/schemamixin.png)
    --->

    <kbd><img src="./images/schemamixin.png"  /></kdb>

      
      
      Here's where you can build your own Mixin or use a prior/similar Mixin object that conforms to your data.
           
      
8. In this lab we will be adding two pre-built mixins listed below

      - Subscription Details Mixin EE,
      - Identities Mixin EE
     
      Search for 'Subscription Details Mixin EE'. Select the mixin and hit Assign Mixin
      
     <!-- 
     ![Demo](./images/schemamixin1.png)
     -->
      <kbd><img src="./images/schemamixin1.png"  /></kdb>
      
      Your schema will now have the Subscription Details Mixin EE object and all of the fields within this object
      
      <!---
      ![Demo](./images/schemamixin2.png)
      --->

      <kbd><img src="./images/schemamixin2.png"  /></kdb>          
             
      Hit +Add to go back to the Mixin list
     
      <kbd><img src="./images/schemamixin3.png"  /></kdb>            
                 
      And, repeat the steps for the Identities Mixin EE.  Search for 'Identities Mixin EE'. Select the mixin and hit Assign Mixin 
                        
      <kbd><img src="./images/schemamixin19.png"  /></kdb>     
       
      Your schema will now have the Identities Mixin EE object and all of the fields within this object
      
      <kbd><img src="./images/schemamixin20.png"  /></kdb>
      
        
9. Now, we'll create a new Mixin from scratch. Go back and hit the +Add button on the left panel.

      <kbd><img src="./images/schemamixin6.png"  /></kdb>    
       
      
10. Select "Create new mixin" on the very top


      <kbd><img src="./images/schemamixin7.png"  /></kdb>    
      
      
11. Display name is "Account Details Mixin EE &lt;your-assigned-number>" and then hit 'Add Mixin'
      
    <!--  
    ![Demo](./images/schemamixin8.png)
    --> 
    <kbd><img src="./images/schemamixin8.png"  /></kdb>     
     
12. In the left-hand schema composition menu, click on your newly create Mixin (it should be highlighted now)


    <!---
    ![Demo](./images/schemamixin9.png)
    --->

    <kbd><img src="./images/schemamixin9.png"  /></kdb>   
       

13. Notice that on the Structure view a '+Add Field' appears next to the Schema name, Click it to start adding fields 


    <!---
    ![Demo](./images/schemamixin10.png)
    --->

    <kbd><img src="./images/schemamixin10.png"  /></kdb>   


14. On the Field Properties panel to the right add the following  
      - FieldName = accountDetails
      - Description = Account Details
      - Type = Object

    <!--  
    ![Demo](./images/schemamixin11.png)
    -->
    <kbd><img src="./images/schemamixin11.png"  /></kdb>    

    Scroll  down and hit Apply

    <!--  
    ![Demo](./images/schemaapply.png)
    -->
    <kbd><img src="./images/schemaapply.png"  /></kdb>    

15. Next, we will be adding fields to the 'accountDetails' object. Click "+Add Field" next to this object

    <!---
    ![Demo](./images/schemamixin12.png)
    --->

    <kbd><img src="./images/schemamixin12.png"  /></kdb>   

16. On the Field Properties panel to the right add the following  
      - FieldName = accountCurrentContractMonth
      - Description = Account Current Contract Month
      - Type = String

     <!-- 
     ![Demo](./images/schemamixin13.png)
     -->
     <kbd><img src="./images/schemamixin15.png"  /></kdb>   

     Scroll down and hit Apply

    <!--  
    ![Demo](./images/schemaapply.png)
    -->
    <kbd><img src="./images/schemaapply.png"  /></kdb>    

17. We will be adding two more fields to the 'accountDetails' object.  Click "+Add Field" next to the object

    <!---
    ![Demo](./images/schemamixin12.png)
    --->

    <kbd><img src="./images/schemamixin12.png"  /></kdb>

18. On the Field Properties panel to the right add the following  
      - FieldName = accountOriginChannel
      - Description = Account Origin Channel
      - Type = String

    <!--  
    ![Demo](./images/schemamixin14.png)
    -->
    <kbd><img src="./images/schemamixin21.png"  /></kdb>

    Scroll down and hit Apply

    <!--  
    ![Demo](./images/schemaapply.png)
    -->
    <kbd><img src="./images/schemaapply.png"  /></kdb>
    
19. Click "+Add Field" next to the 'accountDetails' object.

    <!---
    ![Demo](./images/schemamixin12.png)
    --->

    <kbd><img src="./images/schemamixin12.png"  /></kdb>

20. On the Field Properties panel to the right add the following  
      - FieldName = accountStatus
      - Description = Account Status
      - Type = String

    <!--  
    ![Demo](./images/schemamixin15.png)
    -->
    <kbd><img src="./images/schemamixin22.png"  /></kdb>

    Scroll down and hit Apply

    <!--  
    ![Demo](./images/schemaapply.png)
    -->
    <kbd><img src="./images/schemaapply.png"  /></kdb>
    
    
21. We are done with modeling the schema. Make sure that your schema structure looks like the one in the screenshot below
 
     <!---
     ![Demo](./images/schemafinal.png)
     --->
     <kbd><img src="./images/schemafinal.png"  /></kdb>

22.  Save your schema. hit Save on the top right corner.

      <kbd><img src="./images/segment_retail_ordersave.png"  /></kdb>
 
23. Congratulations!!! You have constructed your schema.
 
<br>
<br>
<br>


Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/retail/README.md#lab-agenda)

