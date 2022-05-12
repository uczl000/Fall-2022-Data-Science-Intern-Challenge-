# Fall-2022-Data-Science-Intern-Challenge-
Question 1:


Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. 
Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.


a.	How many orders were shipped by Speedy Express in total?

SELECT COUNT(a.orderID) as NumberOfOrders
FROM Orders a
LEFT JOIN Shippers b
ON a.ShipperID = b.ShipperID
Where b.ShipperID = ‘Speedy Express’;

Result --> 54


b.	What is the last name of the employee with the most orders?


SELECT b.LastName
FROM Orders  a
JOIN Employees b ON a.EmployeeID = b.EmployeeID
GROUP BY EmployeeID
ORDER BY count(orderID) DESC
LIMIT 1;

Result --> Peacock

c.	What product was ordered the most by customers in Germany?


SELECT a.ProductName
FROM Products a
    JOIN OrderDetails b ON a.ProductID = b.ProductID
    JOIN Orders c ON b.OrderID = c.OrderID
    JOIN Customers d ON c.CustomerID = d.CustomerID
WHERE d.Country = "Germany"
GROUP BY a.ProductName
ORDER BY SUM(b.Quantity) DESC
LIMIT 1;

Result --> Boston Crab Meat

	



