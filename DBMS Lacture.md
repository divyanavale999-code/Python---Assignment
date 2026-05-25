DATE : 11-05-2026

Database Management System

Data : Analysis : Analyze the data

Relational Database : RDBMS : SQL

Structured Query Language

Software Tools :

1\. MySQL

2\. Oracle

3\. PosgresSQL

4\. Sqllite


Cloud :

AWS : Amazon Web Services

Azure : Microsoft : TQL : Transact Query Language

Google Cloud


Database : Collection of tables : Schema



Database Vs Schema : 

Database : Collection of tables

Schema : A database schema is the "blueprint" or formal structure of a database. It defines how data is organized,

how tables are structured and how they relate to one another.

while the schema acts as the skeleton, it does not actually contain any data, the data present at a specific point in

time is instead called a database instance.



tables : collection of rows and columns

rows : tuple : record

columns : fields



SQL (Structure Query Language) commands are categorized into different "language" based on whether

they affect the database's structure, the actual data, or the permissions.



DDL : Data Definition Database : Create, Alter, Drop, Truncate, Rename

DML : Data Manipulation Database : Insert, Update, Delete, Call, Explain Call

DCL : Data Control Language : Grant, Revoke

TCL : Transaction Control Language : Commit, Rollback, Savepoints

properties : ACID is a properties

A : Atomicity

C : Consistency

I : Isolation

D : Durability


DQL : Data Query Language : Select

TQL : Transact Query Language

PL/SQL :



Advanced SQL Queries :

View :

CTE : Common Table Expressions

Windows Function


DATE : 12-05-2026


SQL Queries :

show databases; : this query will list the database present in MySQL

create database <database-name>;



table :

row : tuple : record

column : fields



create the table :

create table <table-name> <fieldsname data types>;



Data Types :

Numerical Data : 

Integer : 2, 4, 6, 9, 1

smallint : 2 bytes

int : 4 bytes

mediumint : 3 bytes

tinyint : 1 bytes

bigint : 8 bytes



Decimal : 2.564, 3.14567

float

double

decimal(8, 2)



student :

id : int



**Date : 13-05-2026**


mysql> show databases;

+--------------------+

| Database           |

+--------------------+

| demodata           |

| information\_schema |

| mydb               |

| mysql              |

| performance\_schema |

| sakila             |

| sys                |

| world              |

+--------------------+

8 rows in set (0.03 sec)



mysql> drop database mydb;

Query OK, 1 row affected (0.04 sec)



mysql> show databases;

+--------------------+

| Database           |

+--------------------+

| demodata           |

| information\_schema |

| mysql              |

| performance\_schema |

| sakila             |

| sys                |

| world              |

+--------------------+

7 rows in set (0.00 sec)



mysql> create database mydb;

Query OK, 1 row affected (0.01 sec)



mysql> use mydb;

Database changed

mysql> select database();

+------------+

| database() |

+------------+

| mydb       |

+------------+

1 row in set (0.00 sec)



mysql> create table employee(emp\_id int, emp\_name varchar(50), email varchar(35));

Query OK, 0 rows affected (0.03 sec)



mysql> show tables;

+----------------+

| Tables\_in\_mydb |

+----------------+

| employee       |

+----------------+

1 row in set (0.01 sec)



mysql> describe employee;

+----------+-------------+------+-----+---------+-------+

| Field    | Type        | Null | Key | Default | Extra |

+----------+-------------+------+-----+---------+-------+

| emp\_id   | int         | YES  |     | NULL    |       |

| emp\_name | varchar(50) | YES  |     | NULL    |       |

| email    | varchar(35) | YES  |     | NULL    |       |

+----------+-------------+------+-----+---------+-------+

3 rows in set (0.01 sec)



mysql> alter table employee add column gender varchar(10);

