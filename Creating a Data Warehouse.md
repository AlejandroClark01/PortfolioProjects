**Scenario
You are a data engineer hired by a solid waste management company. The company collects and recycles solid waste across major cities in the country of Brazil. The company operates hundreds of trucks of different types to collect and transport solid waste. The company would like to create a data warehouse so that it can create reports like**

total waste collected per year per city
total waste collected per month per city
total waste collected per quarter per city
total waste collected per year per trucktype
total waste collected per trucktype per city
total waste collected per trucktype per station per city
You will use your data warehousing skills to design and implement a data warehouse for the company.

**Objectives
In this assignment you will:**

Design a Data Warehouse
Load data into Data Warehouse
Write aggregation queries
Create MQTs
Create a Dashboard
Note - Screenshots
Throughout this lab you will be prompted to take screenshots and save them on your own device. These screenshots will need to be uploaded for peer review in the next section of the course. You can use various free screengrabbing tools or your operating system's shortcut keys (Alt + PrintScreen in Windows, Commannd + Shift + 5 on Mac, Shift + Ctrl + Show windows on Chromebook) to capture the required screenshots. The screenshots can be either jpg or png.

About the dataset
The dataset you would be using in this assignment is not a real life dataset. It was programmatically created for this assignment purpose.

Prerequisites
You need access to a cloud instance of IBM DB2 to proceed with this assignment.

If you do not have an instance of IBM DB2 on cloud, follow the instructions in this lab to create one.

You need access to Cognos Analytics.

This lab will guide to get your access to Cognos Analytics, and also get you started with how to use it to analyze the data.

**Exercise 1 - Design a Data Warehouse
The solid waste management company has provied you the sample data they wish to collect.**



You will start your project by designing a Star Schema warehouse by identifying the columns for the various dimension and fact tables in the schema.

**Task 1 - Design the dimension table MyDimDate
Write down the fields in the MyDimDate table in any text editor one field per line. The company is looking at a granularity of day. Which means they would like to have the ability to generate the report on yearly, monthly, daily, and weekday basis.**

Here is a partial list of fields to serve as an example:

dateid
month
monthname
...
...

