**Exercise 1.1 - Set up the lab environment
Before you proceed with the assignment**

Start the PostgreSQL Server
Download the lab setup bash file from https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0231EN-SkillsNetwork/labs/Final%20Assignment/postgres-setup.sh
Run the bash file

`wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0231EN-SkillsNetwork/labs/Final%20Assignment/postgres-setup.sh`

**Task 1.1 - Find the settings in PostgreSQL
What is the maximum number of connections allowed for the postgres server on theia lab?**

Hint: /home/project/postgres/data/postgresql.conf is the configuration file for PostgreSQL.

![Task 1 1](https://user-images.githubusercontent.com/121275064/230522840-48dcd80f-6745-43d5-8f17-aa94d1349ebc.jpg)

**Exercise 1.2 - User Management
Perform these user management tasks on your PostgreSQL server. Perform the tasks 1.2 to 1.5 using the PostgreSQL CLI. DO NOT USE THE PGADMIN GUI.**

**Task 1.2 - Create a User
Create a user named backup_operator.**

![Task 1 2](https://user-images.githubusercontent.com/121275064/230522972-f408b688-3dad-4c4d-be86-ba8208365631.jpg)


**Task 1.3 - Create a Role
Create a role named backup.**

![Task 1 3](https://user-images.githubusercontent.com/121275064/230523008-9d9c9632-38f9-47c0-8f0b-bc76d76a6d9a.jpg)

**Task 1.4 - Grant privileges to the role
Grant the following privileges to the backup role.**

CONNECT ON tolldata DATABASE.
SELECT ON ALL TABLES IN SCHEMA toll.

![Task 1 4](https://user-images.githubusercontent.com/121275064/230523020-baa23509-7159-4e90-94df-8237e3f54e59.jpg)

**Task 1.5 - Grant role to an user
Grant the role backup to backup_operator**

![Task 1 5](https://user-images.githubusercontent.com/121275064/230523099-22b1b507-c8bb-4aac-b072-fd35e725f6dd.jpg)

**Exercise 1.3 - Backup
Task 1.6 - Backup a database on PostgreSQL server
Backup the database tolldata using PGADMIN GUI.**

Backup the database tolldata into a file named tolldatabackup.tar, select the backup format as Tar

![Task 1 6](https://user-images.githubusercontent.com/121275064/230523212-895d7ea0-3e10-4454-bffd-cc6debf398cb.jpg)

**Exercise 2.2 - Recovery
Task 2.1 - Restore MySQL server using a previous backup
Download the backup file https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0231EN-SkillsNetwork/labs/Final%20Assignment/billingdata.sql.**

Restore this file onto MySQL server.

List the tables in the billing database.

![Task 2 1](https://user-images.githubusercontent.com/121275064/230523354-f79f15ba-79a2-4852-b52b-6c3eabd60249.jpg)

**Task 2.2 - Find the table data size
Find the data size of the table billdata.**

![Task 2 2](https://user-images.githubusercontent.com/121275064/230523398-ccf59e08-ba2e-448d-8d18-a0872fd89123.jpg)

**Exercise 2.3 - Indexing
Task 2.3 - Baseline query performance
Write a query to select all rows with a billedamount > 19999 in table billdata.**

![Task 2 3](https://user-images.githubusercontent.com/121275064/230523421-46a9c311-a843-49d5-9d14-809b1898100c.jpg)

**Task 2.4 - Create an index
Your customer wants to improve the execution time of the query you wrote in Task 2.3.**

Create an appropriate index to make it run faster.

![Task 2 4](https://user-images.githubusercontent.com/121275064/230523449-5969152f-8fd0-48ea-a1bc-cc9b40790465.jpg)

**Task 2.5 - Document the improvement in query performance
Find out if the index has any impact on query performance.**

Re-run the baseline query of Task 2.3 after creating the index.

![Task 2 4](https://user-images.githubusercontent.com/121275064/230523506-e2eedb44-3f49-45fa-b00e-b2f9464e21fd.jpg)

**Exercise 2.4 - Storage Engines
Task 2.6 - Find supported storage engines
Run a command to find out if your MySQL server supports the MyISAM storage engine.**

![Task 2 6](https://user-images.githubusercontent.com/121275064/230523541-391ad0de-9022-4966-84b8-d3cf80fdf3c5.jpg)

**Task 2.7 - Find the storage engine of a table
Find the storage engine of the table billdata.**

![Task 2 7](https://user-images.githubusercontent.com/121275064/230523552-e36a4357-b4d6-41ed-b433-9728a818b9a9.jpg)

**Exercise 3.1 - Prepare the lab environment
Before you proceed with the assignment, you need to have access to a cloud instance of IBM DB2 database. If you do not have access, use the instructions in this lab Hands-on Lab: Sign up for IBM Cloud and Create a Db2 service instance to create a instance for yourself.**

Download the file billing.csv

**Exercise 3.2 - Restore data
Task 3.1 - Restore the table billing
Use the billing.csv you have downloaded earlier, restore the csv file into a table named billing.**

Note: You will see that each column has data type and column width auto generated based on the content. Edit column attributes by clicking on the pencil icon next to the respective attributes to change the width of country column to varchar of 30 and month column to varchar of 7.

![Task 3 1](https://user-images.githubusercontent.com/121275064/230523931-f64857ef-58bc-4282-b82b-539d0d97bf3d.jpg)

**Exercise 3.3 - Create a view
Task 3.2 - Create a view named basicbilldetailswith the columns customerid, month, billedamount**

![Task 3 2](https://user-images.githubusercontent.com/121275064/230523965-f89eabaa-615b-441a-9a76-44570a95b123.jpg)







