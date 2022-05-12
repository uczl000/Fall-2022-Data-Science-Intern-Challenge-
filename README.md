# Fall-2022-Data-Science-Intern-Challenge-
Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.
Answer: 
There were a lot of outliers; A better way to evaluate this data is to remove the outliers first before attempting to get the mean (average) value. 

What metric would you report for this dataset?
Answer: 
Since mean is quite sensitive to outliers, median could be used instead; But if outliers are removed, mean could still be used as metric.

What is its value?
Answer: 
The value of median: $284.00;
The value of mean after removing outliers: $230.46


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

	