![T1](https://user-images.githubusercontent.com/121275064/231015581-187fdf87-75d0-45ac-b7b4-34037013cb9e.JPG)

**Task 2 - Design the dimension table MyDimWaste
Write down the fields in the MyDimWaste table in any text editor one field per line.**

![T2](https://user-images.githubusercontent.com/121275064/231015605-ae6cec53-7d41-49d4-9696-3bbe88d6a537.JPG)

**Task 3 - Design the dimension table MyDimZone
Write down the fields in the MyDimZone table in any text editor one field per line.**

![T3](https://user-images.githubusercontent.com/121275064/231015615-09ae2b84-1b7b-4d1d-a4d1-682d2ae76833.JPG)

**Task 4 - Design the fact table MyFactTrips
Write down the fields in the MyFactTrips table in any text editor one field per line.**

![T4](https://user-images.githubusercontent.com/121275064/231015625-e00a554a-a803-4d8b-ae6b-a1df30b80680.JPG)

**Exercise 2 - Create schema for Data Warehouse on DB2
In this exercise you will create the tables, you have designed in the previous exercise.**

**Task 5 - Create the dimension table MyDimDate
Create the MyDimDate table.**

![T5](https://user-images.githubusercontent.com/121275064/231015644-e9ca9f87-3517-4599-b3a5-f19a7a88ac87.JPG)

**Task 6 - Create the dimension table MyDimWaste
Create the MyDimWaste table.**

![T6](https://user-images.githubusercontent.com/121275064/231015775-7b223fb8-582a-483c-88a8-f344ce996fa8.JPG)

**Task 7 - Create the dimension table MyDimZone
Create the MyDimZone table.**

![T7](https://user-images.githubusercontent.com/121275064/231015797-e62bf5bf-28c1-48a9-8021-bcceb228c4ba.JPG)

**Task 8 - Create the fact table MyFactTrips
Create the MyFactTrips table.**

![T8](https://user-images.githubusercontent.com/121275064/231015804-cda2ca2b-85f3-46ed-8f9a-f650bd238821.JPG)

**Exercise 3 - Load data into the Data Warehouse
In this exercise you will load the data into the tables.**

After the initial schema design, you were told that due to opertional issues, data could not be collected in the format initially planned.

You will load the data provided by the company in csv format.

**Task 9 - Load data into the dimension table DimDate**
Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimDate.csv

Load this data into DimDate table.

![T9](https://user-images.githubusercontent.com/121275064/231015857-7f56d08e-0344-46bc-8394-ee55c8c2a9d6.JPG)

**Task 10 - Load data into the dimension table DimTruck**
Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimTruck.csv

Load this data into DimTruck table.

![T10](https://user-images.githubusercontent.com/121275064/231015865-2057e0ef-a70e-411b-bc36-36d6f4da79cc.JPG)

**Task 11 - Load data into the dimension table DimStation**
Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DimStation.csv

![T11](https://user-images.githubusercontent.com/121275064/231015878-5b64c595-4cc3-4ba3-81f5-22982b209c8c.JPG)


**Task 12 - Load data into the fact table FactTrips**
Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/FactTrips.csv

Load this data into FactTrips table.

![T12](https://user-images.githubusercontent.com/121275064/231015903-cfcb377a-ba3d-43d5-a94b-4caf349665bb.JPG)

**Exercise 4 - Write aggregation queries and create MQTs**
In this exercise you will query the data you have loaded in the previous exercise.

**Task 13 - Create a grouping sets query**
Create a grouping sets query using the columns stationid, trucktype, total waste collected.

![T13](https://user-images.githubusercontent.com/121275064/231016002-105aa33b-3e67-4306-87dd-e935aa869404.JPG)

**Task 14 - Create a rollup query**
Create a rollup query using the columns year, city, stationid, and total waste collected.

![T14](https://user-images.githubusercontent.com/121275064/231016006-c6d3b943-b4f3-48f4-b132-1f8d3d91a100.JPG)

**Task 15 - Create a cube query**
Create a cube query using the columns year, city, stationid, and average waste collected.

![T15](https://user-images.githubusercontent.com/121275064/231016015-e8a064bd-48f5-4d3f-9867-e53caffb181d.JPG)

**Task 16 - Create an MQT**
Create an MQT named max_waste_stats using the columns city, stationid, trucktype, and max waste collected.

![T16](https://user-images.githubusercontent.com/121275064/231016022-4ef002f6-19ea-421b-a252-c51ba5c1acd5.JPG)

**Exercise 5 - Create a dashboard using Cognos Analytics**
Download the data from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0260EN-SkillsNetwork/labs/Final%20Assignment/DataForCognos.csv

Use the DataForCognos.csv file to generate the following charts.

**Task 17 - Create a pie chart in the dashboard**
Create a pie chart that shows the waste collected by truck type.

![T17](https://user-images.githubusercontent.com/121275064/231016126-be823c34-812c-42af-a7de-312e4eadcba5.JPG)

Task 18 - Create a bar chart in the dashboard
Create a bar chart that shows the waste collected station wise.

![T18](https://user-images.githubusercontent.com/121275064/231016131-2efc95e6-d1c0-47c5-8035-1c9b6c16bfe7.JPG)

Task 19 - Create a line chart in the dashboard
Create a line chart that shows the waste collected by month wise.

![T19](https://user-images.githubusercontent.com/121275064/231016136-8ab50cb1-fb8f-47e6-877a-aae9c5bd5127.JPG)

Task 20 - Create a pie chart in the dashboard
Create a pie chart that shows the waste collected by city.

Take a screenshot of the pie chart.

![T20](https://user-images.githubusercontent.com/121275064/231016146-3d423aad-4103-4e78-bb83-f2474d46097c.JPG)
