# [SQL Interview](https://www.linkedin.com/learning/nail-your-sql-interview/build-confidence-for-your-sql-interview?autoplay=true)

## Introduction
### Common SQL terminology 
**Q1.** Why and how might we use an alias?     
A: We can use alias on columns as well as tables. Aliases can save us some typing as well as produce new columns that show the 
output of an aggregate function for example. Aliases for the table do not usually use *AS*.


**Q2.** What are the three types of SQL relationships?    
1. One to one
2. One to many
3. Many to many 

**Q3.** What is the difference between UNION and UNION ALL?
* **UNION:** same number of columns, compatible data types, columns must be in the same order
* **UNION ALL:** preserve duplicates


**Q4.** How many *main clauses* are in a SQL query and what are they?
**Main clauses(6)**: ```SELECT, FROM, WHERE, ORDER BY, HAVING, GROUP BY```

**Q5.** What is the *order of execution* for a SELECT statement?
* ```FROM```: where data is coming from
* ```WHERE```: what is returned
* ```GROUP BY```: how data is grouped
* ```HAVING```: which characteristics 
* ```SELECT```: what data is returned 
* ```ORDER BY```: how data is sorted 

**Q6.** What is a *constraint*? Give an example.   
* Controls what type of data is allowed into a table. 
* Examples: Primary keys, Foreign keys, UNIQUE, NOT NULL

**Q7.** Name five aggregate functions. What do they do?
1. ```SUM()```: returns a total
2. ```AVG()```: returns the average of numbers
3. ```MIN()```: returns the lowest or oldest(date)
4. ```MAX()```: returns the highest or newest(date)
5. ```COUNT()```: returns the number of values 

**Q8.** What are the five *types* of SQL commands?   
1. Data definition language 
2. Data manipulation language 
3. Data control language 
4. Transaction control language 
5. Data query language 

## Data Definition Language Review
### Create and seed a table with data 
```mysql
--Creating a employee info table
--Keywords:
--CREATE Table table_nm
CREATE Table employee_info(
id int not null identity(1,1) primary key,
firstname nvarchar(75),
lastname nvarchar(75),
email nvarchar(125)
)
--table_nm(col_names?, null values allowed?, constraints?(PK?), datatypes?)

--INSERT INTO Table_nm
INSERT INTO employee_info(
firstname, lastname, email
)
--VALUES
VALUES('John','Arthur','123ghj@gmail.com'),
('Addison','Barclay','345@gmail.com'),
('Betty','Barclay','456@gmail.com'),
('Maggie','Sheffield','567@gmail.com'),
('April','James','678@gmail.com')

Select * from employee_info
```

### Modify existing table with ALTER 
ALTER Command:    
Changes the structure of a table -- Data type, column names, ADD/DROP columns 
```mysql
--ALTER Command:
--Changes the structure of the table:
	--Datatypes
	--Column names (exception: stored procedure for MSSQL Server)
	--ADD/DROP columns

select * from employee_info
--using employee info table
--ALTER table
ALTER Table employee_info
--DROP email column
--query table
select * from employee_info

--ALTER table
ALTER table employee_info
--ADD  country col int datatype
--query table
select * from employee_info

--ALTER TABLE
ALTER table employee_info
--ALTER COL country
--query table
select * from employee_info
```
### TRUNCATE and DROP
* TRUNCATE: delete data from a table, while retaining the table's structure. Column headings and constraints are retained within the table. 
* DROP: remove a table definition and all the data, indexes, triggers, constraints and permission specification 
* DELETE: delete existing records in a table 

## Data Query Language and Logical Operators
### LIKE, IN, BETWEEN
1. ```BETWEEN```: returns data within a range of values 
2. ```IN```: returns data within a list of values   
3. ```LIKE```: returns data similar to a given pattern(use of wildcards is common)

### COALESCE


## Data Manipulation Language 
### UPDATE or ALTER 

### Delete data using transactions 

## Transaction Control Language 



