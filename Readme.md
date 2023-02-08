<!----------------------------------------------- MySQL -------------------------------------------------->
    MySQL is a widely used relational database management system (RDBMS).
    MySQL was first released in 1995
    MySQL is developed, distributed, and supported by Oracle Corporation
    Huge websites like Facebook, Twitter, Airbnb, Booking.com, Uber, GitHub, YouTube, etc.
 
 1.  What is Database ?
      Collection of related information

 2.  What is RDBMS ?
      RDBMS is a program used to maintain a relational database.

      RDBMS uses SQL queries to access the data in the database.

 3.  What is SQL(Structured query language) ?
      It's a Standard Query language used by RDBMS to communicate or access the data with database

 4.  What is a Database Table ?
      Collection of related data entries, and it consists of columns and rows.

 5.  What is a Relational Database ?
      Relationships in database are in the form of tables.

<!----------------------------------------------- MySQL SQL ----------------------------------------------->
     Keep  in Mind That...
      SQL keywords are NOT case sensitive: select is the same as SELECT
     
     Semicolon after SQL Statements?
      Semicolon is the standard way to separate each SQL statement in database systems
 
 1. The MySQL SELECT Statement 
     The SELECT statement is used to select data from a database.
     
     The data returned is stored in a result table, called the result-set. 

    Example : SELECT CustomerName, City, Country FROM Customers;
  
    1.1 The MySQL SELECT DISTINCT Statement ?
         The SELECT DISTINCT statement is used to return only distinct (different) values.  

        Example : SELECT DISTINCT Country FROM Customers;
                   only distinct countrys in resultent set.

 2. What is MySQL WHERE Clause ?
     The WHERE clause is used to filter records.

    Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!

    Example : SQL statement selects all the customers from "Mexico"
              SELECT * FROM Customers
              WHERE Country = 'Mexico';

 Text Fields vs. Numeric Fields
   SQL requires single quotes around text values

 3. Operators in The WHERE Clause ?
    Operator	  Description	
       =	       Equal	
       >	       Greater than	
       <	       Less than	
       >=	       Greater than or equal	
       <=	       Less than or equal	

       <>	       Not equal. Note: In some versions of SQL this operator may be written as !=	
       BETWEEN	   Between a certain range

        Example : SELECT * FROM Products
                  WHERE Price BETWEEN 50 AND 60;

       LIKE	       Search for a pattern	

       Example :  SELECT * FROM Customers
                  WHERE City LIKE 's%';    
    
       IN	       To specify multiple possible values for a column
        Example : 1. SELECT * FROM Customers
                  WHERE City IN ('Paris','London');

                  2. find names of employee who sold 30000 or more to single client 
                     Select emp.firstname from emp where emp.emp_id IN ( Select works_with.emp_id from work_with where works_with.total_sales >30000 );
        





































































        
        

<!-- ORDER BY Keyword -->

 1.1 ORDER BY keyword is used to " sort the result-set " in ascending or descending order.
       ascending order by default ~ ASC
       descending order ~ DESC
 
       Example :  SELECT * FROM Customers
                  ORDER BY Country DESC;
    
 1.2 ORDER BY Several Columns    
       it orders by Country, but if some rows have the same Country, it orders them by CustomerName.

       Example : SELECT * FROM Customers
                 ORDER BY Country, CustomerName;

