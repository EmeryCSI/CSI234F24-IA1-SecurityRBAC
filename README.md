# Renton Technical College CSI-234

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Independent Activity 2: RBAC Implementation in AdventureWorksLT</h3>
</div>

This repository is a part of CSI-234 at Renton Technical College.

Clone this repository to your local machine and complete the instructions below. You will be submitting your SQL scripts and screenshots of your output.

## Independent Activity 2 Part 1: Repository Setup

1. Clone the repository to your local machine using GitHub Desktop or another GitHub tool.
2. Make note of the folder where you cloned the repository.

## Part 2: Database Exploration and User Creation

1. Connect to your SQL Server instance and use the AdventureWorksLT database.
2. Explore the existing tables in the SalesLT schema. You'll be working with these tables for your RBAC implementation.
3. We need to create logins and users for the following accounts.
   - ProjectManager
   - Developer
   - HR_Specialist
   - Sales_Representative
4. Save your user creation SQL script as `01_Logins_Users.sql`.

## Part 3: Role Creation and Permission Assignment

1. Create appropriate roles for each of the users you created.
2. Assign permissions to the roles based on the following requirements:
   - Project Managers should have full access to the SalesLT.Product and SalesLT.ProductCategory tables, and read-only access to SalesLT.Customer and SalesLT.SalesOrderHeader.
   - Developers should have read and update access to SalesLT.Product and SalesLT.ProductCategory, but no access to customer or sales information.
   - HR Specialists should have full access to SalesLT.Customer, but no access to product or sales information.
   - Sales Representatives should have read and update access to SalesLT.Customer and SalesLT.SalesOrderHeader, read-only access to SalesLT.Product, and no access to SalesLT.ProductCategory.
3. Save your role creation and permission assignment SQL script as `02_roles_and_permissions.sql`.

## Part 4: Column-Level Security

1. Implement column-level security for at least one sensitive column in each of the following tables. You may choose which column:
   - SalesLT.Product
   - SalesLT.Customer
   - SalesLT.SalesOrderHeader
2. Save your column-level security SQL script as `03_column_security.sql`.

## Part 5: Testing

In this section, you'll write and execute SQL queries to test the access for each role, ensuring they can perform allowed actions and are restricted from unauthorized access. You'll also test your column-level security implementation.

1. Create a new SQL script file named `04_access_tests.sql` in your repository.

2. In this file, include the following tests for each role. Be sure to use the EXECUTE AS USER statement to switch contexts for each test, and REVERT to switch back.

### ProjectManager Tests:
a. Test full access to SalesLT.Product (take screenshot):
   ```sql
   EXECUTE AS USER = 'ProjectManager';
   -- Attempt to SELECT, INSERT, UPDATE, and DELETE on SalesLT.Product
   -- Show the results
   REVERT;
   ```

b. Test read-only access to SalesLT.Customer (take screenshot):
   ```sql
   EXECUTE AS USER = 'ProjectManager';
   -- Attempt to SELECT from SalesLT.Customer (should succeed)
   -- Attempt to INSERT into SalesLT.Customer (should fail)
   -- Show the results of both attempts
   REVERT;
   ```

### Developer Tests:
a. Test read and update access to SalesLT.ProductCategory (take screenshot):
   ```sql
   EXECUTE AS USER = 'Developer';
   -- Attempt to SELECT and UPDATE SalesLT.ProductCategory (should succeed)
   -- Attempt to DELETE from SalesLT.ProductCategory (should fail)
   -- Show the results of all attempts
   REVERT;
   ```

b. Test no access to SalesLT.SalesOrderHeader (take screenshot):
   ```sql
   EXECUTE AS USER = 'Developer';
   -- Attempt to SELECT from SalesLT.SalesOrderHeader (should fail)
   -- Show the result
   REVERT;
   ```

### HR_Specialist Tests:
a. Test full access to SalesLT.Customer (take screenshot):
   ```sql
   EXECUTE AS USER = 'HR_Specialist';
   -- Attempt to SELECT, INSERT, UPDATE, and DELETE on SalesLT.Customer
   -- Show the results
   REVERT;
   ```

b. Test no access to SalesLT.Product (take screenshot):
   ```sql
   EXECUTE AS USER = 'HR_Specialist';
   -- Attempt to SELECT from SalesLT.Product (should fail)
   -- Show the result
   REVERT;
   ```

### Sales_Representative Tests:
a. Test read and update access to SalesLT.SalesOrderHeader (take screenshot):
   ```sql
   EXECUTE AS USER = 'Sales_Representative';
   -- Attempt to SELECT and UPDATE SalesLT.SalesOrderHeader (should succeed)
   -- Attempt to DELETE from SalesLT.SalesOrderHeader (should fail)
   -- Show the results of all attempts
   REVERT;
   ```

3. Include screenshots of your test results, clearly showing which tests passed and failed. Save these screenshots in the repository with the query.


## Submission

1. Ensure all your SQL scripts are saved in the repository.
2. Include all of your screenshots in the repository.
3. Commit your changes with the message "Independent Activity 1 Complete".
4. Push your changes to GitHub.


If you have any questions about this assignment, please reach out to your instructor or the TA for this course.
