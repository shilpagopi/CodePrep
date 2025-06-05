# SQL Basics
<img width="653" alt="image" src="https://github.com/user-attachments/assets/66f9ebbf-5d4e-4cb0-9b61-7ba6b216a0ea" />

#### Tips
* Remember Order: GROUP BY, HAVING, WINDOW, ORDER BY
* Use SUM(CASE..WHEN..IF..ELSE..END) to count rows only belonging to a certain category set out of n categories (i.e. when using GROUP BY categories).
* ON clause vs.WHERE clause: ON is to specify the conditions for joining the tables. Only the rows satisfying this condition are combined and included in the final result set, whereas the WHERE clause to filter records after the JOIN has been performed.
* Implicit cross product join format: SELECT * FROM facebook, linkedin WHERE facebook.name = linkedin.name.

#### JOINS (t1 JOIN t2 ON)/
* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table
* SELF JOIN (using two different aliases)
* CROSS JOIN : Returns cross product of two tables (no need of ON condition)

#### Window Functions (FUNC(col1) OVER PARTITION BY Col2 ORDER BY Col3)
To perform calculations over a defined set of rows while retaining the original data (eg. compute cumulative sales till date for every row)
<img width="870" alt="image" src="https://github.com/user-attachments/assets/dbf58fd2-4708-461d-882b-8b37c4d2d6fa" />
Window frame extent: Eg. Use 5 PRECEDING
<img width="626" alt="image" src="https://github.com/user-attachments/assets/e880acec-a326-4198-b2e3-26742afe6b1d" />

##### Aggregate
SUM(), AVG(), COUNT(), MAX(),MIN()
<img width="592" alt="image" src="https://github.com/user-attachments/assets/de680099-5d37-40ea-9c1a-e505c2f9fd7a" />

##### Ranking
requires an ORDER BY sub-clause
<img width="911" alt="image" src="https://github.com/user-attachments/assets/c2d40296-c79d-4c60-b844-ba8c42e17817" />
<img width="809" alt="image" src="https://github.com/user-attachments/assets/700cf5f9-b10c-4df1-8141-e2845d11392e" />

<img width="552" alt="image" src="https://github.com/user-attachments/assets/1807d0c4-3194-4737-bf94-77d103a2aace" />
##### Value
FIRST_VALUE(), LAST_VALUE(),..
<img width="711" alt="image" src="https://github.com/user-attachments/assets/2b875e47-7d02-4420-9df1-3200512d7e43" />

##### Lead/Lag: 
LEAD(), LAG()
Syntax: LAG/LEAD(expression [,offset[,default_value]]) OVER(ORDER BY columns)
Expression: the name of the column from which the value is retrieved  
Offset: the number of rows to skip. Defaults to 1.  
Default_value: the value to be returned if the value retrieved is null. Defaults to NULL.  
Requires orderby clause  
<img width="641" alt="image" src="https://github.com/user-attachments/assets/93f5b43a-889f-453f-93a0-ee51b8dc8a6d" />

