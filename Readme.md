
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

# MySQL UPDATE Statement

UPDATE statement is used to modify the existing records in a table.

Example : 
updates the first customer (CustomerID = 1) with a new contact person and a new city.

    UPDATE Customers
    SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
    WHERE CustomerID = 1;

### Update Warning!
 
 Be careful when updating records. If you omit the WHERE clause, ALL records will be updated!

    UPDATE Customers
    SET PostalCode = 00000;

# MySQL DELETE Statement

The DELETE statement is used to delete existing records in a table.

Example : 
SQL statement deletes the customer "Alfreds Futterkiste" from the "Customers" table:

    DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';

## Delete All Records
 It is possible to delete all rows in a table without deleting the table

    DELETE FROM table_name;

### If you omit the WHERE clause, all records in the table will be deleted!

# MySQL LIMIT Clause

#### LIMIT clause is used to specify the number of records to return.

The LIMIT clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.

Example : 
selects the first three records from the "Customers" table

    SELECT * FROM Customers
    LIMIT 3;

# MySQL MIN() and MAX() Functions
### The MIN() function returns the smallest value of the selected column.
### The MAX() function returns the largest value of the selected column.

Example :

    SELECT MIN(Price) AS SmallestPrice
    FROM Products;

Example :

    SELECT MAX(Price) AS LargestPrice
    FROM Products;

# MySQL COUNT(), AVG() and SUM() Functions

### The COUNT() function returns the number of rows that matches a specified criterion.

Example : 
    
    SELECT COUNT(ProductID)
    FROM Products;

### The AVG() function returns the average value of a numeric column.

Example : 
    
    SELECT AVG(Price)
    FROM Products;

### The SUM() function returns the total sum of a numeric column. 

Example : 
    
    SELECT SUM(Quantity)
    FROM OrderDetails;

#### Note: NULL values are ignored.

# MySQL LIKE Operator

#### The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

- The percent sign (%) represents zero, one, or multiple characters
- The underscore sign (_) represents one, single character

| LIKE Operator   | Description                |
| :--------   | :------------------------- |
| WHERE CustomerName LIKE 'a%'   |  Finds any values that start with "a" |
| WHERE CustomerName LIKE '%a'   |  Finds any values that end with "a"	 |
| WHERE CustomerName LIKE '%or%'   |  Finds any values that have "or" in any position	 |
| WHERE CustomerName LIKE '_r%'   | Finds any values that have "r" in the second position	 |
| WHERE ContactName LIKE 'a%o'   |   Finds any values that start with "a" and ends with "o"	 |

# The MySQL IN Operator

### The IN operator allows you to specify multiple values in a WHERE clause.

Example : selects all customers that are from the same countries as the suppliers
    
    SELECT * FROM Customers
    WHERE Country IN (SELECT Country FROM Suppliers);

Example : selects all customers that are NOT located in "Germany", "France" or "UK"
    
    SELECT * FROM Customers
    WHERE Country NOT IN ('Germany', 'France', 'UK');

# The MySQL BETWEEN Operator
### The BETWEEN operator selects values within a given range. 
The values can be numbers, text, or dates.

Example : selects all products with a price between 10 and 20
    
    SELECT * FROM Products
    WHERE Price BETWEEN 10 AND 20;

Example : selects all products with a ProductName between "Carnarvon Tigers" and "Mozzarella di Giovanni
    
    SELECT * FROM Products
    WHERE ProductName BETWEEN 'Carnarvon Tigers' AND    'Mozzarella di Giovanni'
    ORDER BY ProductName;

#### NOT BETWEEN Text Values Example

    SELECT * FROM Products
    WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
    ORDER BY ProductName;

### BETWEEN Dates Example
The following SQL statement selects all orders with an OrderDate between '01-July-1996' and '31-July-1996':

    SELECT * FROM Orders
    WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31';

# MySQL Aliases
### Aliases are used to give a table, or a column in a table, a temporary name.

- Aliases are often used to make column names more readable.
- An alias is created with the AS keyword.

Example: 

    SELECT CustomerID AS ID, CustomerName AS Customer
    FROM Customers;