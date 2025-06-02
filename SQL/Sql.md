# SQL
### SQL Commands
SELECT 
UPDATE..SET
DELETE, DELETE FROM
INSERT INTO
CREATE DATABASE 
ALTER DATABASE 
CREATE TABLE
ALTER TABLE 
DROP TABLE
CREATE INDEX 
DROP INDEX
TOP/LIMIT
IN
IN..SELECT
BETWEEN (both begin and end values inclusive, works for text values as well)
MIN(), MAX(), COUNT(), SUM(), AVG()  #Aggregate functions ignore null values (except for COUNT())
LIKE (The percent sign % represents zero, one, or multiple characters, The underscore sign _ represents one, single character)
<img width="662" alt="image" src="https://github.com/user-attachments/assets/d64f23b7-1079-4f72-aa7f-ca4023b7749d" />



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


