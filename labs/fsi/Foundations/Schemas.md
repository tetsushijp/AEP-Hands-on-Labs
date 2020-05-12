# Lab - Build a Transactions schema (ExperienceEvent)

<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This long lab will show you how to construct 
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

Go to [https://platform.adobe.com/home](https://platform.adobe.com/home). Follow the instructions detailed below.

## Instructions:

1. In the left-hand menu, navigate to "Schemas"


      ![Demo](./images/schemahome.png)

2. Click "Create Schema" on the top right


      ![Demo](./images/schemacreate.png)

3. Click on "Untitled Schema" in the structure view


    <kbd><img src="./images/schemaname.png"  /></kdb>

4. In the right-hand menu, name it "Transactions Schema [your-assigned-number]" (Description is optional)
   ![Demo](./images/schemaname1.png)
5. In the left-hand schema composition menu, click on the "Assign" button across from Class

   <kbd><img src="./images/schemaclassassign.png"  /></kdb>


    Here's where you can choose your base level schema behavior:
    - Time-based Events (ExperienceEvent)
    - Customer Snapshots (Profile)


      ![Demo](./images/schemaclass.png)


      Note: There are other classes available out of the box that represent specific objects needed for Experience Modeling.

6. In this example, choose "XDM ExperienceEvent" and click "Assign class"


      ![Demo](./images/schemaclass1.png)

7. Now, click on the "Add" button across from "Mixins" on the left panel


    <kbd><img src="./images/schemamixin.png"  /></kdb>


      Here's where you can build your own Mixin or use a prior/similar Mixin object that conforms to your data.

8. In this lab, we will be adding two pre-built mixins listed below:

   - Identities Mixin EE
   - Transaction Details Mixin EE

   Search for 'Identities Mixin EE'. Select the mixin and click "Assign Mixin".

   Your schema will now have the identification object and all of the fields within this object.


      <kbd><img src="./images/schemamixin2.png"  /></kdb>


      Hit +Add to go back to the Mixin list


       <kbd><img src="./images/schemamixin3.png"  /></kdb>



      Repeat the steps for 'Identities Mixin EE' mixin


       ![Demo](./images/schemamixin4.png)

9. Now, we'll also create a new Mixin from scratch. Go back and hit the +Add button on the left panel.

   <kbd><img src="./images/schemamixin6.png"  /></kdb>

10. Click "Create new mixin" at the top.


      ![Demo](./images/schemamixin7.png)

13. Enter "Order Details Mixin EE [your-assigned-number]" as the "Display name" and click "Add Mixin".
    ![Demo](./images/schemamixin8.png)
14. In the left-hand schema composition menu, click on your newly create Mixin (it should be highlighted now)


    <kbd><img src="./images/schemamixin9.png"  /></kdb>

15. Notice that on the Structure view a '+Add Field' appears next to the Schema name, Click it to start adding fields


    <kbd><img src="./images/schemamixin10.png"  /></kdb>

16. On the Field Properties panel to the right add the following  
     FieldName = orderDetails
    Description = Order Details
    Type = Object


    ![Demo](./images/schemamixin11.png)


    Scroll  down and hit Apply


    ![Demo](./images/schemaapply.png)

17. Next, we will be adding fields to the 'orderDetails' object Click "+Add Field" next to this object

    <kbd><img src="./images/schemamixin12.png"  /></kdb>

18) On the Field Properties panel to the right add the following  
     FieldName = orderFlag
    Description = Order Flag
    Type = Integer


     ![Demo](./images/schemamixin13.png)


     Scroll down and hit Apply


    ![Demo](./images/schemaapply.png)

19. We will be adding one more field to the 'orderDetails' object Click "+Add Field" next to this object


    <kbd><img src="./images/schemamixin12.png"  /></kdb>

20. On the Field Properties panel to the right add the following  
     FieldName = orderID
    Description = Order ID
    Type = String

    ![Demo](./images/schemamixin14.png)


    Scroll down and hit Apply


    ![Demo](./images/schemaapply.png)

19. Next, We will be adding our final field to the 'orderDetails' object Click "+Add Field" next to this object

    <kbd><img src="./images/schemamixin15.png"  /></kdb>

20. On the Field Properties panel to the right add the following  
     FieldName = orderType
    Description = Order Type
    Type = String


    ![Demo](./images/schemamixin15.png)


    Scroll down and hit Apply


    ![Demo](./images/schemaapply.png)

21. We are done with modeling the schema. To Save your work hit Save on the top right corner. Make sure that your schema structure looks like the one in the screenshot below

    <kbd><img src="./images/schemafinal.png"  /></kdb>

22. Congratulations!!! you have constructed your schema.

<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi/README.md#lab-agenda)
