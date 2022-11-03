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

_____________________________________________________________________
problem Statement: Write a stored procidure namely proc_grade for the caterization of student 

1st condition 1) if marks scored by students in examination is marks <=1500 & marks >=990 then students will be placed in diticntion category 
2) if marks scored between marks 089 and 900 then category is first class
3) if marks 899 and 825 then category is higher second class

write a PL SQL block to use a procedure or function 

Solution:

use rohitdb;

Database changed
mysql> create table stud_marks (stud_id int not NULL,name varchar(50) not NULL, marks int not NULL);
Query OK, 0 rows affected (0.05 sec)

mysql> desc stud_marks;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| stud_id | int         | NO   |     | NULL    |       |
| name    | varchar(50) | NO   |     | NULL    |       |
| marks   | int         | NO   |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
3 rows in set (0.03 sec)

mysql> create table Result (stud_id int not NULL,name varchar(50) not NULL,class varchar(50) not NULL);
Query OK, 0 rows affected (0.03 sec)

mysql> desc Result;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| stud_id | int         | NO   |     | NULL    |       |
| name    | varchar(50) | NO   |     | NULL    |       |
| class   | varchar(50) | NO   |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> delimiter $
mysql> create procedure proc_grade(IN a int,IN b varchar(20),IN m int)
    -> begin
    -> declare c varchar(20);
    -> if(m<=1500 and m>=990)then
    -> set c='Distinction';
    -> elseif(m<=989 and m>=900)then
    -> set c='First Class';
    -> elseif(m<=899 and m>=825)then
    -> set c='Second Class';
    -> end if;
    -> insert into Result values(a,b,c);
    -> insert into stud_marks values(a,b,m);
    -> select * from stud_marks;
    -> select * from Result;
    -> end;
    -> $
Query OK, 0 rows affected (0.03 sec)

mysql> call proc_grade(1,'Ram',1500)$
+---------+------+-------+
| stud_id | name | marks |
+---------+------+-------+
|       1 | Ram  |  1500 |
+---------+------+-------+
1 row in set (0.02 sec)

+---------+------+-------------+
| stud_id | name | class       |
+---------+------+-------------+
|       1 | Ram  | Distinction |
+---------+------+-------------+
1 row in set (0.03 sec)

Query OK, 0 rows affected (0.03 sec)

mysql> call proc_grade(2,'Rohit',989)$
+---------+-------+-------+
| stud_id | name  | marks |
+---------+-------+-------+
|       1 | Ram   |  1500 |
|       2 | Rohit |   989 |
+---------+-------+-------+
2 rows in set (0.01 sec)

+---------+-------+-------------+
| stud_id | name  | class       |
+---------+-------+-------------+
|       1 | Ram   | Distinction |
|       2 | Rohit | First Class |
+---------+-------+-------------+
2 rows in set (0.03 sec)

Query OK, 0 rows affected (0.03 sec)

mysql> call proc_grade(3,'shafiq',899)$
+---------+--------+-------+
| stud_id | name   | marks |
+---------+--------+-------+
|       1 | Ram    |  1500 |
|       2 | Rohit  |   989 |
|       3 | shafiq |   899 |
+---------+--------+-------+
3 rows in set (0.01 sec)

+---------+--------+--------------+
| stud_id | name   | class        |
+---------+--------+--------------+
|       1 | Ram    | Distinction  |
|       2 | Rohit  | First Class  |
|       3 | shafiq | Second Class |
+---------+--------+--------------+
3 rows in set (0.03 sec)

Query OK, 0 rows affected (0.04 sec)


_____________________________________________________________________
Problem Statement: Write PL\SQL code block using control structure for following requriements:-

Accept roll no and name of book from user check the no of days from the date of issue, if dates are between 15-30 then fine amount will be rs 50 per day, if no of days greater than 30 fin will be rs 5 per day and for days less then 30 rs 5 per day
After submitting the book starts will be changed from I to R if condition of fine is ture the details will be stored into fine table

SCHEMA:- 1] Borrower(Rool no, Date, Date of issue, Name of book,Status)
2] fine (roll no, date , amt)


Function name: datediff():- The datediff() function returns the difference in days between two date values

Syntax:- DATEDIFF(date1,date2)
eg:-1)SELECT DATEDIFF('2022-06-25','2022-06-23');
2)SELECT DATEDIFF(curdate(),'2022-11-01');
