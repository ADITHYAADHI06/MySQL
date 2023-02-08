
# MySQL SQL
## 1. The MySQL SELECT Statement 

The SELECT statement is used to select data from a database.

The data returned is stored in a result table, called the result-set. 

Example :
```bash
   SELECT CustomerName, City, Country FROM Customers;
```


## 2. What is MySQL WHERE Clause ?

The WHERE clause is used to filter records.

Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!
 

Example :
```bash
   SQL statement selects all the customers from "Mexico"
   SELECT * FROM Customers
   WHERE Country = 'Mexico';
```


##  3. Operators in The WHERE Clause ?

| Parameter   | Description                |
| :--------   | :------------------------- |
| `=`   |  Equal |
| `>`   |  Greater than	 |
| `<`   |  Less than	 |
| `>=`   |  Greater than or equal	 |
| `<=`   |   Less than or equal	 |
| `<>`   |  Not equal ****Note**** : In some versions of SQL this operator may be written as != |
| `BETWEEN	`   |   Between a certain range	 |
| `LIKE`   |   Search for a pattern	
 |
| `IN`   |   To specify multiple possible values for a column	 |


Example : LIKE
```bash
 SELECT * FROM Customers
 WHERE City LIKE 's%'; 
```
Example : BETWEEN
```bash
 SELECT * FROM Products
 WHERE Price BETWEEN 50 AND 60;
```
Example : IN
```bash
 1. SELECT * FROM Customers
    WHERE City IN ('Paris','London');

 2. find names of employee who sold 30000 or more to single client 
    Select emp.firstname from emp where emp.emp_id IN
    (Select works_with.emp_id from work_with where works_with.total_sales >30000 ); 
```

## 2. What is MySQL WHERE Clause ?

The WHERE clause is used to filter records.

Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!
 

Example :
```bash
   SQL statement selects all the customers from "Mexico"
   SELECT * FROM Customers
   WHERE Country = 'Mexico';
```


# MySQL AND, OR and NOT Operators

- The WHERE clause can be combined with AND, OR, and NOT operators.
- The AND and OR operators are used to filter records based on more than one condition:
- The NOT operator displays a record if the condition(s) is NOT TRUE.

Example : AND

    SELECT * FROM Customers
    WHERE Country = 'Germany' AND City = 'Berlin';
Example : OR

    SELECT * FROM Customers
    WHERE City = 'Berlin' OR City = 'Stuttgart';
Example : NOT

    SELECT * FROM Customers
    WHERE NOT Country = 'Germany';

 ## Combining AND, OR and NOT

 Example : combined

    SELECT * FROM Customers
    WHERE Country = 'Germany' AND (City = 'Berlin' OR City = 'Stuttgart');

selects all fields from "Customers" where country is NOT "Germany" and NOT "USA":

    SELECT * FROM Customers
    WHERE NOT Country = 'Germany' AND NOT Country = 'USA';

# ORDER BY Keyword

 ###  ORDER BY keyword is used to ****sort the result-set**** in ascending or descending order.
- ascending order by default ~ ASC
- descending order ~ DESC

Example : 

    SELECT * FROM Customers   
    ORDER BY Country DESC;
    
## ORDER BY Several Columns 

 ###  it orders by Country, but if some rows have the same Country, it orders them by CustomerName.


Example : 

    SELECT * FROM Customers
    ORDER BY Country, CustomerName;

# MySQL INSERT INTO Statement

The INSERT INTO statement is used to insert new records in a table.

Example : 

    INSERT INTO Customers VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21',  'Stavanger', '4006', 'Norway');

## What is a NULL Value?
A NULL value is different from a zero value. 

A field with a NULL value is one that has been left blank during record creation

## How to Test for NULL Values?

use the IS NULL and IS NOT NULL operators.

## The IS NULL Operator
The IS NULL operator is used to test for empty values


