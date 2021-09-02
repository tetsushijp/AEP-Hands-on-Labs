Optional Exercise - Data Prep and Mapping to XDM Schema
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This short lab will show you the how to map a CSV file to a dataset and create custom mapping functions
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>
                            <li>schema and dataset in place
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
            <td valign="middle" height="70"><img src="https://github.com/adobe/AEP-Hands-on-Labs/blob/master/assets/images/left_hand_nav_menu_schemas.png?raw=true" alt="Schemas"></td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2021-09-01</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Before be begin go to [https://platform.adobe.com/home](https://platform.adobe.com/home). Follow the instructions detailed below.

Instructions:
-----------------

In this exercise, we will be demonstrating the CSV to XDM mapping functionality by mapping a CSV file to a previously created schema and creating some custom mapping functions for data prep.
Before we begin, make sure you have downloaded the exercise files from [HERE](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/media/lab_downloads.md).


1)	From the left hand menu, navigate to “Workflows”
2)	Click “Map CSV to XDM schema” under “Data Ingestion”, and then click “Launch” on the right.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/Workflow_start.png)

3)	Now we need to specify a dataset to map our CSV file to. In this case we are going to use the existing CRM dataset that was already created. In the “Target dataset” dropdown, select “CRM Profile Dataset”. 
4)	Name your Dataflow “CRM Custom CSV [your-attendee-number]” and click “Next”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images//Select_dataset.png) 

5)	Next we will load our data file. Drag and drop the ‘crm_data_001.csv’ file into the “Drag and drop files” box. Ensure the “Data format” is set to “Delimited” and “Delimiter” is set to “,”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/Drag_Drop_File.png)

6)	Once the file has loaded, a preview will appear on the right. Select “Next” to proceed.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/Data_preview.png)

7)	Now we will begin to map our file to the XDM schema structure. Based on source attribute names, Platform automatically provides intelligent recommendations for field mappings based on the dataset that you selected. In this case, the mappings for “country” and “email” need to be corrected. Hit the minus sign to the right of the “faxPhone.countryCode” and “emailFormat” mapping suggestion to remove this mapping. 
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/mapping_1st_screen_edit.png)

8)	After those have been removed, select the “+” sign beside the empty mapping to select a new target field. In the following pop up window, select “homeAddress > country” and “Save” to select the mapping for “country”. Repeat the same process for email and select “personalEmail > address” for the new target mapping.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/new_mapping.png) 

9)	Now let’s assume we need to create a custom field which uppercases and concatenates First Name and Last Name into a new Full Name field. We can do this by creating a calculated field. Underneath the “Source Schema” heading, select “+ Add calculated field”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/click_add_calculated_field.png) 

10)	In the “Create calculated field” dialog, select the “Field” tab, and add “first_name” and “last_name” source fields to the function editor. In between the two fields in the function editor, add ‘+“ “+’ as shown below, and hit the “Preview” button.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/full_name_1.png)

11)	Now let’s uppercase this new field. In the “Function” tab, find the “upper” function, add it to the function editor, and move your full name formula inside of the upper parenthesis and hit “Preview”. Make sure your preview looks good and hit “Save”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/full_name_2.png)

12)	Next we need to map this new field to a target destination. Beside the newly added source field, select “+”, map the field to “person > name > fullName” attribute, and select “Save”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/map_full_name.png)

13)	Last, we will do one more calculated field to write the current timestamp to the dataset. Select “Add calculated field” again, and this time in the editor, paste ‘dformat(timestamp(),"yyyy-MM-dd'T'HH:mm:ss.SSSX")’ to create a properly formatted timestamp in ISO-8601 format and hit “Save”.
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/dateformat.png)

14)	Finally, map the new timestamp field to “_repo > modifyDate”. 
![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/timestamp_map.png)

15)	At this point we will not finish the Workflow wizard and ingest the data, so select “Cancel” in the top right. Congrats on finishing the data mapping exploration exercise! 
 ![Demo](https://github.com/adobe/AEP-Hands-on-Labs/blob/0a72496b0e4376b87b335fd43d1cbc988737a952/labs/fsi/Foundations/images/finished.png)





