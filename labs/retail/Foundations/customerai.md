Lab 1.1 - Creating a Customer AI Instance
==========
<table style="border-collapse: collapse; border: none;" class="tab" cellspacing="0" cellpadding="0">

<tr style="border: none;">

<div align="left">
<td width="600" style="border: none;">
<table>
<tbody valign="top">
      <tr width="500">
            <td valign="top"><h3>Objective</h3></td>
            <td valign="top"><br>Creating a Customer AI instance that calculates propensity to buy (Conversion)
            </td>
     </tr>
     <tr width="500">
           <td valign="top"><h3>Prerequisites</h3></td>
           <td valign="top">
                            <li>AEP instance with Customer AI and/or Attribution AI provisioned
                            <br>
                            <li>Conceptual knowledge of your data, conversion/churn event definitions
                            <br>
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
            <td valign="middle" height="70">Customer AI</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>version</b></td>
            <td valign="middle" height="70">1.0.1</td>
      </tr>
      <tr>
            <td valign="middle" height="70"><b>date</b></td>
            <td valign="middle" height="70">2021-05-05</td>
      </tr>
</tbody>
</table>
</td>
</div>

</tr>
</table>

Instructions:
-----------------

1. Go to [https://platform.adobe.com/home](https://platform.adobe.com/home)

2. Please ensure that you are in your alloted sandbox for this exercise

3. In the left-hand menu, navigate to **Services** and click **Open** within the **Customer AI** section

      ![Demo](./images/1.png)
      
4. Click **Create instance**. 



    ![Demo](./images/2.png)
      
      
      This will take you to the Setup stage of the Customer AI workflow.
      
4. Enter a name for this instance. Let's call it "Propensity to Buy" followed by your sandbox number. eg: **Propensity to buy 001**
5. Set Propensity type to **Conversion**
6. Set Dataset to **FSI Demo Data midValues**. This is a prepopulated Adobe Analytics dataset.
7. Leave the eligible population as is and include the entire population.
8. Click **Next** on the top right of your screen.
      

      <img src= "./images/3.png" width="1800" height="400">
      
 This will take you to the Define Goal stage of the Customer AI workflow.
 
9. Enter the term **purchaseid** inside the *Enter field name* section and select **commerce.order.purchaseid** -> **exists** as your conversion event.
10. Leave Timeframe as is to 30 days     
      
      
      ![Demo](./images/4.png)
      
      This will take you to the Advanced  stage of the Customer AI workflow.
      
11. Set scoring to run **Weekly on Mondays at 12:00 am Eastern**.
12. Leave Exclusion Population as is
      
      
      ![Demo](./images/5.png) 
 
 
13. Click **Finish** on the top right of your screen to save the instance.
      
      
      
