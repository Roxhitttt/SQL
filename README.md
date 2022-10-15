# SQL

Installation has been done through Mysql 
and first command for the mysql is 

mysql -u root -p

SQL is a standard language for accessing and manipulating databases.

SQL stands for Structured Query Language

### What Can SQL do?

SQL can execute queries against a database
SQL can retrieve data from a database
SQL can insert records in a database
SQL can update records in a database
SQL can delete records from a database
SQL can create new databases
SQL can create new tables in a database
SQL can create stored procedures in a database
SQL can create views in a database
SQL can set permissions on tables, procedures, and views

### Using SQL in Your Web Site

To build a web site that shows data from a database, you will need:

An RDBMS database program (i.e. MS Access, SQL Server, MySQL)
To use a server-side scripting language, like PHP or ASP
To use SQL to get the data you want
To use HTML / CSS to style the page

### RDBMS

RDBMS stands for Relational Database Management System.

RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.

The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

### SQL Statements

The following SQL statement selects all the records in the "Customers" table:

SELECT * FROM Customers;

Some database systems require a semicolon at the end of each SQL statement.
SQL keywords are NOT case sensitive: select is the same as SELECT

### Some of The Most Important SQL Commands

SELECT - extracts data from a database
UPDATE - updates data in a database
DELETE - deletes data from a database
INSERT INTO - inserts new data into a database
CREATE DATABASE - creates a new database
ALTER DATABASE - modifies a database
CREATE TABLE - creates a new table
ALTER TABLE - modifies a table
DROP TABLE - deletes a table
CREATE INDEX - creates an index (search key)
DROP INDEX - deletes an index

### SELECT Syntax

- for only two columns 

SELECT column1, column2, ...
FROM table_name;

- for entire table 

SELECT * FROM table_name;

### SELECT DISTINCT Syntax

The SELECT DISTINCT statement is used to return only distinct (different) values.

SELECT DISTINCT column1, column2, ...
FROM table_name;

The following SQL statement lists the number of different (distinct) customer countries:

SELECT COUNT(DISTINCT Country) FROM Customers;

### The SQL WHERE Clause
The WHERE clause is used to filter records.

It is used to extract only those records that fulfill a specified condition.

WHERE Syntax

SELECT column1, column2, ...
FROM table_name
WHERE condition;

SELECT * FROM Customers
WHERE Country='Mexico';

Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!  

SQL requires single quotes around text values (most database systems will also allow double quotes).

However, numeric fields should not be enclosed in quotes

_______________________________________________________________________

### Operators in The WHERE Clause

The following operators can be used in the WHERE clause:                                           

Operator	    Description	                                                                                                                                                                                                                    
=              	Equal	                                                                            
>	              Greater than	                                                                    
<	              Less than	                      
>=	            Greater than or equal	
<=	            Less than or equal	
<>	            Not equal. Note: In some versions of SQL this operator may be written as !=	
BETWEEN	        Between a certain range	
LIKE	          Search for a pattern	
IN	            To specify multiple possible values for a column

_____________________________________________________________________

### The SQL AND, OR and NOT Operators

The WHERE clause can be combined with AND, OR, and NOT operators.

The AND and OR operators are used to filter records based on more than one condition:
- The AND operator displays a record if all the conditions separated by AND are TRUE.
- The OR operator displays a record if any of the conditions separated by OR is TRUE.

The NOT operator displays a record if the condition(s) is NOT TRUE.

AND Syntax

SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;

OR Syntax

SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;

NOT Syntax

SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;


