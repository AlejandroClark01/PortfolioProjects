**Data used in this project
In this project, you will be working with a subset of data from the Coffee shop sample data.**

You will use a modified version of the data for the project, so to succeed in the project, download the linked files when prompted in the instructions. You do not need to use any data from the original source.

**In your scenario, you will be working with data from the following sources:**

Staff information held in a spreadsheet at HQ
Sales outlet information held in a spreadsheet at HQ
Sales data output as a CSV file from the POS system in the sales outlets
Customer data output as a CSV file from a bespoke customer relationship management system
Product information maintained in a spreadsheet exported from your supplier’s database

**Objectives
After completing this lab, you will be able to:**

Identify entities.
Identity attributes.
Create an entity relationship diagram (ERD) using the pgAdmin ERD Tool.
Normalize tables.
Define keys and relationships.
Create database objects by generating and running the SQL script from the ERD Tool.
Create a view and export the data.
Create a materialized view and export the data.
Import data into a Db2 database.
Import data into a MySQL database.

**Task 1: Identify entities
The first step when designing a new database is to review any existing data and identify the entities for your new system.**

The following image shows sample data from each of the data sources that you will be working with to design your new central database. Review the image and identify the entities you plan to create.

![image](https://user-images.githubusercontent.com/121275064/230527818-f6e98528-7a57-4c51-92b8-4c7b38cef58c.png)

Note: You might find it useful to download a copy of this image or open it in another browser tab for reference later in the lab.
Make a list of the entities you have identified.

**Task 2: Identify attributes
In this task, you will identify the attributes for one of the entities that you plan to create.**

Using the information from the sample data in the image from Task 1, identify the attributes for the entity that will store the sales transaction data.

Make a list of the sales transaction attributes that you identified.

**Task 3: Create an ERD
Now that you have defined some of your attributes and entities, you can determine the tables and columns for them and create an ERD.**

Open a new terminal from the side-by-side Cloud IDE.

Use the start_postgres command to start a PostgreSQL service session in the Cloud IDE.

Use the pgAdmin weblink to open pgAdmin in a new tab in your browser.

Create a new database named COFFEE, view the schemas in the new COFFEE database, and then start a new ERD project.

Add a table to the ERD for the sale transactions entity using the information in the following table. Consider what naming convention to use so that your colleagues will be able to understand your data and to ensure that the names are valid in other RDBMS. And use the sample data shown in the image in Task 1 to determine appropriate data types for each column.

![image](https://user-images.githubusercontent.com/121275064/230527887-4c97948b-1956-4b6f-b2ed-7f00016281f7.png)

![Task3A](https://user-images.githubusercontent.com/121275064/230527962-e4c17d51-d158-4036-874d-680c31cc8d1b.JPG)

Add a table to the ERD for the product entity using the information in the following table. Consider what naming convention to use so that your colleagues will be able to understand your data and to ensure that the names are valid in other RDBMS. And use the sample data shown in the image in Task 1 to determine appropriate data types for each column.

![image](https://user-images.githubusercontent.com/121275064/230527969-00a03530-4d65-4213-ac2b-96de488013d1.png)

![Task3B](https://user-images.githubusercontent.com/121275064/230527990-3370bd14-4fe2-403d-a5de-acf0d34df69c.JPG)

**Task 4: Normalize tables
When reviewing your ERD you notice that it does not conform to second normal form. In this task, you will normalize some of the tables within the database.**

Review the data in the sales transaction table. Note that the transaction id column does not contain unique values because some transactions include multiple products.

Determine which columns should be stored in a separate table to remove the repeating rows and to put this table into second normal form.

Add a new table named sales_detail to the ERD, define the columns in the new table, and delete the moved columns from the sales transaction table, leaving a matching column in each of two tables to later create a relationship between them.

![Task4A](https://user-images.githubusercontent.com/121275064/230528040-800b3ee2-bf1e-4609-aa61-b6a5fdce56e1.JPG)

Review the data in the product table. Note that the product category and product type columns contain redundant data.

Determine which columns should be stored in a separate table to reduce redundant data and to put this table into second normal form.

Add a new table named product_type to the ERD, define the columns in the new table, and delete the moved columns from the product table, , leaving a matching column in each of two tables to later create a relationship between them.

![Task4B](https://user-images.githubusercontent.com/121275064/230528072-87df4377-eadc-47b6-b557-4cab527a4821.JPG)

**Task 5: Define keys and relationships
After normalizing your tables, you can define their primary keys and define relationships between the tables in your ERD.**

Identify an appropriate column in each table to be a primary key and create the primary keys in the tables in your ERD.

![5A](https://user-images.githubusercontent.com/121275064/230528288-b3418071-ed8e-4f8e-b694-eeb5e66f6dbf.jpg)

Identify the relationships between the following pairs of tables and then create the relationships in your ERD:

sales_detail to sales_transaction\
sales_detail to product\
product to product_type\

![Task5B](https://user-images.githubusercontent.com/121275064/230528151-cc97adcd-b340-41f1-b160-f7c116e8eaa5.JPG)

**Task 6: Create database objects by generating and running the SQL script from the ERD Tool
Now that your design is complete, you will generate an SQL script from your ERD which you could use to create your database schema. For the purposes of this project, you will then use a provided SQL script to ensure that you will be able to successfully load the sample data into the schema. Finally, you will load the existing data from the various data sources into your new database schema.**

Use the Generate SQL functionality in the ERD Tool to create an SQL script from your ERD.

Download the GeneratedScript.sql file below to your local computer storage.

GeneratedScript.sql
In pgAdmin, open the Query Tool, upload and open the GeneratedScript.sql file from your local computer storage, and then execute the script to create the tables defined in the ERD. Verify that the tables now exist in the public schema of the COFFEE database.

![Task6A](https://user-images.githubusercontent.com/121275064/230528277-0fdfcdae-8b75-4955-a61d-5be341e2e30f.jpg)

Download the CoffeeData.sql file below to your local computer storage.

CoffeeData.sql
In pgAdmin, open another instance of the Query Tool, upload and open the CoffeeData.sql file from your local computer storage, and then execute the script to populate the tables you just created.

In pgAdmin, view the first 100 rows of the sales_detail table.

![Task6B](https://user-images.githubusercontent.com/121275064/230528379-dfa5baa7-7ae5-4d16-afca-78de4247687b.jpg)

**Task 7: Create a view and export the data
The external payroll company have requested a list of employees and the locations at which they work. This should not include the CEO or CFO who own the company. In this task, you will create a view in your PostgreSQL database that returns this information and export the results to a CSV file.**

In your COFFEE database, create a new view named staff_locations_view using the following SQL:

`SELECT staff.staff_id,
staff.first_name,
staff.last_name,
staff.location
FROM staff
WHERE "position" NOT IN ('CEO', 'CFO');`

View all the rows returned from the view.

Save the results of the query to a file named staff_locations_view.csv on your local computer storage.

![Task7](https://user-images.githubusercontent.com/121275064/230528399-5aae435e-ec5f-4e81-92df-fc506449f8bc.png)

**Task 8: Create a materialized view and export the data
A marketing consultant requires access to your product data in their MySQL database for a marketing campaign. You will create a materialized view in your PostgreSQL database that returns this information and export the results to a CSV file.**

In your COFFEE database, create a new materialized view named product_info_m-view using the following SQL:

`SELECT product.product_name, product.description, product_type.product_category
FROM product
JOIN product_type
ON product.product_type_id = product_type.product_type_id;`

Refresh the materialized view with data.

View all the rows returned from the view.

Save the results of the query to a file named product_info_m-view.csv on your local computer storage.

![Task8](https://user-images.githubusercontent.com/121275064/230528454-63f9b6a5-e538-45b0-b15e-fccaa2866000.jpg)

**Task 9: Import data into a Db2 database
The external payroll company have asked you to upload the staff location information to their Db2 database.**

In a new browser tab, go to https://cloud.ibm.com/login, log in using your credentials, and then open a console for your Db2 on Cloud instance that you created earlier in this course.

Use the Load Data feature to load a new table named STAFF_LOCATIONS with the staff location information saved in the staff_locations_view.csv file that you exported from the view you created in Task 7.

Explore the new table and then view the data in it.

![Task9](https://user-images.githubusercontent.com/121275064/230528479-2e600962-0a1c-4178-b284-7b6af6b3e908.png)

**Task 10: Import data into a MySQL database
The marketing consultant has asked you to upload the product information to their MySQL database.**

In the terminal from the side-by-side Cloud IDE, use the start_mysql command to start a My SQL service session in the Cloud IDE.

Use the browser weblink to open phpMyAdmin in a new tab in your browser.

In phpMyAdmin, create a new database named coffee_shop_products, and then import the product information saved in the product_info_m-view.csv file from your materialized view into a new table in the coffee_shop_products database.

Browse the contents of the new table.

![Task10](https://user-images.githubusercontent.com/121275064/230528490-357929aa-7d6f-4be2-bb81-c0f575c1731a.png)
