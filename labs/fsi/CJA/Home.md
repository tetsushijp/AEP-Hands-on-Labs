
# L729 - Paint a Holistic Picture of the Customer Journey

## Table of Contents

* [Lab Overview](#lab-overview)
* [Lesson 1 - AEP Dataset Creation](#lesson-1---AEP-Data-Creation)
* [Lesson 2 - CJA Setup](#lesson-2---CJA-Setup)
* [Lesson 3 - AEP Data Ingestion](#lesson-3---AEP-Data-Ingestion)
* [Lesson 4 - Introduction to the Cross Channel Data View](#lesson-4---Introduction-to-the-Cross-Channel-Data-View)
* [Lesson 5 - Flow Analysis](#lesson-5---flow-analysis)
* [Lesson 6 - Fallout & Attribution IQ](#lesson-6---fallout-&-attribution-iq)
* [Lesson 7 - Cohort Analysis](#lesson-7---cohort-analysis)
* [Conclusion](#conclusion)
* [Additional Resources](#additional-resources)

## Lab Overview

Today, most businesses collect mountains of data in their quest to better understand their customers so they can create great products and experiences. But the challenge isn’t just collecting more data, it’s integrating, analyzing, understanding, and sharing that data across the business. It requires the right data, from all channels, working together to paint a holistic picture of the customer journey, as well as the right tools to analyze the journey and quickly activate discovered insights. Customer journey analytics provides a toolkit to business intelligence and data science teams that help them stitch and analyze cross-channel data. Its capabilities deliver context and clarity to the complex multichannel customer journey.

This lab will show you how to ingest data into Adobe Experience Platform and use Customer Journey Analytics to answer these long burning questions.

### Key Takeaways

* Understand concepts of CJA.
* Ingest data into Adobe Experience Platform.
* Import ingested datasets into CJA
* Create Connections and data views in CJA
* Analyze data in CJA by creating projects and workspaces

### Prerequisites

* High-level understanding of the Adobe Experience Platform.
* Basic knowledge Adobe Analytics
* Basic knowledge of Analysis Workspace in Adobe Analytics

### Background

Customer Journey Analytics is an Analytics capability that lets you use the power of Analysis Workspace with data from Adobe Experience Platform. It can break down, filter, query, and visualize years' worth of data, and is combined with Platform's ability to hold all kinds of data schemas and types. Using the Experience Data Model (XDM) , data can be uniformly represented and organized, ready for combination and exploration.Experience Query Services in AEP allows you to use SQL-compatible tools and frameworks to query and manipulate all your data.This data can then be imported into CJA for further analysis.

For today’s lab, we will be using 8 datasets from 8 different data sources:

1. Online – Adobe Analytics
2. CRM Data
3. POS aka Offline Purchase Data
4. Email Data
5. Ad Impressions Data
6. Call Center Data
7. Survey Data
8. Marketing Channel Lookup

### Customer Journey Analytics workflow

![cja-steps](assets/cja-steps.gif)

Step 1: The schemas for the data sources  has already been set up in your AEP org. We will begin the lab with step 2 from above steps.

# Lesson 1 - AEP Dataset Creation

## Objective

1. Create datasets in AEP

## Lesson Context

First we must create datasets that we plan to import into CJA for customer journey analysis. In the interest of time we will be creating 3 of them today while the rest of the datasets are already set up and ready for you to use.

### Exercise 1.1

1. Login to your lab machine with the following credentials
    * Username: *L765*
    * Password: *summit2019*

2. Open your web browser and navigate to AEP Home Page

    * [https://platform.adobe.com/](https://platform.adobe.com/)

   You will be directed to the sign in page as shown below 
   ![aep-sign-in-page](assets/l729/aep-sign-in-page.gif)
3. Login with below credentials when prompted.

    - Username: *admin*
    - Password: *admin*

4. You will see the below Home Page.
   ![aep-home-page](assets/l729/aep-home-page.gif)

5. Explore Schemas: Now Click on the "Schemas" tab to explore a few of them.

    ![schema-exploration](assets/l729/schema-exploration.gif)

    - Search for the word "Summit CJA"
    - You will see a list of schemas we have created for various data sources
    - Click on schema for "Summit CJA Lab CRM Demo Data" and view it  
    - Click on cancel to go back to schemas and look for "Summit CJA Lab POS" schema and view its fields
    - Click on cancel to go back to schemas and look for "Summit CJA Tracking Code Lookup" schema and view its fields

### Exercise 1.2

Create datasets for CRM, POS, and Tracking Code lookup schemas.

#### CRM dataset

1. Navigate to the "Dataset" section in AEP.(Click on "Dataset" on the left side). Then Click on "Create Dataset" button on the top right corner.

   ![aep-dataset-section](assets/l729/aep-dataset-section.gif)
2. Click on "Create Dataset from schema" button

      ![aep-dataset-creation1](assets/l729/aep-dataset-creation1.gif)

3. Search for "Summit CJA Lab CRM" in the search box.Then select the schema and hit "Next" as shown below.
   ![aep-dataset-creation2](assets/l729/aep-dataset-creation2.gif)

4. Assign a name to your dataset as shown below. Prepend your *username* to the dataset name and click on "Finish" at the top right had corner.
   ![aep-dataset-creation3](assets/l729/aep-dataset-creation3.gif)

5. You will see the below screen:
   ![aep-dataset-creation4](assets/l729/aep-dataset-creation4.gif)

#### POS  dataset

1. Navigate to the "Dataset" section in AEP.(Click on "Dataset" on the left side). Then Click on "Create Dataset" button on the top right corner.

   ![aep-dataset-section](assets/l729/aep-dataset-section.gif)
2. Click on "Create Dataset from schema" button

      ![aep-dataset-creation1](assets/l729/aep-dataset-creation1.gif)

3. Search for "Summit CJA Lab POS" in the search box.Then select the schema and hit "Next" as shown below.
   ![aep-dataset-creation2-pos](assets/l729/aep-dataset-creation2-pos.gif)

4. Assign a name to your dataset as shown below. Prepend your *username* to the dataset name and click on "Finish" at the top right had corner.
   ![aep-dataset-creation3-pos](assets/l729/aep-dataset-creation3-pos.gif)

5. You will see the below screen:
   ![aep-dataset-creation4-pos](assets/l729/aep-dataset-creation4-pos.gif)

#### Tracking Code lookup dataset

1. Navigate to the "Dataset" section in AEP.(CLick on "Dataset" on the left side). Then Click on "Create Dataset" button on the top right corner.
   ![aep-dataset-section](assets/l729/aep-dataset-section.gif)

2. Click on "Create Dataset from schema" button
      ![aep-dataset-creation1](assets/l729/aep-dataset-creation1.gif)

3. Search for "Summit CJA Lab Tracking Code" in the search box.Then select the schema and hit "Next" as shown below.
   ![aep-dataset-creation2-lookup](assets/l729/aep-dataset-creation2-lookup.gif)

4. Assign a name to your dataset as shown below. Prepend your *username* to the dataset name and click on "Finish" at the top right had corner.
   ![aep-dataset-creation3-lookup](assets/l729/aep-dataset-creation3-lookup.gif)

5. You will see the below screen:
   ![aep-dataset-creation4-lookup](assets/l729/aep-dataset-creation4-lookup.gif)

### Exercise 1.3

Now that you've created datasets, take a few minutes to explore AEP! At a high level checkout the various sections in AEP the Datasets, Schemas, Queries, Segments etc. Try opening some of the schemas for the datasets we will be using in our lab by searching for the keyword "Summit CJA" in schemas section. You can see the schema structure, field names and datatypes!

In our next lesson we will dive into setting up CJA components.

# Lesson 2 - CJA Setup

## Objective

1. Create Data Connection
2. Create Data View

## Lesson Context

In this lesson we will get started with CJA.We will understand how to import the datasets available in AEP into CJA  by creating data connections, data views.

### Exercise 2.1

Getting Started in CJA

1. Open CJA and ensure you are connected to the correct org.
 [http://analytics.adobe.com/](http://analytics.adobe.com/)

   You should see the screen as below
   ![cja-home-screen](assets/l729/cja-home-screen.gif)

### Exercise 2.2

Creating Connection

1. Click on Connections and select Create new connection.
   ![cja-create-connection-1](assets/l729/cja-create-connection-1.gif)

2. Search for “LabInstructor” in the search bar and select all the 5 datasets named as Email,Survey,Ad Impressions,Analytics,Call Center , then select all and click on "Add". Then search for your username and select the 3 datasets you created in Lesson 1 i.e. "your_username Summit CJA lab CRM data","your_username Summit CJA lab POS data","your_username Summit CJA lab Tracking Code data" and click on Add as shown below.
    ![cja-create-connection-2](assets/l729/cja-create-connection-2.gif)
    ![cja-create-connection-22](assets/l729/cja-create-connection-22.gif)

3. For each dataset, click on it and scroll through the right hand section. You will see the Person IDs from the right rail as per the below table. These assigned Person ID's  are the only Identity columns in the datasets and hence were picked by CJA automatically.

    | Dataset | Person ID |
    | ------- | --------- |
    | Survey      | customer_id        |
    | Ad  Impressions      | ad_cookie_id        |
    | Email      | Customer ID        |
    | Call Center      | Customer ID        |
    | Analytics      | Stitched ID        |
    | POS      | Customer ID         |
    | CRM      | Customer ID         |

   ![cja-create-connection-3](assets/l729/create-connection-person-id.gif)
 Note if the datasets have more than one identity we need to go through each dataset and select the appropriate ID as "Person ID"

4. For the "Tracking Code dataset" we need to assign a matching key as this is a lookup dataset. Click on Tracking code dataset and in the right rail select the "tracking_code" field from the drop down as shown below.
   ![cja-create-connection-trackingcode1](assets/l729/cja-create-connection-trackingcode1.gif)
   ![cja-create-connection-trackingcode2](assets/l729/cja-create-connection-trackingcode2.gif)

5. Give an appropriate name to your connection(*username* Summit CJA Connection) and click on Save as shown below.
   ![cja-create-connection-4](assets/l729/cja-create-connection-4.gif)
6. Enable Data Streaming option for your connection to stream in data from platform to CJA as shown below.
   ![cja-create-connection-42](assets/l729/cja-create-connection-42.gif)

### Exercise 2.3

Creating Data view

1. Select the connection that you have created and click on Create Data View
   ![cja-create-dataview-1](assets/l729/cja-create-dataview-1.gif)

2. Give an appropriate name to your data view(*username* Summit CJA data view) and click Add Components
   ![cja-create-dataview-2](assets/l729/cja-create-dataview-2.gif)
Tip: Take a few seconds to note the "Timezone" and "Session Timeout" parameter. These are now configurable via the UI on the fly...Hooray!

3. Drag the required components (dimensions or metrics) to the dataview.
For ex. pick dimensions and metrics like Day, Gender, Week, Month, People, Sessions, Call Reason,Household Income, Emails Delivered, Store Location
    ![cja-create-dataview-3](assets/l729/cja-create-dataview-3.gif)

   - Once all components required for your analysis are added, click Save.
   - You should now be able to see your data view under the tab “Data View”
  

### Exercise 2.4

Now that you've set up CJA connection and dataview, take a few minutes to check out your work! Open up the connections tab to view the connections and its settings and also look at the data views tab to understand how they help in porting over dimensions and metrics from the datasets into CJA.

In our next lesson we will learn how to ingest data into 3 datasets that we created in Lesson1.We will move back to AEP and work there for the next lesson.

# Lesson 3 - AEP Data Ingestion

## Objective

1. Ingest datasets in AEP

## Lesson Context

In this lesson we will learn how to ingest data into AEP datasets. We had created the datasets in Lesson 1, now we will upload data in them.

### Exercise 3.1
Lets jump back to AEP and perform data ingestion for the 3 datasets that you created.

#### CRM dataset ingestion

1. Go back to AEP by opening: "https://wwww.platform.adobe.com" and click on "Datasets" section and search for your "Username" as shown below.
    ![aep-dataset-ingestion-crm1](assets/l729/aep-dataset-ingestion-crm1.gif)

2. Click on your CRM dataset.
   ![crm-data-ingestion](assets/l729/crm-data-ingestion.gif)
    - Scroll to the bottom of the screen
    - Click on "Choose Files" or "Drag and Drop" the CRM file we will ingest into this dataset from the "datafiles" folder.Location : l729\datafiles
  
3. Refresh the page. The files you ingested will be loaded as a batch in the dataset. The Batch status will change from "Loading" to "Success" soon as shown below.
    ![config-cif](assets/l729/crm-data-ingestion-success.gif)
Tip: Click on "Preview" button on top right hand corner of this page to preview the data loaded.

#### POS dataset ingestion

Now lets ingest another dataset. This time we will be ingesting the POS data.

1. Click on "Datasets" section and search for your "Username" as shown below.
    ![aep-dataset-ingestion-pos1](assets/l729/aep-dataset-ingestion-pos1.gif)
2. Click on your POS dataset.
   ![pos-data-ingestion](assets/l729/pos-data-ingestion.gif)
    - Scroll to the bottom of the screen
    - Click on "Choose Files" or "Drag and Drop" the POS file we will ingest into this dataset from the "datafiles" folder.Location : l729\datafiles
  
3. Refresh the page. The file you ingested will be loaded as a batch in the dataset. The Batch status will change from "Loading" to "Success" soon as shown below.
    ![pos-data-ingestion-success](assets/l729/pos-data-ingestion-success.gif)
Tip: Click on "Preview" button on top right hand corner of this page to preview the data loaded.

#### Tracking Code Lookup dataset ingestion

Now lets ingest another dataset. This time we will be ingesting a lookup file. Some of the data sources that we are using example : Analytics, Email, Ad Impressions have "tracking code" column which can be mapped to meaningful dimension "Marketing Channels" We will be setting up a lookup dataset that will help us with that mapping.

1. Click on workflows on the top left corner in AEP. Then click on the "Map CSV to XDM schema" thumbnail.
    ![lookup-data-ingestion1](assets/l729/lookup-data-ingestion1.gif)

2. Then click on Launch as shown below.
    ![lookup-data-ingestion2](assets/l729/lookup-data-ingestion2.gif)

3. It will launch a workflow which we can use to bring in CSV data into AEP. Follow below steps:
    ![lookup-data-ingestion3](assets/l729/lookup-data-ingestion3.gif)
    - In the "Add Data" step Drag & Drop trackingcode.csv file or Choose it from the l729\datafiles\folder  as shown above.
    - Once its added you can see the preview of few records on the screen. Click on "Next" and wait for few seconds.
    - It will take you to the "Destination" tab. Select the option "Use Existing dataset" and search your dataset "Your_username Summit CJA lab Tracking Code data"
    -  Click on Next, then it will take you to the "Mapping" tab. Here you can see the  that we have mapped source fields to the fields we have defined in the schema.
    -  Click on Next and it will take you to the last tab which is "Ingest". There is an Ingest button in the "Ingest Details" section, click that and wait for some time. It will will create batch and start the ingestion.
    -  Within a minute you should see the below screen with "Ingestion successful" message. Click on finish as highlighted below.
       ![lookup-data-ingestion4](assets/l729/lookup-data-ingestion4.gif)

4. You will then be navigated to the dataset page where you can see the data that you have loaded just now.
       ![lookup-data-ingestion5](assets/l729/lookup-data-ingestion5.gif)
Tip: Click on "Preview" button on top right hand corner of this page to preview the data loaded.

### Exercise 3.4
Now that you've ingested data into AEP datasets, take a few minutes to check out your work! Search for "LabInstructor Summit CJA" under datasets page and look at all the datasets we will be using. You can preview them and understand what fields they are populating.
   ![dataset-exploration](assets/l729/dataset-exploration.gif)

In our next lesson we will learn how to create visualizations in CJA to perform multi-channel analysis and see the customer journey come to life!

# Lesson 4 - Introduction to the Cross-Channel Data View

## L4: Objective

1. Introduce the interface for Workspace on AEP.
2. Identify differences from web-only datasets.
3. Analyze summary KPIs across datasets.

## L4: Context

Now that you have ingested data and stitched your datasets, it is time to explore the data within Workspace. The interface is similar to Workspace in Adobe Analytics, but your analysis can extend across the entire customer journey. We will begin to identify the populations of each dataset and their overlaps in this lesson.

## L4: Exercises

### Exercise 4.1

Explore the interface of Customer Journey Analytics. It brings the power of Analysis Workspace to cross-channel datasets in Adobe Experience Platform.

1. Click _Projects_ in the top rail.

   ![projects-link](assets/projects-link.gif)

2. We will create a new project. Click on _New Project_. An empty project will open up.

   ![new-project-blank](assets/new-project-blank.gif)

3. Observe the layout.

   * On the left rail, components, visualizations, and panels are available.

      ![left-rail](assets/left-rail.gif)

   * On the right, data views and calendar settings are available (highlighted in green).

      ![data-view-calendar](assets/data-view-calendar.png)

   * A freeform table will be available on default in the center canvas. If you wish to use other visualizations, click on the '+' and you will be presented with options for different visualizations.

      ![center-canvas](assets/center-canvas.gif)

   * Just under the top rail for Customer Journey Analytics, there is a set of menus specific to the project. Many of these options provide an associated keyboard shortcut, such as CTRL/Command-Z for Undo.

      ![menu-undo](assets/menu-undo.gif)

   * The main method of interaction in Workspace is drag-and-drop. Select an object, click and hold the mouse button, and drag it into a valid location. While an object is being dragged, valid drop zones are highlighted. Try dragging any item under the _Dimensions_ heading in the left rail into an available drop zone in the main panel.

      ![drag-and-drop-dimensions](assets/drag-and-drop-dimension.gif)

4. Observe the following differences from Workspace in Adobe Analytics.

   1. _Data Views_ replace the report suite selector of Workspace.

      ![data-views-dropdown](assets/data-views-dropdown.gif)

      Note: Since CJA does not have the feature to show backfill data as of current release, we have already created a connection and data view for you to work on the lab. For all exercises, please select the data view **L729 Data View**.

   2. The left rail now shows information on the namespace and data source in parentheses.

      ![namespace-parentheses](assets/namespace-parentheses.png)

      Note: The labels of components can be changed in the Data View, but the labels for namespace and data source are pulled from the schema and cannot be altered elsewhere.

   3. Some language has changed to better fit the cross-channel, customer-based data in Customer Journey Analytics.

      * _Filters_ represent subsections of data, akin to _segments_ in Workspace.

         ![filters-left-menu](assets/filters-left-menu.png)

      * The container hierarchy for filters is now _Event, Session, Person, instead of _Hit, Visit, Visitor_.

         ![filters-menu](assets/filters-menu.png)

      * Matching this hierarchy, basic traffic KPIs in Customer Journey Analytics are _Events_, _Sessions_, and _People_.

         ![event-session-people](assets/event-session-people.png)

#### E4.1: Value Realization

Customer Journey Analytics provides the flexible power of Analysis Workspace on top of stitched, cross-channel data from Adobe Experience Platform! It is a flexible, robust, intuitive way to explore cross-channel data.

### Exercise 4.2

Create a basic table of the data sources and KPIs. While this is a simple view in Customer Journey Analytics, it is a powerful first look at the stitched datasets.

1. Select the data view _L729 Data View_. This is similar to the view created earlier.

   ![l729-data-view](assets/l729-data-view.gif)

2. Change the calendar time frame to March 1-31, 2020.

   ![calendar-march](assets/calendar-march.gif)

   Further examples and screenshots will reflect the March 1-31 window. The full range of valid dates in this demo data is March 1 - April 30.

3. Create a freeform table with the dimension _Data Source - Time Series_.

   1. If your canvas looks like this, click _Freeform Table_ to open a new freeform table visualization.

      ![start-analyzing-freeform](assets/start-analyzing-freeform.png)

   2. In the left rail, search for _data source_.

      ![search-data-source](assets/search-data-source.gif)

   3. Click and drag the dimension Data Source - Time Series into the main drop zone of the freeform table. (This is the zone containing the text Drop A Dimension Here).

      ![data-source-drag-table](assets/data-source-drag-table.gif)

   A default metric of _Events_ will be applied. Your result should look like this:

   ![data-source-freeform](assets/data-source-freeform.png)

   If your table differs significantly, verify that the selections for Data View, calendar, and the specified dimension match the instructions above.

4. Add Key Performance Indicators (KPIs) to the freeform table.

   1. Clear any search keywords or filters from the left rail.

      ![clear-left-rail](assets/clear-left-rail.gif)

   2. Search for the _Sessions_ metric.

      ![search-sessions](assets/search-sessions.png)

   3. Click and drag Sessions into the freeform table, to the right of _Events_.

      ![sessions-table](assets/sessions-table.gif)

      Note: If you make a mistake, Undo is quickly accessible using Command-Z.

   4. Repeat this process for the metrics of _people_ and _Orders_.

   5. Your result should look like this:

      ![kpi-table](assets/kpi-table.png)

   Note: There may be additional data sources in the Connection that do not appear in this freeform table. This depends on the dataset _type_. The dimension used in this example contains elements listing data sources of the type _Time Series_. Lookup tables and record data are different classes and they do not populate this dimension.

#### E4.2: Value Realization

With the power of Customer Journey Analytics, it only took moments to create a visualization showing the distribution of KPIs across multiple datasets!

### Exercise 4.3

Create a Venn visualization showing the people who share events in multiple data sources. This exercise will use prebuilt filters to identify people of each data source.

Note: Unless otherwise specified in an exercise, you are welcome to open a new panel for each exercise or to use a single panel.

1. On the left edge of the left rail, click on the middle icon to access Visualizations.

   ![visualizations-icon](assets/visualizations-icon.png)

2. Drag the Venn visualization into your panel.

   ![drag-venn](assets/drag-venn.gif)

   With a Venn visualization, we can compare up to 3 filters over a single metric. Here, we want to visualize the overlap in _People_ across a few data sources. To configure this visualization, we will use the _People_ metric and filters for People belonging to various data sources.

3. On the left edge of the left rail, click on the bottom icon to access Components. Ensure any search keywords or filters are cleared from the search box.

4. Drag the following filters into the drop zone _Add up to 3 Filters_:

   * Person: POS Data
   * Person: Call Center Data
   * Person: Ad Impression Data

   ![find-drag-filter](assets/find-drag-filter.gif)

   Note: By clicking the information icon available next to the filter title, you can preview the filter definitions being used.

   ![filter-left-rail-preview](assets/filter-preview.gif)

5. Drag the People metric into the drop zone _Add One Metric_.

   Your Venn configuration should look like this:

   ![venn-people-overlap](assets/venn-people-overlap.png)

6. Click _Build_ to produce the Venn result.

7. Examine the results. Move the mouse over various regions and hover to see the number of people associated with each dataset or a combination of datasets.

   The filters used here were defined at the highest container level (person). Overlaps in the Venn visualization represent _people_ with an interaction in each data source. If a lower container level were used, such as _session_ or _event_, the overlaps would represent active sessions that spanned multiple datasets or individual events that included each dataset (not possible here). In the next exercise, we will create another Venn visualization, using session-level filters.

   Note: You can also create new filters from a Venn visualization by right-clicking on an area in the visualization. Once the filter definition overlay appears, check that the levels (event, session, or person) fit your need.

   ![filter-from-venn](assets/filter-from-venn.gif)

   Note: Return to the blank Venn configuration screen by right-clicking on the visualization header and clicking _Start Over_.

   ![venn-start-over](assets/venn-start-over.png)

#### E4.3: Value Realization

This immediately shows the distribution of _people_ across the selected data sources! Ideally, this overlap is maximized to provide the most robust cross-channel analysis.

### Exercise 4.4

Create a Venn visualization showing those orders that occurred in sessions spanning multiple data sources. This differs from the previous exercise, because here we look at _sessions_ that contained multiple sources, rather than _people_ (whose multiple sources may have been engaged at separate times).

Refer to the prior exercise for granular directions.

1. Load a new Venn visualization into your project.

2. Search the Components of the left rail to find the following filters. Drag them into the filters drop zone for the Venn visualization.

   * Session: Analytics Data
   * Session: POS Data

3. Drag the Orders metric into the metric drop zone for the Venn visualization.

   Your Venn configuration should look like this:

   ![venn-session-overlap](assets/venn-session-overlap.png)

4. Click _Build_ to produce the Venn result.

5. Examine the results.

   The numeric values here represent conversions, while the Venn circles display sessions in the data source. The intersection means that an active session has data occurring in each overlapping source.

   Consider what a session engaged in both Analytics and POS might represent.Shoppers in a brick-and-mortar store often engage with the web or app using their mobile device, prior to checkout. They look for coupons, research products, locate an item, etc. This theory would be explored by analyzing behaviors further for the sessions matching this overlap filter.

   Note: If person-level filters were used here, the interpretation of the overlap would change. It would represent orders completed by people who had engaged Analytics and POS, but not necessarily at the same time.

   Feel free to edit the Venn visualization with other filters and metrics. Note, however, that the demo data is imperfect and may display some characteristics uncommon in the real world.

#### E4.4: Value Realization

Analysis of same-session interactions provides a close-up look of engagement. Customer Journey Analytics opens the view from a traditional, digital-only scope, into a holistic view of all identified engagements within an active session.

### Exercise 4.5

Explore the populations with data available in 1 data source, 2 data sources, and so on. This provides a source-agnostic view of the breadth of stitched data. The prior exercises compared specific sources for overlap.

For granular instructions on typical Workspace interactions, please see prior exercises.

1. Add a new freeform table from the left rail visualizations menu.

   ![new-freeform-from-left-rail](assets/new-freeform-from-left-rail.gif)

2. Drag in the following filters as rows in the table:

   * Person: 1 Data Source
   * Person: 2 Data Sources
   * Person: 3 Data Sources
   * Person: 4 Data Sources
   * Person: 5 Data Sources
   * Person: 6 Data Sources

3. Replace the _Events_ metric with the _People_ metric by dragging _People_ on top of the existing _Events_ metric.

   ![people-replace-events](assets/people-replace-events.gif)

   Your freeform table should look like this:

   ![freeform-number-of-data-sources](assets/freeform-number-of-data-sources.png)

4. Drag in a donut visualization from the left rail visualizations menu.

   ![drag-donut](assets/drag-donut.gif)

5. Check the data source for the donut visualization, ensuring it matches your new freeform table color and title.

   ![donut-data-source-check](assets/donut-data-source-check.gif)

   Note: It is easier to find the right freeform data source table when the tables have been renamed. To rename a freeform table, simply double-click on the title and change it to the desired label.

   Your visualization should look similar to this:

   ![donut-overlap-sample](assets/donut-overlap-sample.png)

6. Consider the results in the visualization. It is immediately apparent how many people in the dataset exist across data sources or channels.

#### E4.5: Value Realization

At a glance, you can grasp the extent of stitching that has occurred for people across the data sources.

#### E4.5: Extra

Try creating a similar visualization, using session-based filters and the Sessions metric. These are shared already with the following names:

* Session: 1 Data Source
* Session: 2 Data Sources
* Session: 3 Data Sources

The result of this visualization demonstrates active sessions spanning multiple data sources. As expected, this is far less common than the existence of a Person in multiple data sources (which is not limited to a window bound by a timeout period).

![donut-overlap-session](assets/donut-overlap-session.png)

## L4: Backup Resources

If needed, you may access a prebuilt project containing each exercise of the lesson. Use this as a backup resource in case you encounter difficulty following the exercises.

Click _Project > Open_ to access the list of projects. Open the **Backup Lesson** project desired.

# Lesson 5 - Flow Analysis

## L5: Objective

1. Learn how to build Flow visualizations.
2. Explore and understand flows across the customer journey.
3. Learn advanced capabilities with the Flow visualization.

## L5: Context

The Flow visualization is a great first step in exploration of the customer journey. It is visually intuitive and enables quick exploration of sequences across sessions, people, and all dimensions. Technically, it builds complex and accurate sequential filters for you, so that your focus is exploration and insights.

## L5: Exercises

### Exercise 5.1 Introduction to Flow Visualizations

Learn how to build and interpret the Flow visualization through simple examples. We will use the Day dimension to keep things simple.

#### Basic Setup

1. Collapse any prior panel(s) and add a new panel for this exercise.

   ![collapse-old-panels-create-new](assets/collapse-old-panels-create-new.gif)

2. Change the calendar selection to March 1-3, 2020. We will use these 3 days for the test case.

3. Create a freeform table with the following components:

   * Rows: Day dimension
   * Columns: Events, Sessions, People

   ![day-by-kpis](assets/day-by-kpis.png)

4. Add a Flow visualization from the left rail, Visualizations menu.

   ![drag-flow](assets/drag-flow.gif)

   Flow can focus on the start of a sequence (entry), end of a sequence (exit), or any node in between. For this example, we look at the _Entry_ type.

5. Drag the Day dimension into the _Entry (Dimensions Only)_ drop zone.

   ![drag-day-entry](assets/drag-day-entry.png)

   Note: You can also drag a dimension from any nearby table in your project. For example, in the adjacent freeform table you have open, you can drag the Day dimension by Control-click on the dimension heading. This will not impact the source table.

   ![drag-existing-dimension](assets/drag-existing-dimension.gif)

6. Confirm that your panel content looks like this. Placement and size may vary.

   ![sample-flow-entry-panel](assets/sample-flow-entry-panel.png)

   Note: If you need or prefer to use a prebuilt project, these are available for each lesson. Click _Project > Open_ to access the list of projects. Open the **Backup Lesson** project desired and expand the related panel for that exercise.

7. Lastly, right-click over any node in the right column and select _Expand entire column_.

   ![expand-entire-column](assets/expand-entire-column.gif)

8. Confirm that your visualization matches the image below.

   ![entry-visitor-flow](assets/entry-visitor-flow.png)

   ![day-by-kpis](assets/day-by-kpis.png)

#### Flow at Person Level

As currently configured, with default settings, this visualization displays the flow of people across the dimension we chose: Day. The left column displays the population, the center column displays the first Day for each person, and the right column shows the next Day for each person. Flow visualizations always display sequences in chronological order, left-to-right, as the timestamp proceeds.

Sample assessments:

   1. The data view for the calendar range contains 42854 people.
   2. Some people interacted first on March 1, others on March 2 or 3.
   3. 32433 people have their first _event_ on March 1. This matches the table.
   4. Of those people:
      1. 24860 interacted next on March 2
      2. 8754 engaged next on March 3 (no events recorded on March 2)
      3. 3145 _exited_ (no subsequent events recorded on March 2 or 3). Hover to see this value in the visualization.

   So, this shows the first Day of each person and the next Day, if they had additional sessions or events. You can click on any node to expand or collapse a branch further.

   Note: The Day dimension was selected to simplify this quick example. For flows across other dimensions, especially those which are not always present like the timestamp (Day), the interpretation may require additional considerations.

#### Flow at Session Level

Flow can also represent sequences within _sessions_. We will copy the prior example, but switch it to show session sequences.

1. Duplicate the Flow visualization of the prior exercise, by right-clicking the header and then _Duplicate Visualization_.

   ![duplicate-visualization](assets/duplicate-visualization.gif)

2. Click the Settings (gear) icon in the upper-right of the new copy. If you don't see it at first, mouse over the visualization and it will slide into view.

   ![settings-flow](assets/settings-flow.png)

3. Change the Flow Container from _Person_ to _Session_. (If the Settings overlay remains displayed, click anywhere outside of it to hide it).

4. Compare the Session flow to the prior version that displayed Person flows.

   ![compare-session-person-flow](assets/compare-session-person-flow.png)

   As currently configured, this version shows the flow of sessions across the dimension we chose: Day. The left node _* Entry (Day)_ shows the population of sessions, then the Day each session started, and the next Day reached (if any) in the same session.

   Sample assessments (Session level):

   1. There are 235928 sessions in our current view.
   2. About 1/3 of the sessions started on each of March 1, 2, and 3.
   3. 99.9% of the sessions starting on Day = Mar 1, 2020 do not continue to another Day.
   4. The remaining 0.1% of those, a total of 96 sessions, began on March 1 and continued to March 2 (crossed midnight).

   ![01-pct-continue](assets/01-pct-continue.png)

#### Flow with Repeat Instances

Above, the visualizations showed a sequence only if the value of Day _changed_. That can be toggled, too, with the setting: _Include Repeat Instances_. It is disabled by default. With repeat instances included, Flow will display sequences at a very granular level.

1. Duplicate the sessions flow visualization.

2. In the Settings overlay, check the box labeled _Include Repeat Instances_.

   ![include-repeat-instances](assets/include-repeat-instances.png)

3. Compare this view with the earlier Session-level flow, without repeat instances.

   ![flow-session-repeats](assets/flow-session-repeats.png)

   Now, every node in this visualization represents a single event with a value in the Day dimension. Since Day is set on all events, each node represents a single event. Try expanding the nodes on the right side; some paths will continue quite far.

   As before, with the Session level, each Entry or Exit represents the beginning or end of a Session. For those sessions including a long set of events on a single day, we will see that day repeated in the visualization. A 5-event-long session beginning on Day = Mar 1, 2020 will have 4 additional nodes in its expanded path, each labeled Mar 1, 2020. Repeats like this were simply suppressed with this option disabled, earlier.

#### E5.1: Value Realization

Flow is interactive and exploratory. The options provide flexibility to study session journeys and person journeys. It can emphasize changes across activity or display repeated nodes, when required for an analysis.

### Exercise 5.2 Use Cases with Flow

Study flows across multi-channel data. Start with a sequence of interest and then create a filter, trend the behavior, breakdown that flow by other components.

1. Collapse any prior panel(s) and add a new panel for this exercise. Choose any calendar range within the demo data of March - April, 2020.

2. Add a Flow visualization to the panel.

3. Drag _Data Source - Time Series_ from the left rail into the center drop zone of the visualization.

   ![data-source-to-center-flow](assets/data-source-to-center-flow.png)

4. Expand some nodes on the right of the visualization, to see how people navigate across channels of your business. (Flow defaults to the _people_ level).

   ![flow-across-channels](assets/flow-across-channels.png)

   Assume that we want to analyze the behaviors of people who flow from POS to Call Center, to identify opportunities to alleviate the need for high-expense calls.

5. Right-click on any node for _POS Data_ and select _Focus on this Node_. It will replace _Analytics Data_ as the central or focus node.

   ![focus-pos-data-flow](assets/focus-pos-data-flow.png)

6. Expand the Call Center Data node on the right.

   ![pos-call](assets/pos-call.png)

   Let's explore the next external marketing channel this group touches.

7. Drag the Marketing Channel dimension over the far right column. Release the dimension when a drop zone labeled Replace appears.

   ![channel-over-source](assets/channel-over-source.gif)

   Note: You can analyze flows across any dimension! Here, we are exploring a customer path from brick-and-mortar to the call center and then the next digital marketing touchpoint!

   Many people exit after the POS to Call Center flow; these people did not engage with the next node (Marketing Channel). Let's explore the reasons for these calls that arose after a POS event.

8. Right-click on _Call Center Data_ and select _Breakdown_ > _Dimension_ > _Call Reason_.

   ![call-breakdown-call-reason](assets/call-breakdown-call-reason.gif)

   The resultant table displays the Call Reason for only those calls that occurred immediately following a POS event!

   ![reason-breakdown-result](assets/reason-breakdown-result.png)

   Let's add the call durations for this flow.

9. Drag in the metric Call Duration Average. Drop it next to _Events_ but still below the _Flow: Data Source..._ filter.

   ![call-duration-average](assets/call-duration-average.gif)

   Note: If the metric is placed outside of the filter, it will represent the average call duration for the entire data view and calendar range. It can be useful to place it twice, once within the filter and once outside it, in order to compare global averages to the sequence averages.

   ![call-reasons-vs-global](assets/call-reasons-vs-global.png)

   Let's check how this sequence has occurred over time. Is it a continued trend or a one-time anomaly?

10. Right-click on the Call Center node in the flow visualization and select _Trend_.

   ![trend-flow](assets/trend-flow.gif)

   Let's save this particular path as a reusable filter, for further analysis elsewhere in Workspace.

11. Right-click on the Call Center node again and select _Create filter for this path_.

12. In the Filter Builder overlay, provide a title and click Save.

   ![flow-filter](assets/flow-filter.png)

   Note: The Flow visualization builds filters like this to enable the features we explored. Filters provide the capability to slice data in innumerable ways. Some of the most powerful filters for analyzing customer journey take advantage of the _Then_ operator, as you see here. These are called sequential filters.

   Note: This is a plain language explanation of this filter, from top to bottom, for those who are interested: _Include all persons that have an event in the Data Source dimension and that are persons with a POS Data event whose next Data Source event is in Call Center Data._ Experienced users can build or tweak filters like this to solve almost any use case. It helps to start with the visual Flow visualization, generating a base filter, first.

#### E5.2 Value Realization

We studied a customer journey across online and offline touchpoints, based on a specific sequence of interest. Then, we were able to analyze the activity that occurred on the completion of that particular sequence! We checked the trend of this path over time. We saved the filter created by Flow for further analysis. The Flow visualization enabled us to easily and flexibly explore customer paths.

## L5: Backup Resources

If needed, you may access a prebuilt project containing each exercise of the lesson. Use this as a backup resource in case you encounter difficulty following the exercises.

Click _Project > Open_ to access the list of projects. Open the **Backup Lesson** project desired.

# Lesson 6 - Fallout & Attribution IQ

## L6: Objective

1. Learn how to analyze non-consecutive flows.
2. Learn how to measure cross-channel fallout.
3. Learn how to measure the attribution of events to prior dimension activity.

## L6: Context

All organizations have a defined funnel of some type, to understand and evaluate performance toward a customer lifecycle. The Fallout visualization is used for scenarios like this, in which we have a set of _known_ checkpoints to evaluate in a specified order. (Flow excels more for exploratory analysis of _unknown_ checkpoints in consecutive order). Checkpoints in the Fallout visualization are flexible: metrics, dimensions, filters, or any group of these can define a checkpoint. As with Flow, it is easy to create a filter, trend checkpoints over time, and breakdown the next action after a checkpoint.

Attribution IQ provides a similar method of assessing the relationship between prior actions and later events. This feature enables dynamic attribution modeling in Workspace, for cross-channel marketing channel analysis as well as analysis of any other dimension.

## L6: Exercises

### Exercise 6.1 Fallout Basics

Because CJA has stitched data across our customer touchpoints, Fallout checkpoints can span the entire customer journey. For example, a journey begun with a display advertising impression can be tied to orders placed in store, attributing credit for the conversion back to its first marketing touchpoints.

1. Collapse any prior panel(s) and add a new panel for this exercise.

2. Add a Fallout visualization.

   ![fallout-visualization](assets/fallout-visualization.gif)

   Note: The top level of Fallout defaults to showing the entire population. In the Settings options (gear icon), you can toggle this on or off.

3. Add the metric _Ad Impressions_ to the drop zone labeled _Add Touchpoint_.

   ![add-ad-impressions](assets/add-ad-impressions.gif)

4. Add the metric _Ad Clicks_ into the same drop zone, which will place it in a new checkpoint below the previous checkpoint.

   ![add-ad-clicks](assets/add-ad-clicks.gif)

5. Add the metric _Orders_ into the drop zone, in a third checkpoint.

   Confirm that your visualization looks like this.

   ![confirm-basic-fallout](assets/confirm-basic-fallout.png)

   If you need to remove or edit a checkpoint, hover from the graph to the left over a checkpoint. The details will be revealed. There, you can remove a component or a checkpoint, entirely.

   ![demo-fallout-removal](assets/demo-fallout-removal.gif)

   This is a very basic funnel, showing a path from ad impressions to clicks to ultimate conversion, using simple metrics only. Fallout affords greater flexibility than is demonstrated so far. Also, note that Fallout is used to measure People or Sessions following some sequence; its results are always a count of those metrics, not a count of other metrics such as _number of Orders_.

   Let's compare our fallout view across some filters.

6. In the left rail, Components menu, expand the dimension CRM Gender.

   ![expand-gender](assets/expand-gender.gif)

7. Drag the _F_ element into the top drop zone containing the default _All People_ filter.

   ![drag-f-fallout](assets/drag-f-fallout.gif)

8. Drag the _M_ element into the same drop zone. (This must be done separately, or else a single filter for CRM Gender = M or F would have been applied).

   Confirm that your visualization looks like this.
   ![fallout-m-f-ads](assets/fallout-m-f-ads.png)

#### E6.1: Value Realization

You can see at a glance how people pass through the simple funnel here, even across multiple filters. This is a very limited usage of Fallout's capabilities. Next, we'll explore something more interesting.

### Exercise 6.2 Advanced Fallout Uses

Fallout is useful for measuring custom checkpoints and sequences. Let's define some checkpoints for analysis of a particular initiative. Say that call center representatives are directed to decrease the number of repeat callers. As one tactic for this initiative, callers with passive call types are receiving an additional, quick script to promote self-service resources online.

1. Collapse any prior panel(s) and add a new panel for this exercise.

2. Add a new Fallout visualization. Click Settings (gear icon) and uncheck the feature _Show "All People" as the first touchpoint_.

   ![show-all-first](assets/show-all-first.png)

   We are not concerned with the full population of customers but only those who began in our sequence of passive or neutral call types. Our first checkpoint will identify this group.

3. Expand the dimension _Call Reason_ in the left rail and add these two elements to the first touchpoint in the visualization:

   * Forgot Password/Login
   * Website Help

   ![call-reasons-touchpoint](assets/call-reasons-touchpoint.png)

   Note: The default names of touchpoints in Fallout can be renamed. Hover over the name and click to open the editor.

   ![name-touchpoint](assets/name-touchpoint.gif)

   The next checkpoint will measure signals of self-service. In this demo dataset, this will be two metrics from the Web dataset.

4. Add these metrics into a next checkpoint:

   * Web Product Views
   * Web Internal Searches

   ![web-signals-touchpoint](assets/web-signals-touchpoint.png)

   The last checkpoint will count orders. However, it needs to exclude those orders that were executed on the Call Center channel.

5. Add the metric _Orders_ into a final checkpoint.

6. Expand the dimension _Data Source: Time Series_ in the left rail and add these two elements to the final checkpoint containing the _Orders_ metric:

   * Analytics Data
   * POS Data

   ![combined-final-touchpoint](assets/combined-final-touchpoint.png)

   The combination of the metric and elements counts only those people with subsequent orders that occurred either in store or on the web. Now, the Fallout visualization conveys the story we wanted to analyze! The checkpoints must be met in order during the calendar range but they need not be consecutive.

   Two further actions can be helpful. Let's trend this view and save it as a filter. This will allow for monitoring and easy analysis in other projects. Both actions are accessible via right-click on the Fallout checkpoint of interest.

7. Right-click the final checkpoint and select _Create filter from touchpoint_. Provide a title for the filter and then save it for reuse!

   ![create-filter-from-checkpoint](assets/create-filter-from-checkpoint.gif)

   Note: The filter length depends on the number of components in the Fallout visualization. Try minimizing the filter containers to assess the whole filter more easily.

   ![collapse-filter-containers](assets/collapse-filter-containers.gif)

   Note: Because of this filter capability, both Fallout and Flow are very helpful as sequential segment-generators. Use the visual interface of the visualization to arrange the checkpoints of interest. Then create a filter and make changes or replicate it as needed.

   Note: A filter saved from a visualization in this way will not have any connection to the original Fallout or Flow visualization. Subsequent changes made to the filter definition or to the visualization will be independent from each other.

8. Right-click the final checkpoint and select _Trend all touchpoints (%)_.

   ![trend-all-touchpoints](assets/trend-all-touchpoints.png)

9. In the resultant visualization, right-click on the legend and select _Edit Label_ to provide a friendlier name than the default.

   ![edit-label](assets/edit-label.gif)

#### E6.2: Value Realization

Fallout enables broader analysis of strategies and tactics, where a simple flow or event is not sufficient to evaluate success. You were able to analyze a customer path across three channels, with granular specificity, providing a trended view of data that addresses the business need.

### Exercise 6.3 Attribution IQ

Attribution settings are the other way to connect prior behaviors to future events. While mostly considered in the context of external marketing, the notion of attribution applies to any dimensions. This feature set in Workspace is known as Attribution IQ. It enables an analyst to connect digital interactions with offline conversions across the customer journey.

1. Collapse any prior panel(s) and add a new panel for this exercise.

2. Add a freeform table and drag the _Marketing Channel_ dimension into the rows of the table.

3. Add the _Orders_ metric 4 times into the columns. Remove the default _Events_ metric.

   ![channel-by-orders](assets/channel-by-orders.png)

   Note: You can quickly copy components by dragging them to a new destination while holding the CTRL key.

   ![control-drag](assets/control-drag.gif)

   As always, the interpretation of the metrics and Marketing Channel dimension depends on the underlying data and any custom configurations in the Data View. Without any special attribution configuration, a metric in CJA like _Orders_ represents the default _Same Touch_ attribution model: an order is credited to a channel only when the channel and order occur on the same record. In this demo dataset, most Analytics records specify a marketing channel, which may vary across other data sources.

4. Right-click on the second metric and select _Modify Attribution Model_. Set it as follows:

   * Model: First Touch
   * Lookback Window: Person (Reporting Window)

   ![modify-to-first](assets/modify-to-first.gif)

5. Modify the attribution model of the third metric to:

   * Model: Participation
   * Lookback Window: Person (Reporting Window)

6. Modify the attribution model of the last metric to:

   * Model: U Shaped
   * Lookback Window: Person (Reporting Window)

   Confirm that your visualization looks like this.
   ![4-orders-adjusted](assets/4-orders-adjusted.png)

   Note: Attribution settings can even be changed at breakdowns in a table. Try breaking down a channel by another dimension and then adjusting the metric attribution at the breakdown row. This can be valuable when high-level analysis (e.g. marketing mix) needs to use a standardized attribution model, but more granular analysis (e.g. tactics of a specific channel) warrants a different model. Use Undo (CTRL-Z) if you need to return your table to the earlier format.

   ![breakdown-model-change](assets/breakdown-model-change.gif)

7. Add a Bar visualization to your panel. It will automatically link to this table, because no other tables exist in the panel.

   ![bar-4-orders](assets/bar-4-orders.png)

8. Review the results and observe how credit from digital touchpoints can be credited in each way to subsequent, even offline conversions.

9. Choose one of the customized order metrics in your table. Right-click on the metric heading and select _Create metric from selection_ then _Open in Calculated Metric Builder_. Provide an intuitive title and save.

   ![calc-metric-order](assets/calc-metric-order.gif)

   Now, this version of the metric can be shared and added quickly to any project in Customer Journey Analytics directly from the left rail.

#### E6.3: Value Realization

The choice of attribution models plays a critical role in analysis. Even if it has not been emphasized, every dimension and metric assessed in any system involves a choice of an attribution scheme. Provisioned Attribution IQ capabilities are available for any dimension. In this exercise, you evaluated the holistic influence of digital marketing channels on downstream orders. The same methods can apply to evaluation of store performance or video impact on downstream cancellations or attrition. You can quickly evaluate and choose the best model for your scenario, whatever it is.

## L6: Backup Resources

If needed, you may access a prebuilt project containing each exercise of the lesson. Use this as a backup resource in case you encounter difficulty following the exercises.

Click _Project > Open_ to access the list of projects. Open the **Backup Lesson** project desired.

# Lesson 7 - Cohort Analysis

## L7: Objective

1. Introduce the cohort analysis capabilities of Workspace.
2. Explore advanced capabilities and use cases for Cohort Tables.

## L7: Context

The exercises in this lesson will explore the features of Cohort Tables in Workspace. This feature helps you analyze customers with shared characteristics and explore their behaviors over time. Like Flow and Fallout, this capability speeds up analysis by providing an intuitive, visual template focused on a common business question in customer journey analysis.

## L7: Exercises

### Exercise 7.1 Cohort Table Basics

Create a Cohort Table with a simple use case: after a customer's first session in the calendar range, how many days pass until the customer's second session?

1. Collapse any prior panel(s) and add a new panel for this exercise.

2. Set the calendar range to March 1-7.

3. Add a new Cohort Table visualization to the panel.

   At a minimum, a Cohort Table requires a metric for the Inclusion Criteria and a metric for the Return Criteria. We will start here, but quickly revise our approach due to the unrealistic trends in our demo dataset.

   ![cohort-basic-fields](assets/cohort-basic-fields.png)

4. Add the Sessions metric into the Inclusion Criteria drop zone and add the Orders metric into the Return Criteria drop zone.

   ![cohort-sessions-orders](assets/cohort-sessions-orders.png)

5. Adjust the Granularity setting to _Day_ granularity and then click Build.

   ![cohort-granularity-day](assets/cohort-granularity-day.png)

   Confirm that your visualization looks like this.

   ![cohort-basics-result](assets/cohort-basics-result.png)

6. Review the results and familiarize yourself with its layout.

   Each row shows the behaviors of a particular _cohort_ of people. The row beginning _Mar 1_ represents a group of people who met the _Inclusion Criteria_ on March 1st. There are 32433 people who had at least one _Session_ on March 1st, shown in the _Included_ column.

   ![included-mar1](assets/included-mar1.png)

   Proceeding to the right, the table reveals the subset of those people who _also_ met the _Return Criteria_ at a later time. The column _+1 Days_ represents that subset that had at least one _Order_ one day afterward (i.e. on March 2nd).

   ![1-day-mar1](assets/1-day-mar1.png)

   More sample assessments:

   1. Of the 32433 people who had at least one session on March 1, 287 people returned on March 3 to place at least one order.
   2. There is not necessarily any relationship between the 280 people of the _Mar 1_ cohort who ordered one day later and the 287 people of the same cohort who ordered two days later. Some people may be counted in both columns, those who ordered both on March 2 and on March 3.
   3. The _Mar 2_ cohort represents the 32215 people who had at least one session on March 2.
   4. 303 people of the _Mar 2_ cohort also placed at least one order on March 3rd.
   5. There is no value for the _Mar 2_ cohort in the _+6 Days_ column because the calendar range ends at March 7 (+5 days from March 2).
   6. People may overlap in multiple cohorts; someone who has a session on March 1, 2, and 3 will be included in each of the cohorts of _Mar 1_, _Mar 2_, and _Mar 3_. Whether that person is counted in subsequent _columns_ depends on when, and if, that person placed orders later.

   Lastly, note the top row labeled _Average Retention_. It summarizes the typical behavior of the cohorts by averaging the results. The average return percentages are especially helpful. For example, this provides a takeaway such as: _On average, about 0.9% of people order one day after a session._

   ![average-retention](assets/average-retention.png)

#### E7.1 Value Realization

With a few clicks, you modeled the timing and frequency of orders placed after a session. This was evaluated over seven days, to provide a few samples for validation of the trends. A task like this would otherwise take significant preparation time to create filters to represent each of the scenarios, whereas Workspace completed this task for you.

### Exercise 7.2 Cohorts with Filters

In the prior exercise, you may have noticed that the results were unusual. This is a reflection of the demo data. There are few real world datasets where 0.8% of the included people order every day for six straight days. In this example, we explore the addition of filters in our inclusion and return metrics. The filters have been chosen to display a more typical cohort trend than in the previous exercise.

1. In the panel and Cohort Table that you created from the prior exercise, click the pencil icon that appears after the Inclusion and Return summary. This will allow you to edit the existing Cohort Table configuration.

   ![cohort-pencil](assets/cohort-pencil.png)

2. Replace the return criteria metric with _Sessions_.

3. Add the following filters to the inclusion and return drop zones labeled _Drop a Filter_ here:

   * Inclusion: _Session: First Session of Calendar Range_
   * Return: _Session: Second Session of Calendar Range_

   ![cohort-filters](assets/cohort-filters.png)

   (At the time of writing, there was a bug preventing filters from being dragged into these drop zones. If this issue persists, a workaround is available: click the + icon that appears when hovering over the drop zone; then create a temporary filter and click _Save_. After this, a replacement filter can be dragged on top of the temporary filter).

4. Click _Build_ and observe the results.

   ![cohort-filters-result](assets/cohort-filters-result.png)

   Note: The displayed trend is much more common in cohort tables; when the return metric is a conversion of some sort, the percentage of returning people typically decreases over time.

   The filters have augmented the definitions of inclusion and return. Now, the _Included_ column counts people if they:

   * Had a session on the listed cohort date
   * _And_ that session matches the associated filter

   In this case, the session matches if it is the first session of that customer, within the range of March 1-7. If the person engaged in February, that is irrelevant in this result; only the first visit in this seven-day window matters. Someone whose first session of March 1-7 occurred on March 1st will be counted in the _Mar 1_ cohort. When that customer returned next for their second session of March 1-7, they would be counted once more in the appropriate column.

   Note: Sometimes, people can be listed across multiple columns of a cohort table. This is not always the case; it depends on the return criteria. In the table just created, a customer that had both  first and second sessions on the inclusion date will be counted once in the _Included_ column, only.

5. Add a Bar visualization to the panel.

   Because no other table exists in this panel, the visualization will link to the cohort table you have built. The visualization of the entire table is a bit complex, but the Average Retention row is perfect for display in a graph.

6. Select the cells in the _Average Retention_ row, beginning at _+1 Days_ and continuing to the final _+6 Days_ column.

   ![average-retention-graph](assets/average-retention-graph.png)

7. Configure the chart to show percentages and hide the legend.

   ![bar-percentages](assets/bar-percentages.png)

8. In the Data Source Settings menu, lock the selected positions.

   ![lock-positions](assets/lock-positions.gif)

   Now, even if the selected cells in the cohort table change, the graph will remain focused on the Average Retention cells.

   Confirm that your result looks like this.

   ![cohort-average-retention](assets/cohort-average-retention.png)

   This visual display conveys the return trends of people over time. The horizontal legend may be ignored, as it displays the labels of the current calendar range. Since the displayed data reflects the _Average Retention_, each data point represents _+1 Days return_, _+2 Days return_, etc. If it is helpful context, you can include the 100% _Included_ cell in the selection, too (you will have to unlock the chart, update the selection, and then lock it again).

   ![cohort-average-retention-with-100](assets/cohort-average-retention-with-100.png)

#### E7.2 Value Realization

   With a few more adjustments, you augmented the cohort table to display results of a customized inclusion and return metric using filters. We visualized the curve representing this return trend over time, which highlights the inflection points or points of diminishing returns. In other real scenarios, analysts can identify the optimal window for sending followup emails to maximize open rates, or they may establish the duration of time at which attrition liklihood exceeds a certain percentage. Business processes can be optimized with the insights from this visualization.

### Exercise 7.3 Advanced Features with Cohort Tables

The Cohort Table visualization can help in more customer journey analyses. It can display an inverse view of returning people (churn) and it can show a forward and backward view from the inclusion point (latency). You can adjust the calculations to show retention from the prior column, instead of retention from the _Included_ column (rolling calculation). Finally, you can also analyze return behaviors spread across a dimension other than time! This exercise will explore these capabilities.

#### Churn

1. Duplicate the Cohort Table you created earlier (right-click the header and select _Duplicate Visualization_).

2. In the duplicate table, click the pencil icon to return to the configuration view.

3. In the _Type_ section, change the radio button from _Retention_ to _Churn_. Then click _Build_.

   ![type-churn](assets/type-churn.png)

4. Compare the two cohort visualizations; they are like inverses of one another.

   ![retention-vs-churn](assets/retention-vs-churn.png)

   Choose the best view for your analysis and storytelling. The people counted in the columns of the _Churn_ variant are those who did _not_ return or meet the return criteria at that time. Whether emphasizing those who did or those who did not return, the data calculated is essentially the same.

#### Rolling Calculation

1. Duplicate the original _Retention_ Cohort Table and click the pencil icon to return to the configuration view.

2. In the Settings section, check the box labeled _Rolling Calculation_. Then click _Build_.

   ![rolling-calculation-cohort](assets/rolling-calculation-cohort.png)

3. Compare this with the original cohort table.

   The columns after _+1 Days_ represent something completely different, now. Rather than measure the returners from the original _Included column_, each column now measures the returners as a sub-population of the _prior column_. _Included_ and _+1 Days_ results are unchanged, but beginning with _+2 Days_, the result is the number of people that met the return criteria +2 days later _and_ were also matched in the _+1 Days_ column (the prior column to the _+2 Days_ column).

   Because this example requires a return to be the second session, specifically, no people will meet that condition on multiple days or more than once. Those people who had a first session on March 1 and a second session on March 2 are logically unable to also have a second session on a later date.

   More sample assessments:

   1. 7359 people had a session, their first session within March 1-7, on the date of March 1st. These are labeled as the cohort _Mar 1_.
   2. Of those 7359 people, 1994 also had a session, their second session of March 1-7, on the date of March 2nd.
   3. Of those 1994 people, none of them had their second session of March 1-7 on March 3-7 - because their second session occurred on March 2nd, of course.

   Note: This _Rolling Calculation_ setting supports a different kind of analysis. The Cohort Table default shows how a cohort of people behaves over subsequent dates. With the rolling calculation model, the visualization tells a story of people who continued to _repeat_ a behavior over time. For example, this view helps to identify people who engage with your brand every day or week, your most loyal customers. A filter can be created from these results for further analysis or activation on this group.

#### Latency

1. Add a new cohort table visualization, with the following settings:

   * Inclusion Metric: Orders
   * Return Metric: Sessions
   * Granularity: Day
   * Settings: Advanced, Latency Table

   ![latency-setup](assets/latency-setup.png)

2. Click _Build_ and observe the results.

   ![latency-result](assets/latency-result.png)

   The _Latency_ configuration provides the most similar insights to the default cohort table. The _Included_ column and the + Days columns are identical to those of a Cohort Table created without the _Latency_ setting checked. People meeting the inclusion criteria appear in the _Included_ group, and those who meet the return criteria on a subsequent day are listed in the column for that day, also.

   The addition here is a view prior to the cohort inclusion date. Just as the + Days columns show people who met the return condition later, the - Days columns describe the people who triggered the _return_ condition prior to the Inclusion date. This aids in analysis of customer journeys after _and before_ a point of interest. For example, this supports analysis of engagement before and after an order occurs or analysis of marketing materials accessed before and after a sales call.

   More sample assessments:

   1. The _Mar 2_ cohort comprises 373 people that ordered on March 2.
   2. _+1 Days_ later, on March 3, 279 of the 373 people had at least one session.
   3. 280 of the 373 people in this cohort also had at least one session _-1 Days_ prior, on March 1.
   4. None of these 373 people had a session on February 29 (because of the current calendar range).

#### Custom Dimension Cohorts

This final permutation of cohort analysis enables the study of cohorts defined by a dimension other than _time_. Say that you need to evaluate the shared behaviors of people acquired by a particular marketing channel. You want to understand the amount of time before each cohort places an order. Without cohort analysis and the custom dimension feature, this would require a slew of custom filters to be manually defined and compiled.

1. Add a new cohort table visualization, with the following settings:

   * Inclusion Metric: Sessions
   * Return Metric: Orders
   * Granularity: Day
   * Settings: Advanced, Custom Dimension Cohort: _Marketing Channel_

   ![custom-cohort-setup](assets/custom-cohort-setup.png)

2. Build the visualization. Observe and interpret the results.

   ![custom-cohort-result](assets/custom-cohort-result.png)

   This is a very different result than the default Cohort Table. Without the custom dimension, the visualization expressed the trends of people who shared a characteristic (the Include metric) on some date. Now, the shared characteristic is an event _in some marketing channel_. Analyzing these cohorts over time highlights the differences (or similarities) related to a channel's impact.

   Note: The cell shading is intended to guide interpretation. If the shading trend of multiple rows aligns, it suggests the elements of the custom dimension may not significantly affect the tendency to meet the return conditions. If the shading differs strongly over various rows, it may reflect varying influence of certain elements on customers' tendency to meet the return conditions. An exception exists, however, where a random shading pattern can represent weak correlation between the dimension and the return criteria.

   More sample assessments:

   1. 26049 people had a session on March 1 including the _Marketing Channel_ element of _Display Ads_.
   2. Of those 26049 people, 127 placed an order on March 2nd.
   3. 6449 people had a session containing _Other Referrals_ on March 1.
   4. If a customer had both the channels of _Display Ads_ and _Other Referrals_ in session(s) on March 1, they would be counted in both cohort rows.

   Note: As noted earlier, the potential for a single person to be counted in multiple rows or columns depends on the configuration of the cohort visualization. Be careful to set up the visualization to match your business goal and to interpret the results accordingly.

#### E7.3: Value Realization

The basic and advanced features of cohort analysis enabled you to compare behaviors over time, based on complex criteria, with a variety of flexible options. This saved significant time in planning, creating, arranging, and combining custom filters. You moved quickly through different views and identified distinguishing characteristics of the journeys customers take _over time_!

## E7: Backup Resources

If needed, you may access a prebuilt project containing each exercise of the lesson. Use this as a backup resource in case you encounter difficulty following the exercises.

Click _Project > Open_ to access the list of projects. Open the **Backup Lesson** project desired.

# Conclusion

By performing these exercises, you were able to stitch online and offline customer data using the power of Adobe Experience Platform and Customer Journey Analytics. Workspace enabled you to explore this stitched data and paint a holistic picture of the customer journey through multiple channels.

# Additional Resources

[AEP-general-documentation](https://www.adobe.io/apis/experienceplatform/home/services.html)

[CJA-documentation](https://docs.adobe.com/content/help/en/analytics-platform/using/cja-landing.htmll)

[Analytics-connector-data-in-aep](https://www.adobe.io/apis/experienceplatform/home/data-ingestion/data-ingestion-services.html#!api-specification/markdown/narrative/technical_overview/acp_connectors_overview/analytics_data_connector.md)

[Analytics-connector-fields-mapping](https://www.adobe.io/apis/experienceplatform/home/data-ingestion/data-ingestion-services.html#!api-specification/markdown/narrative/technical_overview/acp_connectors_overview/analytics_mapping_fields.md)
