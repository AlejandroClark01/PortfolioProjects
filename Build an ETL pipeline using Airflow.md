**Exercise 1 - Prepare the lab environment
Start Apache Airflow.**

Open a terminal and create a directory structure for staging area as follows:
/home/project/airflow/dags/finalassignment/staging.

sudo mkdir -p /home/project/airflow/dags/finalassignment/staging

Download the dataset from the source to the destination mentioned below using wget command.
Note: While downloading the file in the terminal use the sudo command before the command used to download the file.

Source : https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Final%20Assignment/tolldata.tgz

Destination : /home/project/airflow/dags/finalassignment

Change to the staging directory.

cd /home/project/airflow/dags/finalassignment/staging

**Exercise 2 - Create a DAG
Task 1.1 - Define DAG arguments
Define the DAG arguments as per the following details:**

Parameter	Value\
owner:	< You may use any dummy name>\
start_date:	today\
email:	< You may use any dummy email>\
email_on_failure:	True\
email_on_retry:	True\
retries:	1\
retry_delay:	5 minutes\

![Task 1 1](https://user-images.githubusercontent.com/121275064/230518704-8ca29252-fe60-4746-938d-0f489a508b8d.JPG)

**Task 1.2 - Define the DAG
Create a DAG as per the following details.**

Parameter	Value\
DAG id:	ETL_toll_data\
Schedule:	Daily once\
default_args:	as you have defined in the previous step\
description:	Apache Airflow Final Assignment

![Task 1 2](https://user-images.githubusercontent.com/121275064/230518870-8f0b8ae2-0549-42d0-91f2-def40574a0b4.JPG)

**Task 1.3 - Create a task to unzip data
Create a task named unzip_data.**

Use the downloaded data from the url given in the first part of this assignment in exercise 1 and uncompress it into the destination directory.

![Task 1 3](https://user-images.githubusercontent.com/121275064/230519451-7a54d0a7-b228-4a20-ac28-81e96dfae120.JPG)

**Task 1.4 - Create a task to extract data from csv file
Create a task named extract_data_from_csv.**

This task should extract the fields Rowid, Timestamp, Anonymized Vehicle number, and Vehicle type from the vehicle-data.csv file and save them into a file named csv_data.csv.

![Task 1 4](https://user-images.githubusercontent.com/121275064/230519530-efedab0f-1987-4a61-9f4f-14b453e2351f.JPG)

**Task 1.5 - Create a task to extract data from tsv file
Create a task named extract_data_from_tsv.**

This task should extract the fields Number of axles, Tollplaza id, and Tollplaza code from the tollplaza-data.tsv file and save it into a file named tsv_data.csv.

![Task 1 5](https://user-images.githubusercontent.com/121275064/230519613-bf8d48ab-2f48-4cc0-a9f6-06a67465a70c.JPG)

**Task 1.6 - Create a task to extract data from fixed width file
Create a task named extract_data_from_fixed_width.**

This task should extract the fields Type of Payment code, and Vehicle Code from the fixed width file payment-data.txt and save it into a file named fixed_width_data.csv.

![Task 1 6](https://user-images.githubusercontent.com/121275064/230519639-d851b355-bfb8-4a21-8731-057cfebe922e.JPG)

**Task 1.7 - Create a task to consolidate data extracted from previous tasks
Create a task named consolidate_data.**

This task should create a single csv file named extracted_data.csv by combining data from the following files:

csv_data.csv
tsv_data.csv
fixed_width_data.csv
The final csv file should use the fields in the order given below:

Rowid, Timestamp, Anonymized Vehicle number, Vehicle type, Number of axles, Tollplaza id, Tollplaza code, Type of Payment code, and Vehicle Code

![Task 1 7](https://user-images.githubusercontent.com/121275064/230519670-f725dea0-8460-4f58-9bbd-e15575d56ba1.JPG)

**Task 1.8 - Transform and load the data
Create a task named transform_data.**

This task should transform the vehicle_type field in extracted_data.csv into capital letters and save it into a file named transformed_data.csv in the staging directory.

![Task 1 8](https://user-images.githubusercontent.com/121275064/230519709-60297a74-f2bc-49f6-a7fc-afa827c020a7.JPG)

**Task 1.9 - Define the task pipeline
Define the task pipeline as per the details given below:**

First task	unzip_data\
Second task	extract_data_from_csv\
Third task	extract_data_from_tsv\
Fourth task	extract_data_from_fixed_width\
Fifth task	consolidate_data\
Sixth task	transform_data

**Exercise 3 - Getting the DAG operational.
Save the DAG you defined into a file named ETL_toll_data.py.**

Task 1.10 - Submit the DAG

![Task 1 10](https://user-images.githubusercontent.com/121275064/230519845-4085fcc9-fd05-4773-ba49-14c50d3ca646.JPG)

**Task 1.11 - Unpause the DAG**

![Task 1 11](https://user-images.githubusercontent.com/121275064/230519878-fd557f4e-0b7e-4fd5-9afd-46aafe52414d.JPG)











