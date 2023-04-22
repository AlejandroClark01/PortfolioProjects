**Final Assignment - Querying data in NoSQL
databases**

Estimated time needed: 90 minutes.
It is highly recommened that you finish the Setup and Practice Assignment Lab before you proceed with this
Assignment.
About This SN Labs Cloud IDE
This Skills Network Labs Cloud IDE provides a hands-on environment for course and project related labs. It
utilizes Theia, an open-source IDE (Integrated Development Environment) platform, that can be run on desktop
or on the cloud. To complete this lab, we will be using the Cloud IDE based on Theia and Cassandra and
Mongodb running in a Docker container. You will also need an instance of Cloudant running in IBM Cloud.
Important Notice about this lab environment
Please be aware that sessions for this lab environment are not persisted. Every time you connect to this lab, a
new environment is created for you. Any data you may have saved in the earlier session would get lost. Plan to
complete these labs in a single session, to avoid losing your data.
Scenario

You are a data engineer at a data analytics consulting company. Your company prides itself in being able to
efficiently handle data in any format on any database on any platform. Analysts in your office need to work with
data on different databases, and data in different formats. While they are good at analyzing data, they count on
you to be able to move data from external sources into various databases, move data from one type of database
to another, and be able to run basic queries on various databases.
Objectives

**In this assignment you will:
replicate a Cloudant database.
create indexes on a Cloudant database.
query data in a Cloudant database.
import data into a MongoDB database.
query data in a MongoDB database.
export data from MongoDB.
import data into a Cassandra database.
query data in a Cassandra database.**

Note - Screenshots
Throughout this lab you will be prompted to take screenshots and save them on your own device. These
screenshots will be needed to be uploaded for peer review in the next section of the course. You can use various
free screengrabbing tools to do this or use your operating system’s shortcut keys to do this (for example
Alt+PrintScreen in Windows).
**Exercise 1 - Check the lab environment**
Before you proceed with the assignment :
Check if you have the ‘couchimport’ tool installed on the lab, otherwise install it.
Check if you have the ‘mongoimport’ and ‘mongoexport’ tools installed on the lab, otherwise install them.
Check if the environment variable CLOUDANTURL is set, otherwise set it.
Right-click on the link and “open in a new tab” to obtain the content of the json file and copy the entire content:
movies.json
Now, go to the lab environment by clicking on the Launch/Open Tool button, and create a new file named
movie.json under the project directory and paste the entire content copied earlier into the newly created json file.
Export the json into your Cloudant Database
Go to your Cloudant Service created on IBM Cloud and then click on Launch Dashboard to launch the cloudant
databases. Then, click on New database on the top-right corner and create a Non-patitioned database named
movies.
Run the given command in the terminal to export the data of the “movie.json” file into your Cloudant database
“movies”:
curl -XPOST $CLOUDANTURL/movies/_bulk_docs -Hcontent-type:application/json -d @movie.json
**Exercise 2 - Working with a Cloudant database
Task 1 - Replicate a local database into your Cloudant instance**
Using the replication page in the Cloudant dashboard, replicate the below source database using one time
replication,
Source
Type : Local Database
Name: movies
Authentication : IAM Authentication
Add your Cloudant API key below.(You can find it in the service credentials tab)
Target
Type: New local database
Authentication : IAM Authentication
Add your Cloudant API key below.(You can find it in the service credentials tab)
Options
Replication type: One time
Click on Start Replication

