Lab 2.1 - Construct a Dataset from Schema
==========
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

Instructions:
-----------------

We will be creating a dataset for the schema we created in the previous exercise. Please follow the steps below
1. In the left-hand menu, navigate to "Datasets"


      ![Demo](./images/datasetshome.png)
      
      
2. Click "+ Create Dataset" on the top right


      ![Demo](./images/datasetcreate.png)
      
      
3. Since we will be creating the dataset from a schema definition please select "Create dataset from schema"


      ![Demo](./images/datasetcreate2.png)
 
 
4. On the "Select schema" page, search for "Transactions Schema [your-assigned-number]" then select the schema and click "Next".
      
      
      ![Demo](./images/datasetschema.png)
      
      
5. Next, to configure the dataset we need to give it a name. Please name your dataset "Transactions Dataset [your-assigned-number]' and give it the same description 
      
      
      ![Demo](./images/datasetname.png) 
 
 
6. Click "Finish" to save the dataset
      
      
      ![Demo](./images/datasetfinish.png) 


7. We have successfully created the dataset, but this dataset has not ingested data. We will now import a file into this dataset. This time we will import a JSON file and it will simply need to be dragged and dropped into the dataset. 

    On the right panel, scroll down until you see the "ADD DATA" section

    ![Demo](./images/datasetadddata.png) 


8. From the lab files you downloaded, drag and drop the "transactions_data_xxx.json" file into the "ADD DATA" section.

      ![Demo](./images/datasetbatchdragdrop.png) 

      You will now see a batch with a "Processing" status

      ![Demo](./images/datasetbatch.png)


9. Adobe Experience Platform will perform the XDM mapping and conversion for JSON format to parquet and make this data available on the data lake and the profile store. This process usually takes a few mins. 

    Once your batch status shows "Success", you can preview the data by clicking the "Preview Dataset" button on the top right corner.


    ![Demo](./images/datasetpreview.png)


10. Congratulations !!! You are done with the Dataset exercise.


<br>
<br>
<br>

Return to [Lab Agenda Directory](https://github.com/adobe/AEP-Hands-on-Labs/blob/master/labs/fsi/README.md#lab-agenda)