Query OK, 0 rows affected (0.07 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> decribe employee;

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'decribe employee' at line 1

mysql> describe employee;

+----------+-------------+------+-----+---------+-------+

| Field    | Type        | Null | Key | Default | Extra |

+----------+-------------+------+-----+---------+-------+

| emp\_id   | int         | YES  |     | NULL    |       |

| emp\_name | varchar(50) | YES  |     | NULL    |       |

| email    | varchar(35) | YES  |     | NULL    |       |

| gender   | varchar(10) | YES  |     | NULL    |       |

+----------+-------------+------+-----+---------+-------+

4 rows in set (0.00 sec)



mysql> alter table employee add column DOB date after email;

Query OK, 0 rows affected (0.08 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> describe emloyee;

ERROR 1146 (42S02): Table 'mydb.emloyee' doesn't exist

mysql> describe employee;

+----------+-------------+------+-----+---------+-------+

| Field    | Type        | Null | Key | Default | Extra |

+----------+-------------+------+-----+---------+-------+

| emp\_id   | int         | YES  |     | NULL    |       |

| emp\_name | varchar(50) | YES  |     | NULL    |       |

| email    | varchar(35) | YES  |     | NULL    |       |
/
| DOB      | date        | YES  |     | NULL    |       |

| gender   | varchar(10) | YES  |     | NULL    |       |

+----------+-------------+------+-----+---------+-------+

5 rows in set (0.01 sec)



mysql> alter table employee drop gender;

Query OK, 0 rows affected (0.07 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> describe employee;

+----------+-------------+------+-----+---------+-------+

| Field    | Type        | Null | Key | Default | Extra |

+----------+-------------+------+-----+---------+-------+

| emp\_id   | int         | YES  |     | NULL    |       |

| emp\_name | varchar(50) | YES  |     | NULL    |       |

| email    | varchar(35) | YES  |     | NULL    |       |

| DOB      | date        | YES  |     | NULL    |       |

+----------+-------------+------+-----+---------+-------+

4 rows in set (0.00 sec)



mysql> alter table employee rename email to emp\_email;

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to emp\_email' at line 1

mysql> alter table employee rename email to emp\_email;

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to emp\_email' at line 1

mysql> ^C

mysql> alter table employee rename column email to emp\_email;

Query OK, 0 rows affected (0.03 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> alter table employee rename column DOB to emp\_DOB;

Query OK, 0 rows affected (0.04 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> describe employee;

+-----------+-------------+------+-----+---------+-------+

| Field     | Type        | Null | Key | Default | Extra |

+-----------+-------------+------+-----+---------+-------+

| emp\_id    | int         | YES  |     | NULL    |       |

| emp\_name  | varchar(50) | YES  |     | NULL    |       |

| emp\_email | varchar(35) | YES  |     | NULL    |       |

| emp\_DOB   | date        | YES  |     | NULL    |       |

+-----------+-------------+------+-----+---------+-------+

4 rows in set (0.01 sec)



mysql> alter table employee modify column emp\_id bigint;

Query OK, 0 rows affected (0.11 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> describe employee;

+-----------+-------------+------+-----+---------+-------+

| Field     | Type        | Null | Key | Default | Extra |

+-----------+-------------+------+-----+---------+-------+

| emp\_id    | bigint      | YES  |     | NULL    |       |

| emp\_name  | varchar(50) | YES  |     | NULL    |       |

| emp\_email | varchar(35) | YES  |     | NULL    |       |

| emp\_DOB   | date        | YES  |     | NULL    |       |

+-----------+-------------+------+-----+---------+-------+

4 rows in set (0.01 sec)



mysql> alter table employee change column emp\_email to email char(50);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to email char(50)' at line 1

mysql> alter table employee change column emp\_email varchar(35) to email varchar(40);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'varchar(35) to email varchar(40)' at line 1

mysql> alter table employee change column emp\_email varchar(35) to email varchar(40);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'varchar(35) to email varchar(40)' at line 1

mysql> alter table employee change emp\_email to email varchar(40);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to email varchar(40)' at line 1

mysql> alter table employee change emp\_email email varchar(40);

Query OK, 0 rows affected (0.02 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> describe employee;

+----------+-------------+------+-----+---------+-------+

| Field    | Type        | Null | Key | Default | Extra |

+----------+-------------+------+-----+---------+-------+

| emp\_id   | bigint      | YES  |     | NULL    |       |

| emp\_name | varchar(50) | YES  |     | NULL    |       |

| email    | varchar(40) | YES  |     | NULL    |       |

| emp\_DOB  | date        | YES  |     | NULL    |       |

+----------+-------------+------+-----+---------+-------+

4 rows in set (0.00 sec)


DATE :- 14-05-2026

Constraints :
primary Key : only one field in one table
Foreign Key : parent child relationship : connect multiple tables
Not Null : not insert null value
Unique Key : multiple fields in one table
Default : insert default value if value will not pass
Check : condition will be check

DATE :- 15-05-2026

Aggregate Function : 

COUNT() : Returns the number of rows that match a specific condition.

COUNT(*) : Includes all rows, even those with NULL values.

COUNT(column) only counts rows where the column value is not NULL.

SUM() : Calculate the total sum of values in a numeric column, ignoring NULL values.

AVG() : Computes the average(mean) of a numeric column by dividing the sum by the count of non-NULL values.

MAX() : Retrieves the highest (maximum) value in a set, working with numbers, dates and strings.

MIN() : Retrieves the lowest (minimum) value in a set.

Functions and Operators : 

Functions:
1. String Functions :
2. Date and Time Functions :

Operators : 
like : pattern matching
abc% : starts with abc and ends with anything.

1. Arithmetic Operators :

2. Relational Operators : 

3. Decision Control Structure: 
where

4. Logical Operators : 

5. Bitwise Operators :

6. Ternary operators :


DATE :- 16-05-2026

Enter password: ******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.45 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mdb;
Database changed
mysql> show database;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database' at line 1
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| demodata           |
| information_schema |
| mdb                |
| mydb               |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
9 rows in set (0.02 sec)

mysql> create table student;
ERROR 1050 (42S01): Table 'student' already exists
mysql> create table students;
ERROR 4028 (HY000): A table must have at least one visible column.
mysql> create table students(ID int, Name varchar(30), Email varchar(50), Phone int, About varchar(100));
Query OK, 0 rows affected (0.04 sec)

mysql> insert into students values(1, "Nasir", "nasir@gmail.com", 1637017926, "This is about of nasir"),(2, "Lalon", "lalon@gmail.com", 1637417926, "This is about of lalon"),(3, "Kamrul", "kamrul@gmail.com", 1637411926, "This is about of kamrul"),(4, "Noman", "Noman@gmail.com", 1636717926, "This is about of Noman"),(5, "Mim", "mim@gmail.com", 1655417926, "This is about of mim"),(6, "Monju", "monju@gmail.com", 1637417456, "This is about of monju"),(7, "Riad", "riad@gmail.com", 1637413242, "This is about of riad");
Query OK, 7 rows affected (0.01 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> select * from students;
+------+--------+------------------+------------+-------------------------+
| ID   | Name   | Email            | Phone      | About                   |
+------+--------+------------------+------------+-------------------------+
|    1 | Nasir  | nasir@gmail.com  | 1637017926 | This is about of nasir  |
|    2 | Lalon  | lalon@gmail.com  | 1637417926 | This is about of lalon  |
|    3 | Kamrul | kamrul@gmail.com | 1637411926 | This is about of kamrul |
|    4 | Noman  | Noman@gmail.com  | 1636717926 | This is about of Noman  |
|    5 | Mim    | mim@gmail.com    | 1655417926 | This is about of mim    |
|    6 | Monju  | monju@gmail.com  | 1637417456 | This is about of monju  |
|    7 | Riad   | riad@gmail.com   | 1637413242 | This is about of riad   |
+------+--------+------------------+------------+-------------------------+
7 rows in set (0.00 sec)

mysql> alter table students modify column Name bigint;
ERROR 1366 (HY000): Incorrect integer value: 'Nasir' for column 'Name' at row 1
mysql> alter table students modify column ID bigint;
Query OK, 7 rows affected (0.11 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> alter table students modify column Phone bigint;
Query OK, 7 rows affected (0.07 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> alter table students modify column ID int;
Query OK, 7 rows affected (0.07 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> drop table student;
Query OK, 0 rows affected (0.02 sec)

mysql> create table student(ID int primary key auto_increment, Name varchar(50) unique, Email varchar(50), Phone bigint, about varchar(50));
Query OK, 0 rows affected (0.24 sec)

mysql> describe student;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| ID    | int         | NO   | PRI | NULL    | auto_increment |
| Name  | varchar(50) | YES  | UNI | NULL    |                |
| Email | varchar(50) | YES  |     | NULL    |                |
| Phone | bigint      | YES  |     | NULL    |                |
| about | varchar(50) | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> create table student table(ID int, name varchar(50), Email varchar(50), Phone bigint, About varchar(50));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(ID int, name varchar(50), Email varchar(50), Phone bigint, About varchar(50))' at line 1
mysql> create table student_table(ID int, name varchar(50), Email varchar(50), Phone bigint, About varchar(50));
Query OK, 0 rows affected (0.06 sec)

mysql> describe student_table;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| ID    | int         | YES  |     | NULL    |       |
| name  | varchar(50) | YES  |     | NULL    |       |
| Email | varchar(50) | YES  |     | NULL    |       |
| Phone | bigint      | YES  |     | NULL    |       |
| About | varchar(50) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
5 rows in set (0.01 sec)

mysql> alter table student_table modify column ID int primary key not null auto_increment;
Query OK, 0 rows affected (0.18 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_table;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| ID    | int         | NO   | PRI | NULL    | auto_increment |
| name  | varchar(50) | YES  |     | NULL    |                |
| Email | varchar(50) | YES  |     | NULL    |                |
| Phone | bigint      | YES  |     | NULL    |                |
| About | varchar(50) | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> alter table student_table modify column email varchar(50) unique not null;
Query OK, 0 rows affected (2.62 sec)
Records: 0  Duplicates: 0  Warnings: 0


mysql> describe student_table;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| ID    | int         | NO   | PRI | NULL    | auto_increment |
| name  | varchar(50) | YES  |     | NULL    |                |
| email | varchar(50) | NO   | UNI | NULL    |                |
| Phone | bigint      | YES  |     | NULL    |                |
| About | varchar(50) | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> alter table student_table modify column Phone bigint default 000;
Query OK, 0 rows affected (0.34 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_table;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| ID    | int         | NO   | PRI | NULL    | auto_increment |
| name  | varchar(50) | YES  |     | NULL    |                |
| email | varchar(50) | NO   | UNI | NULL    |                |
| Phone | bigint      | YES  |     | 0       |                |
| About | varchar(50) | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql>
mysql>
mysql> drop table employee;
ERROR 1051 (42S02): Unknown table 'mdb.employee'
mysql> create table employee (emp_id int, emp_name varchar(100), DeptName varchar(10), designation varchar(50), DOJ date, Salary float, primary key(emp_id));
Query OK, 0 rows affected (0.04 sec)

mysql> describe employee;
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| emp_id      | int          | NO   | PRI | NULL    |       |
| emp_name    | varchar(100) | YES  |     | NULL    |       |
| DeptName    | varchar(10)  | YES  |     | NULL    |       |
| designation | varchar(50)  | YES  |     | NULL    |       |
| DOJ         | date         | YES  |     | NULL    |       |
| Salary      | float        | YES  |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> alter table employee modify column emp_id int auto_increment;
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employee;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| emp_id      | int          | NO   | PRI | NULL    | auto_increment |
| emp_name    | varchar(100) | YES  |     | NULL    |                |
| DeptName    | varchar(10)  | YES  |     | NULL    |                |
| designation | varchar(50)  | YES  |     | NULL    |                |
| DOJ         | date         | YES  |     | NULL    |                |
| Salary      | float        | YES  |     | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
6 rows in set (0.00 sec)

mysql> insert table employee values(1, "Colleen Hurst", "HQ", "Regional Director", "2009-09-15", 205500),(2, "Brielle Williamson", "Software", "Integration Specialist", "2012-12-02", 372000),(3, "Garrett Winters", "Finance", "Accountant", "2011-07-25", 170750),(4, "Caesar Vance", "Sales", "Sales Support", "2011-12-12", 106450),(5, "Sonya Frost", "Software", "Software Engineer", "2008-12-13", 133600),(6, "Herrod Chandler", "Sales", "Sales Executive", "2012-08-06", 127500),(7, "Jena Gains", "HQ", "Office Manager", "2008-12-19", 90560);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table employee values(1, "Colleen Hurst", "HQ", "Regional Director", "2009-09-15' at line 1
mysql> insert table employee values(1, "Colleen Hurst", "HQ", "Regional Director", '2009-09-15', 205500),(2, "Brielle Williamson", "Software", "Integration Specialist", "2012-12-02", 372000),(3, "Garrett Winters", "Finance", "Accountant", "2011-07-25", 170750),(4, "Caesar Vance", "Sales", "Sales Support", "2011-12-12", 106450),(5, "Sonya Frost", "Software", "Software Engineer", "2008-12-13", 133600),(6, "Herrod Chandler", "Sales", "Sales Executive", "2012-08-06", 127500),(7, "Jena Gains", "HQ", "Office Manager", "2008-12-19", 90560);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table employee values(1, "Colleen Hurst", "HQ", "Regional Director", '2009-09-15' at line 1
mysql> insert table employee values(1, "Colleen Hurst", "HQ", "Regional Director", 2009-09-15, 205500),(2, "Brielle Williamson", "Software", "Integration Specialist", 2012-12-02, 372000),(3, "Garrett Winters", "Finance", "Accountant", 2011-07-25, 170750),(4, "Caesar Vance", "Sales", "Sales Support", 2011-12-12, 106450),(5, "Sonya Frost", "Software", "Software Engineer", 2008-12-13, 133600),(6, "Herrod Chandler", "Sales", "Sales Executive", 2012-08-06, 127500),(7, "Jena Gains", "HQ", "Office Manager", 2008-12-19, 90560);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table employee values(1, "Colleen Hurst", "HQ", "Regional Director", 2009-09-15,' at line 1
mysql> insert into employee values(1, "Colleen Hurst", "HQ", "Regional Director", "2009-09-15", 205500),(2, "Brielle Williamson", "Software", "Integration Specialist", "2012-12-02", 372000),(3, "Garrett Winters", "Finance", "Accountant", "2011-07-25", 170750),(4, "Caesar Vance", "Sales", "Sales Support", "2011-12-12", 106450),(5, "Sonya Frost", "Software", "Software Engineer", "2008-12-13", 133600),(6, "Herrod Chandler", "Sales", "Sales Executive", "2012-08-06", 127500),(7, "Jena Gains", "HQ", "Office Manager", "2008-12-19", 90560);
Query OK, 7 rows affected (0.01 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> describe employee;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| emp_id      | int          | NO   | PRI | NULL    | auto_increment |
| emp_name    | varchar(100) | YES  |     | NULL    |                |
| DeptName    | varchar(10)  | YES  |     | NULL    |                |
| designation | varchar(50)  | YES  |     | NULL    |                |
| DOJ         | date         | YES  |     | NULL    |                |
| Salary      | float        | YES  |     | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
6 rows in set (0.00 sec)

mysql> select * from employee;
+--------+--------------------+----------+------------------------+------------+--------+
| emp_id | emp_name           | DeptName | designation            | DOJ        | Salary |
+--------+--------------------+----------+------------------------+------------+--------+
|      1 | Colleen Hurst      | HQ       | Regional Director      | 2009-09-15 | 205500 |
|      2 | Brielle Williamson | Software | Integration Specialist | 2012-12-02 | 372000 |
|      3 | Garrett Winters    | Finance  | Accountant             | 2011-07-25 | 170750 |
|      4 | Caesar Vance       | Sales    | Sales Support          | 2011-12-12 | 106450 |
|      5 | Sonya Frost        | Software | Software Engineer      | 2008-12-13 | 133600 |
|      6 | Herrod Chandler    | Sales    | Sales Executive        | 2012-08-06 | 127500 |
|      7 | Jena Gains         | HQ       | Office Manager         | 2008-12-19 |  90560 |
+--------+--------------------+----------+------------------------+------------+--------+
7 rows in set (0.00 sec)

mysql>


DATE :-  18-05-2026

Enter password: ******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.45 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mdb;
Database changed
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| demodata           |
| information_schema |
| mdb                |
| mydb               |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
9 rows in set (0.02 sec)

mysql> show tables;
+---------------+
| Tables_in_mdb |
+---------------+
| employee      |
| student       |
+---------------+
2 rows in set (0.01 sec)

mysql> select * from employee;
+--------+--------------------+----------+------------------------+------------+--------+
| emp_id | emp_name           | DeptName | designation            | DOJ        | Salary |
+--------+--------------------+----------+------------------------+------------+--------+
|      1 | Colleen Hurst      | HQ       | Regional Director      | 2009-09-15 | 205500 |
|      2 | Brielle Williamson | Software | Integration Specialist | 2012-12-02 | 372000 |
|      3 | Garrett Winters    | Finance  | Accountant             | 2011-07-25 | 170750 |
|      4 | Caesar Vance       | Sales    | Sales Support          | 2011-12-12 | 106450 |
|      5 | Sonya Frost        | Software | Software Engineer      | 2008-12-13 | 133600 |
|      6 | Herrod Chandler    | Sales    | Sales Executive        | 2012-08-06 | 127500 |
|      7 | Jena Gains         | HQ       | Office Manager         | 2008-12-19 |  90560 |
+--------+--------------------+----------+------------------------+------------+--------+
7 rows in set (0.04 sec)

mysql> use mydb;
Database changed
mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
+----------------+
1 row in set (0.00 sec)

mysql> select * from employee;
+--------+----------+------------------+------+
| emp_id | emp_name | email            | age  |
+--------+----------+------------------+------+
|    101 | Divya    | divya@gmail.com  |   28 |
|    102 | Krupesh  | kruesh@live.in   |   21 |
|    103 | Vidhi    | vidhi@hotmail.in |   20 |
|    104 | Nandini  | nandini@live.in  |   21 |
|    104 | Rudra    | rudra@live.in    |   20 |
|    104 | Hardik   | hardik@live.in   |   21 |
+--------+----------+------------------+------+
6 rows in set (0.03 sec)

mysql> create table employees(empid int primary key auto_increment, empname varchar(50), emp_email varchar(50) unique, age int, city varchar(100));
Query OK, 0 rows affected (0.08 sec)

mysql> describe employees;
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| empid     | int          | NO   | PRI | NULL    | auto_increment |
| empname   | varchar(50)  | YES  |     | NULL    |                |
| emp_email | varchar(50)  | YES  | UNI | NULL    |                |
| age       | int          | YES  |     | NULL    |                |
| city      | varchar(100) | YES  |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> insert into employees(empname, emp_email, age, city) values ("Divya", "divya@gmail.com", "24", "Vadodara");
Query OK, 1 row affected (0.01 sec)

mysql> insert into employees(empname, emp_email, age, city) values ("Vidhi", "vidhi@gmail.com", "20", "Vadodara");
Query OK, 1 row affected (0.01 sec)

mysql> insert into employees(empname, emp_email, age, city) values ("Sakshi", "sakshi@gmail.com", "21", "Ahmedabad"),
    -> ("Rudra", "rudra@gmail.com", 21, "Padra");
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> insert into employees(empname, emp_email, age, city) values ("Hardik", "hardik@gmail.com", "23", "Surat"),
    -> ("Nandini", "nandini@gmail.com", 19, "Vadodara");
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from employees;
+-------+---------+-------------------+------+-----------+
| empid | empname | emp_email         | age  | city      |
+-------+---------+-------------------+------+-----------+
|     1 | Divya   | divya@gmail.com   |   24 | Vadodara  |
|     2 | Vidhi   | vidhi@gmail.com   |   20 | Vadodara  |
|     3 | Sakshi  | sakshi@gmail.com  |   21 | Ahmedabad |
|     4 | Rudra   | rudra@gmail.com   |   21 | Padra     |
|     5 | Hardik  | hardik@gmail.com  |   23 | Surat     |
|     6 | Nandini | nandini@gmail.com |   19 | Vadodara  |
+-------+---------+-------------------+------+-----------+
6 rows in set (0.00 sec)

mysql> insert into employees(empname, emp_email, age, city) values ("Ashwini", "ashwini@gmail.com", "22", "Vadodara");
Query OK, 1 row affected (0.01 sec)

mysql> select * from table;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'table' at line 1
mysql> select * from employees;;
+-------+---------+-------------------+------+-----------+
| empid | empname | emp_email         | age  | city      |
+-------+---------+-------------------+------+-----------+
|     1 | Divya   | divya@gmail.com   |   24 | Vadodara  |
|     2 | Vidhi   | vidhi@gmail.com   |   20 | Vadodara  |
|     3 | Sakshi  | sakshi@gmail.com  |   21 | Ahmedabad |
|     4 | Rudra   | rudra@gmail.com   |   21 | Padra     |
|     5 | Hardik  | hardik@gmail.com  |   23 | Surat     |
|     6 | Nandini | nandini@gmail.com |   19 | Vadodara  |
|     7 | Ashwini | ashwini@gmail.com |   22 | Vadodara  |
+-------+---------+-------------------+------+-----------+
7 rows in set (0.00 sec)

ERROR:
No query specified

mysql> select empname, emp_email from employee where age > 20;
ERROR 1054 (42S22): Unknown column 'empname' in 'field list'
mysql> select empname, emp_email from employees where age > 20;
+---------+-------------------+
| empname | emp_email         |
+---------+-------------------+
| Divya   | divya@gmail.com   |
| Sakshi  | sakshi@gmail.com  |
| Rudra   | rudra@gmail.com   |
| Hardik  | hardik@gmail.com  |
| Ashwini | ashwini@gmail.com |
+---------+-------------------+
5 rows in set (0.00 sec)

mysql> select empname, emp_email, age from employees where age > 20 order by desc;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'desc' at line 1
mysql> select empname, emp_email, age from employees where age > 20 order by age desc;
+---------+-------------------+------+
| empname | emp_email         | age  |
+---------+-------------------+------+
| Divya   | divya@gmail.com   |   24 |
| Hardik  | hardik@gmail.com  |   23 |
| Ashwini | ashwini@gmail.com |   22 |
| Sakshi  | sakshi@gmail.com  |   21 |
| Rudra   | rudra@gmail.com   |   21 |
+---------+-------------------+------+
5 rows in set (0.00 sec)

mysql> select max(age) as 'Maximum Age' from employees;
+-------------+
| Maximum Age |
+-------------+
|          24 |
+-------------+
1 row in set (0.00 sec)

mysql> select min(age) as 'Minimum Age' from employees;
+-------------+
| Minimum Age |
+-------------+
|          19 |
+-------------+
1 row in set (0.00 sec)

mysql> select avg(age) as 'Average Age' from employees;
+-------------+
| Average Age |
+-------------+
|     21.4286 |
+-------------+
1 row in set (0.00 sec)

mysql> select sum(age) as 'Sum Age' from employees;
+---------+
| Sum Age |
+---------+
|     150 |
+---------+
1 row in set (0.00 sec)

mysql> select std(age) as 'Standard Devision' from employees;
+--------------------+
| Standard Devision  |
+--------------------+
| 1.5907898179514353 |
+--------------------+
1 row in set (0.00 sec)

mysql> delete from employee where empid = 7;
ERROR 1054 (42S22): Unknown column 'empid' in 'where clause'
mysql> delete from employees where empid = 7;
Query OK, 1 row affected (0.01 sec)

mysql> select * from employees;
+-------+---------+-------------------+------+-----------+
| empid | empname | emp_email         | age  | city      |
+-------+---------+-------------------+------+-----------+
|     1 | Divya   | divya@gmail.com   |   24 | Vadodara  |
|     2 | Vidhi   | vidhi@gmail.com   |   20 | Vadodara  |
|     3 | Sakshi  | sakshi@gmail.com  |   21 | Ahmedabad |
|     4 | Rudra   | rudra@gmail.com   |   21 | Padra     |
|     5 | Hardik  | hardik@gmail.com  |   23 | Surat     |
|     6 | Nandini | nandini@gmail.com |   19 | Vadodara  |
+-------+---------+-------------------+------+-----------+
6 rows in set (0.00 sec)


DATE :- 19-05-2026

Enter password: ******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.45 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mydb;
Database changed
mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
| employees      |
+----------------+
2 rows in set (0.02 sec)

mysql> drop database employees;
ERROR 1008 (HY000): Can't drop database 'employees'; database doesn't exist
mysql> drop table employees;
Query OK, 0 rows affected (0.03 sec)

mysql> drop database mydb;
Query OK, 1 row affected (0.04 sec)

mysql> create database mydb;
Query OK, 1 row affected (0.01 sec)

mysql> create table employee(EmpID int, EmpName varchar(100), Email varchar(50), Age int, City varchar(10));
ERROR 1046 (3D000): No database selected
mysql> use mydb;
Database changed
mysql> create table employee(EmpID int, EmpName varchar(100), Email varchar(50), Age int, City varchar(10));
Query OK, 0 rows affected (0.03 sec)

mysql> describe employee
    -> ;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EmpID   | int          | YES  |     | NULL    |       |
| EmpName | varchar(100) | YES  |     | NULL    |       |
| Email   | varchar(50)  | YES  |     | NULL    |       |
| Age     | int          | YES  |     | NULL    |       |
| City    | varchar(10)  | YES  |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
5 rows in set (0.01 sec)

mysql> alter table employee add constraints pk_employee primary key(EmpID)
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'pk_employee primary key(EmpID)' at line 1
mysql> alter table employee add constraints pk_employee primary key(EmpID);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'pk_employee primary key(EmpID)' at line 1
mysql> alter table employee add constraint pk_employee primary key(EmpID);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employee;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EmpID   | int          | NO   | PRI | NULL    |       |
| EmpName | varchar(100) | YES  |     | NULL    |       |
| Email   | varchar(50)  | YES  |     | NULL    |       |
| Age     | int          | YES  |     | NULL    |       |
| City    | varchar(10)  | YES  |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table employee add constraint uq_Email unique(Email);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employee;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EmpID   | int          | NO   | PRI | NULL    |       |
| EmpName | varchar(100) | YES  |     | NULL    |       |
| Email   | varchar(50)  | YES  | UNI | NULL    |       |
| Age     | int          | YES  |     | NULL    |       |
| City    | varchar(10)  | YES  |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table employee add constraint chk_employee check(age >= 18);
Query OK, 0 rows affected (0.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employee;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EmpID   | int          | NO   | PRI | NULL    |       |
| EmpName | varchar(100) | YES  |     | NULL    |       |
| Email   | varchar(50)  | YES  | UNI | NULL    |       |
| Age     | int          | YES  |     | NULL    |       |
| City    | varchar(10)  | YES  |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> insert into employee values(101, "Krupesh", "krupesh@gmail.com", 21, "Ahmedabad");
Query OK, 1 row affected (0.01 sec)

mysql> select * from employee;
+-------+---------+-------------------+------+-----------+
| EmpID | EmpName | Email             | Age  | City      |
+-------+---------+-------------------+------+-----------+
|   101 | Krupesh | krupesh@gmail.com |   21 | Ahmedabad |
+-------+---------+-------------------+------+-----------+
1 row in set (0.00 sec)

mysql> insert into employee values(102, "Hardik", "hardik@gmail.com", 14, "Vadodara");
ERROR 3819 (HY000): Check constraint 'chk_employee' is violated.
mysql> alter table employee alter city set defult 'Mumbai';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'defult 'Mumbai'' at line 1
mysql> alter table employee alter City set defult 'Mumbai';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'defult 'Mumbai'' at line 1
mysql> alter table employee alter City set default 'Mumbai';
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employee;
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| EmpID   | int          | NO   | PRI | NULL    |       |
| EmpName | varchar(100) | YES  |     | NULL    |       |
| Email   | varchar(50)  | YES  | UNI | NULL    |       |
| Age     | int          | YES  |     | NULL    |       |
| City    | varchar(10)  | YES  |     | Mumbai  |       |
+---------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> insert into employee(EmpID, EmpName, Email, Age) values(103, "Rudra", "rudra@gmail.com", 23);
Query OK, 1 row affected (0.01 sec)

mysql> select * from employee;
+-------+---------+-------------------+------+-----------+
| EmpID | EmpName | Email             | Age  | City      |
+-------+---------+-------------------+------+-----------+
|   101 | Krupesh | krupesh@gmail.com |   21 | Ahmedabad |
|   103 | Rudra   | rudra@gmail.com   |   23 | Mumbai    |
+-------+---------+-------------------+------+-----------+
2 rows in set (0.00 sec)


DATE :-  20-05-2026

Enter password: ******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.45 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mydb;
Database changed
mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
+----------------+
1 row in set (0.02 sec)

mysql> select * from employee;
+-------+---------+-------------------+------+-----------+
| EmpID | EmpName | Email             | Age  | City      |
+-------+---------+-------------------+------+-----------+
|   101 | Krupesh | krupesh@gmail.com |   21 | Ahmedabad |
|   103 | Rudra   | rudra@gmail.com   |   23 | Mumbai    |
+-------+---------+-------------------+------+-----------+
2 rows in set (0.03 sec)

mysql> create table students(student_id int primary key auto_increment, student_name varchar(50));
Query OK, 0 rows affected (0.07 sec)

mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
| students       |
+----------------+
2 rows in set (0.00 sec)

mysql> create table subjects(subject_id primary key auto_increment, subject_name varchar(100));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'primary key auto_increment, subject_name varchar(100))' at line 1
mysql> create table subjects(subject_id primary key auto_increment, subject_name varchar(100));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'primary key auto_increment, subject_name varchar(100))' at line 1
mysql> create table subjects(subject_id int primary key auto_increment, subject_name varchar(100));
Query OK, 0 rows affected (0.03 sec)

mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
| students       |
| subjects       |
+----------------+
3 rows in set (0.00 sec)

mysql> create table marks(mark_id int primary key auto_increment, student_id int, score int, test_date date, foreign key(student_id) references students(student_id));
Query OK, 0 rows affected (0.07 sec)

mysql> alter table constraint fk_subjects foreign key(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'constraint fk_subjects foreign key(subject_id)' at line 1
mysql> alter table add constraint fk_subjects foreign key(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'add constraint fk_subjects foreign key(subject_id)' at line 1
mysql> alter table add constraint fk_subjects foreign key(subject_id) references subjects(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'add constraint fk_subjects foreign key(subject_id) references subjects(subject_i' at line 1
mysql> alter table marks add constraint fk_subjects foreign key(subject_id) references subjects(subject_id);
ERROR 1072 (42000): Key column 'subject_id' doesn't exist in table
mysql> alter table marks add constraint foreign key(subject_id) references subjects(subject_id);
ERROR 1072 (42000): Key column 'subject_id' doesn't exist in table
mysql> alter table marks add column subject_id int after student_id;
Query OK, 0 rows affected (0.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks add constraint foreign key(subject_id) references subjects(subject_id);
Query OK, 0 rows affected (0.14 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks drop column student_id;
ERROR 1828 (HY000): Cannot drop column 'student_id': needed in a foreign key constraint 'marks_ibfk_1'
mysql> alter table students drop column student_id;
ERROR 1829 (HY000): Cannot drop column 'student_id': needed in a foreign key constraint 'marks_ibfk_1' of table 'marks'
mysql> alter table marks drop column foreign key(marks_ibfk_1) student_id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(marks_ibfk_1) student_id' at line 1
mysql> alter table marks drop constrait foreign key(marks_ibfk_1) student_id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(marks_ibfk_1) student_id' at line 1
mysql> alter table marks drop constrait foreign key;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key' at line 1
mysql> alter table marks drop constrait foreign key(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(subject_id)' at line 1
mysql> alter table marks drop constrait foreign key(subject_id) references subjects;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(subject_id) references subjects' at line 1
mysql>
mysql>
mysql> alter table marks drop column student_id;
ERROR 1828 (HY000): Cannot drop column 'student_id': needed in a foreign key constraint 'marks_ibfk_1'
mysql> alter table marks drop column subject_id;
ERROR 1828 (HY000): Cannot drop column 'subject_id': needed in a foreign key constraint 'marks_ibfk_2'
mysql> alter table marks drop foreign key marks_ibfk_1;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks drop foreign key marks_ibfk_2;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks drop column student_id;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks drop column subject_id;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe marks;
+-----------+------+------+-----+---------+----------------+
| Field     | Type | Null | Key | Default | Extra          |
+-----------+------+------+-----+---------+----------------+
| mark_id   | int  | NO   | PRI | NULL    | auto_increment |
| score     | int  | YES  |     | NULL    |                |
| test_date | date | YES  |     | NULL    |                |
+-----------+------+------+-----+---------+----------------+
3 rows in set (0.01 sec)


DATE :- 21-05-2026

mysql> create database ECommerce;
Query OK, 1 row affected (0.01 sec)

mysql> use ECommerce;
Database changed
mysql> use mdb;
Database changed
mysql> show tables;
+---------------+
| Tables_in_mdb |
+---------------+
| employee      |
| student       |
+---------------+
2 rows in set (0.05 sec)

mysql> use mydb;
Database changed
mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| employee       |
| marks          |
| students       |
| subjects       |
+----------------+
4 rows in set (0.00 sec)

mysql> drop table employee;
Query OK, 0 rows affected (0.04 sec)

mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| marks          |
| students       |
| subjects       |
+----------------+
3 rows in set (0.00 sec)

mysql> describe students;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| student_id   | int         | NO   | PRI | NULL    | auto_increment |
| student_name | varchar(50) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
2 rows in set (0.01 sec)

mysql> insert into students (student_name) values("Divya");
Query OK, 1 row affected (0.01 sec)

mysql> insert into students (student_name) values("Sakshi"),("Vidhi"),("Nandini"),("Rudra"),("Krupesh"),("Parth"),("Hardik");
Query OK, 7 rows affected (0.01 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql> describe subjects;
+--------------+--------------+------+-----+---------+----------------+
| Field        | Type         | Null | Key | Default | Extra          |
+--------------+--------------+------+-----+---------+----------------+
| subject_id   | int          | NO   | PRI | NULL    | auto_increment |
| subject_name | varchar(100) | YES  |     | NULL    |                |
+--------------+--------------+------+-----+---------+----------------+
2 rows in set (0.01 sec)

mysql> insert into subjects (subject_name) values("Maths"),("Science"),("English"),("Accounts"),("S.S.");
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> describe marks;
+-----------+------+------+-----+---------+----------------+
| Field     | Type | Null | Key | Default | Extra          |
+-----------+------+------+-----+---------+----------------+
| mark_id   | int  | NO   | PRI | NULL    | auto_increment |
| score     | int  | YES  |     | NULL    |                |
| test_date | date | YES  |     | NULL    |                |
+-----------+------+------+-----+---------+----------------+
3 rows in set (0.00 sec)

mysql> alter table marks add constraint fk_student_id foreign key students(student_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> alter table marks add constraint fk_student_id foreign key(student_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> alter table marks add constraint fk_students foreign key(student_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> alter table marks add column student_id int;
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks add column subject_id int;
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks add constraint fk_students foreign key(student_id) references students(student_id);
Query OK, 0 rows affected (0.11 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table marks add constraint fk_subjects foreign key(subject_id) refernces subjects(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'refernces subjects(subject_id)' at line 1
mysql> alter table marks add constraint fk_subjects foreign key(subject_id) refernces subjects(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'refernces subjects(subject_id)' at line 1
mysql> alter table marks add constraint fk_subject foreign key(subject_id) refernces subjects(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'refernces subjects(subject_id)' at line 1
mysql> alter table marks add constraint frk_subjects foreign key(subject_id) refernces subjects(subject_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'refernces subjects(subject_id)' at line 1
mysql> alter table marks add constraint frk_subjects foreign key(subject_id) references subjects(subject_id);
Query OK, 0 rows affected (0.12 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe marks;
+------------+------+------+-----+---------+----------------+
| Field      | Type | Null | Key | Default | Extra          |
+------------+------+------+-----+---------+----------------+
| mark_id    | int  | NO   | PRI | NULL    | auto_increment |
| score      | int  | YES  |     | NULL    |                |
| test_date  | date | YES  |     | NULL    |                |
| student_id | int  | YES  | MUL | NULL    |                |
| subject_id | int  | YES  | MUL | NULL    |                |
+------------+------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> select * from students;
+------------+--------------+
| student_id | student_name |
+------------+--------------+
|          1 | Divya        |
|          2 | Sakshi       |
|          3 | Vidhi        |
|          4 | Nandini      |
|          5 | Rudra        |
|          6 | Krupesh      |
|          7 | Parth        |
|          8 | Hardik       |
+------------+--------------+
8 rows in set (0.00 sec)

mysql> select * from subjects;
+------------+--------------+
| subject_id | subject_name |
+------------+--------------+
|          1 | Maths        |
|          2 | Science      |
|          3 | English      |
|          4 | Accounts     |
|          5 | S.S.         |
+------------+--------------+
5 rows in set (0.00 sec)

mysql> insert into marks (score, test_date, student_id, subject_id) values(87, '2026-03-01', 1, 1), (75, '2026-03-01', 1, 2), (70, '2026-03-01', 1, 3),(71, '2026-03-01', 1, 4), (65, '2026-03-01', 1, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> select * from marks;
+---------+-------+------------+------------+------------+
| mark_id | score | test_date  | student_id | subject_id |
+---------+-------+------------+------------+------------+
|       1 |    87 | 2026-03-01 |          1 |          1 |
|       2 |    75 | 2026-03-01 |          1 |          2 |
|       3 |    70 | 2026-03-01 |          1 |          3 |
|       4 |    71 | 2026-03-01 |          1 |          4 |
|       5 |    65 | 2026-03-01 |          1 |          5 |
+---------+-------+------------+------------+------------+
5 rows in set (0.00 sec)

mysql> delete from students where student_id >6;
Query OK, 2 rows affected (0.01 sec)

mysql> select * from students;
+------------+--------------+
| student_id | student_name |
+------------+--------------+
|          1 | Divya        |
|          2 | Sakshi       |
|          3 | Vidhi        |
|          4 | Nandini      |
|          5 | Rudra        |
|          6 | Krupesh      |
+------------+--------------+
6 rows in set (0.00 sec)

mysql> insert into marks (score, test_date, student_id, subject_id) values(90, '2026-03-01', 2, 1), (68, '2026-03-01', 2, 2), (85, '2026-03-01', 2, 3),(84, '2026-03-01', 2, 4), (72, '2026-03-01', 2, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> insert into marks (score, test_date, student_id, subject_id) values(67, '2026-03-01', 3, 1), (83, '2026-03-01', 3, 2), (72, '2026-03-01', 3, 3),(69, '2026-03-01', 3, 4), (86, '2026-03-01', 3, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> insert into marks (score, test_date, student_id, subject_id) values(88, '2026-03-01', 4, 1), (76, '2026-03-01', 4, 2), (67, '2026-03-01', 4, 3),(92, '2026-03-01', 4, 4), (91, '2026-03-01', 4, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> insert into marks (score, test_date, student_id, subject_id) values(94, '2026-03-01', 5, 1), (85, '2026-03-01', 5, 2), (90, '2026-03-01', 5, 3),(88, '2026-03-01', 5, 4), (70, '2026-03-01', 5, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> insert into marks (score, test_date, student_id, subject_id) values(89, '2026-03-01', 6, 1), (73, '2026-03-01', 6, 2), (68, '2026-03-01', 6, 3),(74, '2026-03-01', 6, 4), (77, '2026-03-01', 6, 5);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> update marks set student_id primary key where student_id = 4;   


DATE :-  22-05-2026

mysql> drop database mdb;
Query OK, 2 rows affected (0.08 sec)

mysql> create database mdb;
Query OK, 1 row affected (0.01 sec)

mysql> create database if not exists mdb;
Query OK, 1 row affected, 1 warning (0.04 sec)

mysql> create database if not exists ndb;
Query OK, 1 row affected (0.04 sec)

mysql> use mdb;
Database changed
mysql> create table departments(dept_id primary key, dept_name varchar(50));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'primary key, dept_name varchar(50))' at line 1
mysql> create table departments(dept_id int primary key, dept_name varchar(50));
Query OK, 0 rows affected (0.03 sec)

mysql> create table cities(city_id int primary key, city_name varchar(50));
Query OK, 0 rows affected (0.03 sec)

mysql> create table employees(emp_id int primary key, emp_name varchar(100), dept_id int, city_id int, foreign key(dept_id) references departments(dept_id), foreign key(city_id) references cities(city_id));
Query OK, 0 rows affected (0.07 sec)

mysql> describe departments;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| dept_id   | int         | NO   | PRI | NULL    |       |
| dept_name | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
2 rows in set (0.03 sec)

mysql> describe cities;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| city_id   | int         | NO   | PRI | NULL    |       |
| city_name | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> describe employees;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| emp_id   | int          | NO   | PRI | NULL    |       |
| emp_name | varchar(100) | YES  |     | NULL    |       |
| dept_id  | int          | YES  | MUL | NULL    |       |
| city_id  | int          | YES  | MUL | NULL    |       |
+----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> insert into departments(dept_id, dept_name) values
    -> (1, "Engineering"),
    -> (2, "HR"),
    -> (3, "Finance"),
    -> (4, "Marketing");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> insert into cities(city_id, city_name) values
    -> (101, "Mumbai"),
    -> (102, "Delhi"),
    -> (103, "Bangalore"),
    -> (104, "Pune");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> insert into employees(emp_id, emp_name, dept_id, city_id) values
    -> (1, "Arav", 1, 101),
    -> (2, "Priya", 2, 102),
    -> (3, "Rohan", 1, 103),
    -> (4, "Ananya", 3, 104),
    -> (5, "Vikram", Null, 104),
    -> (6, "Neha", 2, 101),
    -> (7, "Aditya", 1, Null),
    -> (8, "Kavya", 4, 103),
    -> (9, "Siddharth", 3, 102),
    -> (10, "Pooja", Null, Null);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> select * from departments;
+---------+-------------+
| dept_id | dept_name   |
+---------+-------------+
|       1 | Engineering |
|       2 | HR          |
|       3 | Finance     |
|       4 | Marketing   |
+---------+-------------+
4 rows in set (0.00 sec)

mysql> select * from cities;
+---------+-----------+
| city_id | city_name |
+---------+-----------+
|     101 | Mumbai    |
|     102 | Delhi     |
|     103 | Bangalore |
|     104 | Pune      |
+---------+-----------+
4 rows in set (0.00 sec)

mysql> select * from employees;
+--------+-----------+---------+---------+
| emp_id | emp_name  | dept_id | city_id |
+--------+-----------+---------+---------+
|      1 | Arav      |       1 |     101 |
|      2 | Priya     |       2 |     102 |
|      3 | Rohan     |       1 |     103 |
|      4 | Ananya    |       3 |     104 |
|      5 | Vikram    |    NULL |     104 |
|      6 | Neha      |       2 |     101 |
|      7 | Aditya    |       1 |    NULL |
|      8 | Kavya     |       4 |     103 |
|      9 | Siddharth |       3 |     102 |
|     10 | Pooja     |    NULL |    NULL |
+--------+-----------+---------+---------+
10 rows in set (0.00 sec)

mysql> select emp.emp_name, dept.dept_name from employees emp join departments dept
    -> on emp.dept.id = dept.dept.id;
ERROR 1054 (42S22): Unknown column 'emp.dept.id' in 'on clause'
mysql> select emp.emp_name, dept.dept_name from employees emp join departments dept on emp.dept_id = dept.dept_id;
+-----------+-------------+
| emp_name  | dept_name   |
+-----------+-------------+
| Arav      | Engineering |
| Rohan     | Engineering |
| Aditya    | Engineering |
| Priya     | HR          |
| Neha      | HR          |
| Ananya    | Finance     |
| Siddharth | Finance     |
| Kavya     | Marketing   |
+-----------+-------------+
8 rows in set (0.00 sec)

mysql> select emp.emp_name, dept.dept_name from employees emp join departments dept on emp.dept_id = dept.dept_id;
+-----------+-------------+
| emp_name  | dept_name   |
+-----------+-------------+
| Arav      | Engineering |
| Rohan     | Engineering |
| Aditya    | Engineering |
| Priya     | HR          |
| Neha      | HR          |
| Ananya    | Finance     |
| Siddharth | Finance     |
| Kavya     | Marketing   |
+-----------+-------------+
8 rows in set (0.00 sec)

 ysql> select emp.emp_name, dept.dept_name from employees emp inner join departments dept on emp.dept_id = dept.dept_id;
+-----------+-------------+
| emp_name  | dept_name   |
+-----------+-------------+
| Arav      | Engineering |
| Rohan     | Engineering |
| Aditya    | Engineering |
| Priya     | HR          |
| Neha      | HR          |
| Ananya    | Finance     |
| Siddharth | Finance     |
| Kavya     | Marketing   |
+-----------+-------------+
8 rows in set (0.00 sec)

mysql> select emp.emp_name, dept.dept_name from employees emp left join departments dept on emp.dept_id = dept.dept_id;
+-----------+-------------+
| emp_name  | dept_name   |
+-----------+-------------+
| Arav      | Engineering |
| Priya     | HR          |
| Rohan     | Engineering |
| Ananya    | Finance     |
| Vikram    | NULL        |
| Neha      | HR          |
| Aditya    | Engineering |
| Kavya     | Marketing   |
| Siddharth | Finance     |
| Pooja     | NULL        |
+-----------+-------------+
10 rows in set (0.00 sec)

 ysql> select emp.emp_name, dept.dept_name from employees emp right join departments dept on emp.dept_id = dept.dept_id;
+-----------+-------------+
| emp_name  | dept_name   |
+-----------+-------------+
| Arav      | Engineering |
| Rohan     | Engineering |
| Aditya    | Engineering |
| Priya     | HR          |
| Neha      | HR          |
| Ananya    | Finance     |
| Siddharth | Finance     |
| Kavya     | Marketing   |
+-----------+-------------+
8 rows in set (0.00 sec)


DATE :-  23-05-2026

mysql> create database demodb;
Query OK, 1 row affected (0.06 sec)

mysql> use demodb;
Database changed
mysql> create table employee(empid int primary key, empname varchar(50), age int, salary float);
Query OK, 0 rows affected (0.07 sec)

mysql> show tables;
+------------------+
| Tables_in_demodb |
+------------------+
| employee         |
+------------------+
1 row in set (0.03 sec)

mysql> rename table employee to employees;
Query OK, 0 rows affected (0.03 sec)

mysql> alter table employees add column doj datetime default current_timestamp;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employees;
+---------+-------------+------+-----+-------------------+-------------------+
| Field   | Type        | Null | Key | Default           | Extra             |
+---------+-------------+------+-----+-------------------+-------------------+
| empid   | int         | NO   | PRI | NULL              |                   |
| empname | varchar(50) | YES  |     | NULL              |                   |
| age     | int         | YES  |     | NULL              |                   |
| salary  | float       | YES  |     | NULL              |                   |
| doj     | datetime    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------+-------------+------+-----+-------------------+-------------------+
5 rows in set (0.01 sec)

mysql> alter table employees modify column empid int auto_increment;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> insert into employees(empname, age, salary) values("Krupesh", 21, 26000);
Query OK, 1 row affected (0.01 sec)

mysql> select * from employees;
+-------+---------+------+--------+---------------------+
| empid | empname | age  | salary | doj                 |
+-------+---------+------+--------+---------------------+
|     1 | Krupesh |   21 |  26000 | 2026-05-23 11:33:53 |
+-------+---------+------+--------+---------------------+
1 row in set (0.00 sec)

mysql> alter table employees add column DOB date, add column Mobile int, add column email varchar(50) unique;
Query OK, 0 rows affected (0.15 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe employees;
+---------+-------------+------+-----+-------------------+-------------------+
| Field   | Type        | Null | Key | Default           | Extra             |
+---------+-------------+------+-----+-------------------+-------------------+
| empid   | int         | NO   | PRI | NULL              | auto_increment    |
| empname | varchar(50) | YES  |     | NULL              |                   |
| age     | int         | YES  |     | NULL              |                   |
| salary  | float       | YES  |     | NULL              |                   |
| doj     | datetime    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| DOB     | date        | YES  |     | NULL              |                   |
| Mobile  | int         | YES  |     | NULL              |                   |
| email   | varchar(50) | YES  | UNI | NULL              |                   |
+---------+-------------+------+-----+-------------------+-------------------+
8 rows in set (0.00 sec)

mysql> alter table employees drop column DOB, drop column Mobile, drop column doj;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> decribe employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'decribe employees' at line 1
mysql> describe employees;
+---------+-------------+------+-----+---------+----------------+
| Field   | Type        | Null | Key | Default | Extra          |
+---------+-------------+------+-----+---------+----------------+
| empid   | int         | NO   | PRI | NULL    | auto_increment |
| empname | varchar(50) | YES  |     | NULL    |                |
| age     | int         | YES  |     | NULL    |                |
| salary  | float       | YES  |     | NULL    |                |
| email   | varchar(50) | YES  | UNI | NULL    |                |
+---------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)



DATE :- 25-05-2026

mysql> select * from employees;
+------------+--------------+-----------+--------+
| EmployeeID | EmpName      | City      | DeptID |
+------------+--------------+-----------+--------+
|        101 | Aarav Sharma | Delhi     |     10 |
|        102 | Priya Patel  | Mumbai    |     20 |
|        103 | Amit Mishra  | Bengaluru |     10 |
|        104 | Ananya Iyer  | Chennai   |     30 |
|        105 | Rohan Das    | Kolkata   |   NULL |
+------------+--------------+-----------+--------+
5 rows in set (0.03 sec)

mysql> select E1.EmployeeID, E2.deptID from employees E1 join departments E2 on E1.EmployeeID = E2.DeptID;
ERROR 1054 (42S22): Unknown column 'E2.deptID' in 'field list'
mysql> select E1.EmployeeID, E2.City from employees E1 join departments E2 on E1.EmployeeID = E2.DeptID;
ERROR 1054 (42S22): Unknown column 'E2.City' in 'field list'
mysql> select E1.EmployeeID, E2.City from employees E1 join departments E2 on E1.EmployeeID = E2.DeptID;
ERROR 1054 (42S22): Unknown column 'E2.City' in 'field list'
mysql> use mdb;
Database changed
mysql> show tables;
+---------------+
| Tables_in_mdb |
+---------------+
| cities        |
| departments   |
| employees     |
+---------------+
3 rows in set (0.00 sec)

mysql> use mydb;
Database changed
mysql> show mydb;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mydb' at line 1
mysql> show tables'
    '> ;
    '> ^C
mysql> show tables;
+----------------+
| Tables_in_mydb |
+----------------+
| marks          |
| students       |
| subjects       |
+----------------+
3 rows in set (0.00 sec)

mysql> create table employees(emp_id primary key, emp_name varchar(50), department varchar(56), salary int, manager_id int, city varchar(50));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'primary key, emp_name varchar(50), department varchar(56), salary int, manager_i' at line 1
mysql> create table employees(emp_id int primary key, emp_name varchar(50), department varchar(56), salary int, manager_id int, city varchar(50));
Query OK, 0 rows affected (0.04 sec)

mysql> describe employees;
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| emp_id     | int         | NO   | PRI | NULL    |       |
| emp_name   | varchar(50) | YES  |     | NULL    |       |
| department | varchar(56) | YES  |     | NULL    |       |
| salary     | int         | YES  |     | NULL    |       |
| manager_id | int         | YES  |     | NULL    |       |
| city       | varchar(50) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
6 rows in set (0.01 sec)

mysql> insert into employees(emp_id, emp_name, department, salary, manager_id, city) values
    -> (101, "Arvind Sharma", "Executive", 250000, Null, "Mumbai"),
    -> (102, "Priya patel", "IT", 120000, 101 "Bangalore"),
    -> (103, "Rajesh Kumar", "IT", 115000, 101, "Bangalore"),
    -> (104, "Sunita Rao", "HR", 90000, 101, "Delhi"),
    -> (105, "Amit Mishra", "IT", 85000, 102, "Mumbai"),
    -> (106, "Deepika Padukone", "IT", 85000, 102, "Bangalore"),
    -> (107, "Vijay Malya", "Finance", 99000, 101, "Delhi"),
    -> (108, "Ananya Iyer", "HR", 60000, 104, "Delhi"),
    -> (109, "Rahul Dravid", "Finance", 95000, 107, "Mumbai"),
    -> (110, "Sanjay Dutt", "IT", 85000, 103, "Pune");
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"Bangalore"),
(103, "Rajesh Kumar", "IT", 115000, 101, "Bangalore"),
(104, "Suni' at line 3
mysql> insert into employees(emp_id, emp_name, department, salary, manager_id, city) values
    -> (101, "Arvind Sharma", "Executive", 250000, Null, "Mumbai"),
    -> (102, "Priya patel", "IT", 120000, 101, "Bangalore"),
    -> (103, "Rajesh Kumar", "IT", 115000, 101, "Bangalore"),
    -> (104, "Sunita Rao", "HR", 90000, 101, "Delhi"),
    -> (105, "Amit Mishra", "IT", 85000, 102, "Mumbai"),
    -> (106, "Deepika Padukone", "IT", 85000, 102, "Bangalore"),
    -> (107, "Vijay Malya", "Finance", 99000, 101, "Delhi"),
    -> (108, "Ananya Iyer", "HR", 60000, 104, "Delhi"),
    -> (109, "Rahul Dravid", "Finance", 95000, 107, "Mumbai"),
    -> (110, "Sanjay Dutt", "IT", 85000, 103, "Pune");
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> select * from employees;
+--------+------------------+------------+--------+------------+-----------+
| emp_id | emp_name         | department | salary | manager_id | city      |
+--------+------------------+------------+--------+------------+-----------+
|    101 | Arvind Sharma    | Executive  | 250000 |       NULL | Mumbai    |
|    102 | Priya patel      | IT         | 120000 |        101 | Bangalore |
|    103 | Rajesh Kumar     | IT         | 115000 |        101 | Bangalore |
|    104 | Sunita Rao       | HR         |  90000 |        101 | Delhi     |
|    105 | Amit Mishra      | IT         |  85000 |        102 | Mumbai    |
|    106 | Deepika Padukone | IT         |  85000 |        102 | Bangalore |
|    107 | Vijay Malya      | Finance    |  99000 |        101 | Delhi     |
|    108 | Ananya Iyer      | HR         |  60000 |        104 | Delhi     |
|    109 | Rahul Dravid     | Finance    |  95000 |        107 | Mumbai    |
|    110 | Sanjay Dutt      | IT         |  85000 |        103 | Pune      |
+--------+------------------+------------+--------+------------+-----------+
10 rows in set (0.00 sec)

mysql> select m.emp_name as 'Manager Name', count(e.emp_id) as team_size from employees e inner join employees m on m.manager_id = e.emp_id group by m.emp_name having team_size > 2;
Empty set (0.00 sec)

mysql> select m.emp_name as 'Manager Name', count(e.emp_id) as team_size from employees e inner join employees m on e.manager_id = m.emp_id group by m.emp_name having team_size > 2;
+---------------+-----------+
| Manager Name  | team_size |
+---------------+-----------+
| Arvind Sharma |         4 |
+---------------+-----------+
1 row in set (0.00 sec)

mysql> select m.emp_name as 'Manager Name', count(e.emp_id) as team_size from employees e inner join employees m on e.manager_id = m.emp_id group by m.emp_name having team_size >= 2;
+---------------+-----------+
| Manager Name  | team_size |
+---------------+-----------+
| Arvind Sharma |         4 |
| Priya patel   |         2 |
+---------------+-----------+
2 rows in set (0.00 sec)

mysql> select m.emp_name as 'Manager Name', count(e.emp_id) as team_size from employees e inner join employees m on e.manager_id = m.emp_id group by m.emp_name having team_size > 0;
+---------------+-----------+
| Manager Name  | team_size |
+---------------+-----------+
| Arvind Sharma |         4 |
| Priya patel   |         2 |
| Sunita Rao    |         1 |
| Vijay Malya   |         1 |
| Rajesh Kumar  |         1 |
+---------------+-----------+
5 rows in set (0.00 sec)


mysql> select e1.department, e1.salary, count(*) as team_data from employees e1 inner join employees e2 on e1.department = e2.department and e1.salary = e2.salary and e1.emp_id <> e2.emp_id
    -> group by e1.department, e1.salary having team_data > 1;
+------------+--------+-----------+
| department | salary | team_data |
+------------+--------+-----------+
| IT         |  85000 |         6 |
+------------+--------+-----------+
1 row in set (0.01 sec)