![T1](https://user-images.githubusercontent.com/121275064/233767284-799dd4ad-6efe-4f58-b5fe-8b2530e49afd.JPG)


**Task 2 - Create an index for the “Director” key, on the ‘movies’ database using the HTTP API**

![T2](https://user-images.githubusercontent.com/121275064/233767565-4d8e476a-d4f2-4507-8ba6-68c16a3967e0.JPG)

**Task 3 - Write a query to find all movies directed by ‘Richard Gage’ using the HTTPAPI
Take a screenshot of the command you used and the output.**

![T3](https://user-images.githubusercontent.com/121275064/233767419-b4e88a88-a7e0-4057-b5d8-09af58f6b2ef.JPG)

**Task 4 - Create an index for the “title” key, on the ‘movies’ database using the HTTPAPI
Take a screenshot of the command you used and the output.**

![T4](https://user-images.githubusercontent.com/121275064/233767445-17632af4-bf90-4bec-ad4a-2bcbcec6071c.JPG)

**Task 5 - Write a query to list only the “year” and “Director” keys for the ‘Top Dog’ movies
using the HTTPAPI
Take a screenshot of the command you used and the output.**

![T5](https://user-images.githubusercontent.com/121275064/233767615-c007c3d9-48fd-479b-9ffe-681cfa346383.JPG)

**Task 6 - Export the data from the ‘movies’ database into a file named ‘movies.json’
Take a screenshot of the command you used and the output.**

![T6](https://user-images.githubusercontent.com/121275064/233767571-597db770-0490-4160-bfd8-c1107f18991f.JPG)
Exercise 3 - Working with a MongoDB database

**Task 7 - Import ‘movies.json’ into mongodb server into a database named ‘entertainment’
and a collection named ‘movies’
Take a screenshot of the command you used and the output.**

![T7](https://user-images.githubusercontent.com/121275064/233767574-170ac83f-9379-4a77-9d77-62fecddb799f.JPG)

Note: Please use the movies.json (new file that gets created in the project directory as part of Task6) and not the
movie.json (previous file that was downloaded as part of Exercise:1) for this task.

**Task 8 - Write a mongodb query to find the year in which most number of movies were
released
Take a screenshot of the command you used and the output.**

![T8](https://user-images.githubusercontent.com/121275064/233767577-3e4289c4-1a24-4a73-ae7c-0f8ea27e7bd0.JPG)

**Task 9 - Write a mongodb query to find the count of movies released after the year 1999
Take a screenshot of the command you used and the output.**

![T9](https://user-images.githubusercontent.com/121275064/233767632-92612c31-5e91-42e2-92fa-b112ffd96d7d.JPG)

**Task 10. Write a query to find out the average votes for movies released in 2007
Take a screenshot of the command you used and the output.**

![T10](https://user-images.githubusercontent.com/121275064/233767642-dccd6f4a-26fe-4581-8059-b2b8a80e176a.JPG)

**Task 11 - Export the fields _id,“title”,“year”,“rating” and “director” from the ‘movies’collection into a file named partial_data.csv
Take a screenshot of the command you used and the output.**

![T11](https://user-images.githubusercontent.com/121275064/233767655-ce5281c8-a7ab-4832-9530-a1476df8cf14.JPG)

**Exercise 4 - Working with a Cassandra database
Task 12 - Import ‘partial_data.csv’ into cassandra server into a keyspace named
‘entertainment’ and a table named ‘movies’
Note: While creating the table movies make the all the columns as text columns including the id column.
Take a screenshot of the command you used and the output.**

![T12](https://user-images.githubusercontent.com/121275064/233767689-32ab1cd4-52bc-4319-87ba-4e1df898b584.JPG)

**Task 13 - Write a cql query to count the number of rows in the ‘movies’ table
Take a screenshot of the command you used and the output.**

![T13](https://user-images.githubusercontent.com/121275064/233767725-39aceed6-aa03-499d-bc34-a677f18f4ff3.JPG)

**Task 14 - Create an index for the “rating” column in the ‘movies’ table using cql
Take a screenshot of the command you used and the output.**

![T14](https://user-images.githubusercontent.com/121275064/233767723-b6c6394d-fab5-4905-9185-5ae6b02f5a05.JPG)

**Task 15 - Write a cql query to count the number of movies that are rated ‘G’.
Take a screenshot of the command you used and the output.**

![T15](https://user-images.githubusercontent.com/121275064/233767719-8caba259-23a3-4c57-8fa9-96631196ca5d.JPG)

End of assignment.
