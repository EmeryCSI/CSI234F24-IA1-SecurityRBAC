# Renton Technical College CSI-234
<br />    

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Independent Activity1</h3>
</div>

This repository is a part of CSI-234 at Renton Technical College.

Clone this repository to your local machine and complete the instructions below. You will be submitting screenshots as well as SQL code in this repository

## Independent Activity 1 - Project Setup

1. Clone the repository to your local machine using GitHub Desktop or other GitHub tool.
2. Make note of the folder where you cloned the repository.
3. Click Show in Explorer to open the repository folder.
4. Inside of this folder create a screenshots folder. This is where you will save your screenshots for this assignmnent.
5. Just to test that it is working take a screenshot of your desktop and save it inside of the screenshots folder.
6. Create a new commit "Testing Screenshots" and push the changes to GitHub.


### Assignment: Create SQL Server Logins with Varying Access Levels

#### Objective:
Create 5 different logins for your SQL Server, each with varying levels of access that might commonly be needed in a deployed cloud database.
Save the .sql script for each user in the assignment repository.
<p><a href="https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16">Server-level roles - SQL Server | Microsoft Learn</a></p>
<p><a href="https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/database-level-roles?view=sql-server-ver16">Database-Level Roles - SQL Server | Microsoft Learn</a></p>

#### Template:
```sql
-- Run on master
CREATE LOGIN [LoginName] WITH PASSWORD = '[SecurePassword]';

-- RUN on the database that you want the user to access
CREATE USER [LoginName]
FROM LOGIN [LoginName]
-- Add the roles or permissions that you want the user to have based on the description
```

#### Note:
- Replace `[LoginName]` with the actual name of the login and `[SecurePassword]` with a secure password.
- Adapt the script to meet the access level described for each login.

#### Login 1: Report Generator
- **Description:** This login is for a report generator who needs read-only access to the database.
- **Access Level:** Read-only access to all tables in the database.
- **Create a new query to create this user:** Save the .sql file to this repository.
- **Login with the new Account:**

- **Run the following Queries and Screenshot the output**

  - **This Query should work**
    ```sql
    SELECT * FROM SalesLT.Customer;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

  - **This Query should fail**
    ```sql
    DELETE FROM SalesLT.Customer WHERE CustomerID = 1;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory


#### Login 2: Sales API
- **Description:** This login is for a Web API that has full read/write access but only to tables in the SalesLT schema.
- **Access Level:** Full read/write access to tables in the SalesLT schema.
- **Create a new query to create this user:** Save the .sql file to this repository.
- **Login with the new Account:**

- **Run the following Queries and Screenshot the output**

  - **This Query should work**
    ```sql
    SELECT FirstName, LastName FROM SalesLT.Customer WHERE CompanyName IS NOT NULL;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

  - **This Query should fail**
    ```sql
    UPDATE SalesLT.Product SET ListPrice = ListPrice * 0.9 WHERE ProductID < 100;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

#### Login 3: DB Maintenance
- **Description:** This login is for a database maintenance user who needs to perform maintenance tasks such as reindexing and backups.
- **Access Level:** Ability to perform maintenance tasks and backups.
- **Create a new query to create this user:** Save the .sql file to this repository.
- **Login with the new Account:**

- **Run the following Queries and Screenshot the output**

  - **This Query should work**
    ```sql
    SELECT AVG(ListPrice) AS AveragePrice FROM SalesLT.Product;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

  - **This Query should fail**
    ```sql
    INSERT INTO SalesLT.Address (AddressLine1, City, StateProvince, CountryRegion, PostalCode) VALUES ('123 Main St', 'Anytown', 'Anystate', 'USA', '12345');
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory



#### Login 4: Data Analyst
- **Description:** This login is for a data analyst who needs read access to all tables and execute access to stored procedures.
- **Access Level:** Read access to all tables and execute access to stored procedures.
- **Create a new query to create this user:** Save the .sql file to this repository.
- **Login with the new Account:**

- **Run the following Queries and Screenshot the output**

  - **This Query should work**
    ```sql
    SELECT TOP 5 * FROM SalesLT.SalesOrderHeader ORDER BY SalesOrderID DESC;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

  - **This Query should fail**
    ```sql
    ALTER TABLE SalesLT.SalesOrderDetail ADD DiscountAmount DECIMAL(10, 2);
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory


#### Login 5: Guest User
- **Description:** This login is for a guest user who needs limited read-only access to view product information.
- **Access Level:** Read-only access to SalesLT.Product table.
- **Create a new query to create this user:** Save the .sql file to this repository.
- **Login with the new Account:**

- **Run the following Queries and Screenshot the output**

  - **This Query should work**
    ```sql
    SELECT MIN(OrderQty) AS MinimumOrderQuantity FROM SalesLT.SalesOrderDetail;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

  - **This Query should fail**
    ```sql
    DROP TABLE SalesLT.Address;
    ```
    Run this query and take a screenshot of the output and add to the screenshots directory

Create a new Commit in GitHub Desktop with "Assignment Complete"
Push the changes to GitHub.


If you have any questions about this assignment please reach out to myself or our TA for this course. 



Feel free to message your instructor or the TA on Canvas if you have any questions.
