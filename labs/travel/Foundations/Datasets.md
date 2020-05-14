# Lab - Construct a Dataset from Schema

<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective:</h3></td>
            <td valign="top"><br>This short lab will show you the how to quickly convert a schema into a dataset
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites:</h3></td>
           <td valign="top"><br>
                            <li>schema in place
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
            <td valign="middle" height="70">2020-01-06</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Before be begin go to [https://platform.adobe.com/home](https://platform.adobe.com/home). Follow the instructions detailed below.

## Instructions:

We will be creating a dataset for the schema we created in the previous exercise. Please follow the steps below

1. In the left-hand menu, navigate to "Datasets"

   ![Demo](./images/datasetshome.png)

2. Click “Create Dataset”

   ![Demo](./images/datasetcreate.png)

3. Since we will be creating the dataset from a schema definition please select ''Create dataset from schema'

   ![Demo](./images/datasetcreate2.png)

4. On the Select Schema page search for "Bookings EE Schema &lt;your-assigned-number>" then select the schema and hit Next

   ![Demo](./images/datasetschema.png)

5. Next, to configure the dataset we need to give it a name. Please name your dataset "Bookings EE Dataset <your-assigned-number>' and give it the same description

   ![Demo](./images/datasetname.png)

4) Hit Finish to save the dataset

   ![Demo](./images/datasetfinish.png)

5. We have successfully created the dataset, but this dataset has not ingested data. We will now import a file into this dataset. This time we will import a JSON file and it will simply need to be dragged and dropped into the dataset.

   On the right panel scroll down until you see the 'Add data' section

   ![Demo](./images/datasetadddata.png)

6. From the lab files you downloaded, drag and drop the 'bookings_data_001.json' file into the 'Add Data' sections. You will now see a batch with a 'Loading' status

   <kbd><img src="./images/datasetbatch.png"  /></kdb>

7. Adobe Experience Platform will perform the XDM mapping and conversion for JSON format to parquet and make this data available on the data lake and the profile store. Refresh the screen This process only takes afew seconds.

   Once your batch status is 'Success', you can preview the data by hitting the 'Preview Dataset' button on the top right corner.


    ![Demo](./images/datasetpreview.png)

8. Congratulations !!! you are done with the Dataset exercise.

<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/travel/README.md#lab-agenda)