#### NULL Handling
* Arithmetic Operations (+, -, *, /, %): the result is typically NULL.
  Eg. 5 +/* NULL = NULL, NULL - NULL = NULL  
* Comparison Operations (=, !=, <, >, <=, >=): Always results in UNKNOWN.
  Eg. WHERE Commission = NULL; --> Returns 0 rows. Use Commission IS NULL or IS NOT NULL
* Logical Operations (AND, OR, NOT): Use common sense  
  Eg. TRUE AND UNKNOWN = UNKNOWN, FALSE AND UNKNOWN = FALSE, NOT UNKNOWN = UNKNOWN
* Aggregate Functions (COUNT, SUM, AVG, MIN, MAX): Most by default, ignore NULL values  
* ORDER BY Clause: NULLs are treated as either the smallest or largest values.
  Eg. Can be controlled using NULLS FIRST or NULLS LAST: ORDER BY Commission ASC NULLS LAST;  
* Special Functions:  
  COALESCE(expression1, expression2, ...): Returns the first non-NULL expression in the list. Eg.COALESCE(Commission, 0)
  ISNULL(expression, replacement_value): Use ISNULL or IFNULL or NVL
  NULLIF(expression1, expression2): Returns NULL if expression1 equals expression2; else, returns expression1. Useful for preventing division by zero (e.g., value / NULLIF(divisor, 0)).

#### UNION (SELECT..UNION SELECT)
* The UNION operator is used to combine the result-set of two or more SELECT statements.
* Every SELECT statement within UNION must have the same number of columns
* The columns must also have similar data types
* The columns in every SELECT statement must also be in the same order
* The UNION operator selects only distinct values by default. For duplicate valaues, use "UNION ALL"

#### Performance Tips
* Use INNER JOIN Instead of WHERE for Joins
* Use WHERE Instead of HAVING
* Limit Wildcards to the End of a Search Term (for making use of indices)
* Performance monitoring tools: SQL Sentry (SolarWinds), SQL Profiler (Microsoft), SQL Index Manager (Red Gate), SQL Diagnostic Manager (IDERA)

#### Constraints
<img width="821" alt="image" src="https://github.com/user-attachments/assets/13d7dc81-0d07-4cbe-9aca-279f76b92bfa" />

### SQL Format Examples
* SELECT CustomerName, City FROM Customers;
* SELECT * FROM Customers;
* SELECT DISTINCT Country FROM Customers;
* SELECT COUNT(DISTINCT Country) FROM Customers;
* SELECT * FROM Customers WHERE Country='Mexico';
* SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC; #(Default is Asc)
* SELECT * FROM Customers WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
* SELECT * FROM Customers WHERE Country = 'Spain' AND (CustomerName LIKE 'G%' OR CustomerName LIKE 'R%');
* SELECT * FROM Customers WHERE NOT Country = 'Spain';
* SELECT * FROM Customers WHERE CustomerName NOT LIKE 'A%';
* SELECT * FROM Customers WHERE CustomerID NOT BETWEEN 10 AND 60;
* SELECT * FROM Customers WHERE City NOT IN ('Paris', 'London');
* SELECT * FROM Customers WHERE NOT CustomerID > 50;
* SELECT * FROM Customers WHERE Address IS NOT NULL;
* INSERT INTO Customers (CustomerName, City, Country) VALUES ('Cardinal', 'Stavanger', 'Norway'); #even if there are other columns in the table
* INSERT INTO Customers VALUES ('Cardinal', 'Stavanger', 'Norway'); #If all columns are covered
* INSERT INTO Customers VALUES ('Cardinal', 'Stavanger', 'Norway'),('Greasy Burger', 'Stavanger','Norway'); #insert multiple rows
* UPDATE Customers SET ContactName = 'Alfred Schmidt', City= 'Frankfurt' WHERE CustomerID = 1;
* DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
* DELETE FROM Customers; #Table remains
* DROP TABLE Customers;
  
* SELECT column_name(s) FROM table_name WHERE condition LIMIT number; (MYSQL syntax)
* SELECT TOP 3 * FROM Customers; (SQL Server or MS Access syntax)
* SELECT TOP 50 PERCENT * FROM Customers; (SQL Server or MS Access syntax)
* SELECT MIN(Price) FROM Products;
* SELECT MIN(Price) AS SmallestPrice, CategoryID FROM Products GROUP BY CategoryID;
* SELECT COUNT(*) AS [Number of records], CategoryID FROM Products GROUP BY CategoryID;
* SELECT SUM(Quantity * 10) FROM OrderDetails;
* SELECT SUM(Price * Quantity) FROM OrderDetails LEFT JOIN Products ON OrderDetails.ProductID = Products.ProductID;

* SELECT * FROM Customers WHERE city LIKE 'L_nd__';
* SELECT * FROM Customers WHERE CustomerName LIKE '[bsp]%' OR CustomerName LIKE '[a-f]%';
* SELECT * FROM Customers WHERE CustomerID IN (SELECT CustomerID FROM Orders);
* SELECT * FROM Products WHERE ProductName BETWEEN "A" AND "B";
* SELECT ProductName AS "My Great Products" FROM Products; OR SELECT ProductName "My Great Products" FROM Products;
* SELECT o.OrderID, o.OrderDate, c.CustomerName FROM Customers AS c, Orders AS o WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;
* SELECT CustomerName, CONCAT(Address,', ',PostalCode) AS Address FROM Customers;
* SELECT CustomerName, Address + ', ' + PostalCode AS Address FROM Customers;

* SELECT ProductName, CategoryName FROM Products INNER JOIN Categories ON Products.CategoryID = Categories.CategoryID;
* SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName FROM ((Orders INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID) INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
* SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City FROM Customers A, Customers B WHERE A.CustomerID <> B.CustomerID AND A.City = B.City; #Self-join
* SELECT City FROM Customers UNION SELECT City FROM Suppliers ORDER BY City;
* SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country ORDER BY COUNT(CustomerID) DESC;
* SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID GROUP BY ShipperName;
* SELECT COUNT(CustomerID) as C, Country FROM Customers GROUP BY Country HAVING COUNT(CustomerID) > 5 ORDER BY COUNT(CustomerID) DESC;
* SELECT PROGRAMMING, SCHOOL, COLLEGE FROM geeksforgeeks PIVOT (SUM(Price) FOR Course IN (SCHOOL, COLLEGE)) AS PivotTable
  
* INSERT INTO Student1 SELECT * FROM Student2;
* SELECT SupplierName FROM Suppliers WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID)
* SELECT ProductName FROM Products WHERE ProductID (=, <>, !=, >, >=, <, or <=) ANY (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
* SELECT * INTO CustomersBackup2017 FROM Customers where Year=='2025';
* SELECT * INTO newtable FROM oldtable WHERE 1 = 0; #for schema copying
* SELECT OrderID, Quantity, CASE WHEN Quantity > 30 THEN 'The quantity is greater than 30' WHEN Quantity = 30 THEN 'The quantity is 30' ELSE 'The quantity is under 30' END AS QuantityText FROM OrderDetails;
* SELECT CustomerName, City, Country FROM Customers ORDER BY (CASE WHEN City IS NULL THEN Country ELSE City END);
* SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0)) FROM Products;

* CREATE TABLE Persons (PersonID int,LastName varchar(255));
* CREATE TABLE TestTable AS SELECT customername, contactname FROM customers;
* TRUNCATE TABLE table_name; #deletes only data, not table
* ALTER TABLE Customers ADD Email varchar(255);
* ALTER TABLE table_name DROP COLUMN Email;
* ALTER TABLE table_name RENAME COLUMN old_name to new_name;
* ALTER TABLE Persons ALTER COLUMN DateOfBirth year;
* CREATE VIEW [Brazil Customers] AS SELECT CustomerName, ContactName FROM Customers WHERE Country = 'Brazil';
* CREATE TABLE Persons (Age int, CHECK (Age>=18));
  
* SELECT Name, Age, Department, Salary, AVG(Salary) OVER (PARTITION BY Department) AS Avg_Salary FROM employee
* SELECT Name, Department, Salary, RANK() OVER(PARTITION BY Department ORDER BY Salary DESC) AS emp_rank FROM employee;
* SELECT Date, Sales, SUM(Sales) OVER(ORDER BY Date) AS cumulative_sales_till_date FROM sales_data;

* <img width="230" alt="image" src="https://github.com/user-attachments/assets/86bd1325-6656-4628-92e9-dbea4c46ceea" />
WITH totalSalary(Airline, total) AS (
    SELECT Airline, SUM(Salary)
    FROM Pilot
    GROUP BY Airline
),
    airlineAverage (avgSalary) AS (
    SELECT avg(Salary)
    FROM Pilot 
)
    SELECT Airline
    FROM totalSalary, airlineAverage
    WHERE totalSalary.total > airlineAverage.avgSalary;

#### SQL Keywords and Notes
SELECT   
UPDATE..SET  
DELETE, DELETE FROM  
GROUP BY  
HAVING - The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions  
ORDER BY
INSERT INTO   
CREATE DATABASE   
ALTER DATABASE   
CREATE TABLE   
ALTER TABLE.. ADD/DROP/RENAME/ALTER COLUMN colname #skip keyword COLUMN for add case
DROP TABLE   
CREATE INDEX   
DROP INDEX   
TOP/LIMIT   
IFNULL  
IN   
IN..SELECT   
CASE WHEN..THEN..ELSE..END..AS #to create a new column based on conditions  
CONCAT  
PIVOT  
UNPIVOT  
BETWEEN (both begin and end values inclusive, works for text and date values as well)   
MIN(), MAX(), COUNT(), SUM(), AVG()  #Aggregate functions ignore null values (except for COUNT())   
AS (keyword is optional)   
EXISTS operator returns TRUE if the subquery returns one or more records  
LIKE (The percent sign % represents zero, one, or multiple characters, The underscore sign _ represents one, single character)   
<img width="662" alt="image" src="https://github.com/user-attachments/assets/d64f23b7-1079-4f72-aa7f-ca4023b7749d" />    
Comment formats: /* comments */  or --comments    
For SQL triggers, refer to https://www.geeksforgeeks.org/sql-trigger-student-database    
Subqueries can be used with operators like =, >, <, IN, NOT IN, LIKE, etc.    
Subqueries must always be enclosed in parentheses ().  
For SQL Sequences, refer to https://www.geeksforgeeks.org/sql-sequences/   
For creating stored procedures with parameters, refer to https://www.w3schools.com/sql/sql_stored_procedures.asp   

