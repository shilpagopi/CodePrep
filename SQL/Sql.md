# SQL
### SQL Commands
SELECT /
UPDATE..SET/
DELETE, DELETE FROM/
GROUP BY
ORDER BY
HAVING - The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions
INSERT INTO /
CREATE DATABASE /
ALTER DATABASE /
CREATE TABLE /
ALTER TABLE /
DROP TABLE /
CREATE INDEX /
DROP INDEX /
TOP/LIMIT /
IN /
IN..SELECT /
CONCAT
BETWEEN (both begin and end values inclusive, works for text and date values as well) /
MIN(), MAX(), COUNT(), SUM(), AVG()  #Aggregate functions ignore null values (except for COUNT()) /
AS (keyword is optional) /
LIKE (The percent sign % represents zero, one, or multiple characters, The underscore sign _ represents one, single character) /
<img width="662" alt="image" src="https://github.com/user-attachments/assets/d64f23b7-1079-4f72-aa7f-ca4023b7749d" />

###### JOINS (t1 JOIN t2 ON)/
* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table
* SELF JOIN (using two different aliases)

###### UNION (SELECT..UNION SELECT)
* The UNION operator is used to combine the result-set of two or more SELECT statements.
* Every SELECT statement within UNION must have the same number of columns
* The columns must also have similar data types
* The columns in every SELECT statement must also be in the same order
* The UNION operator selects only distinct values by default. For duplicate valaues, use "UNION ALL"


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


