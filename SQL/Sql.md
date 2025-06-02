# SQL
### SQL Commands
SELECT 
UPDATE
DELETE 
INSERT INTO
CREATE DATABASE 
ALTER DATABASE 
CREATE TABLE
ALTER TABLE 
DROP TABLE
CREATE INDEX 
DROP INDEX

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


