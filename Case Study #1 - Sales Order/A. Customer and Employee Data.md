# Case Study #1 - Sales Order Data

## A. Customer and Employee Data

### 1. Customer names & data they placed the order.

````sql
select Customers.CustFirstName, customers.CustLastName, Orders.OrderDate
from Customers
inner join Orders on Customers.CustomerID = Orders.CustomerID
order by OrderDate
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/3f65482c-cdcb-406a-a19b-d163c45ab903)

**This result has 944 rows.**

### 2. Employee name & customer name for whom they booked the order.

````sql
select Employees.EmpFirstName, Employees.EmpLastName, Customers.CustFirstName, Customers.CustLastName
from Employees, Customers, Orders
where Employees.EmployeeID = Orders.EmployeeID and
Orders.CustomerID = Customers.CustomerID
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/0f5b86fa-5e3c-49c3-845a-98f403392f0a)

**This result has 944 rows.**

### 3. Customer name & phone number for all customers who ordered clothing. (excluding duplicates)

````sql
select distinct Customers.CustFirstName, Customers.CustLastName, Customers.CustPhoneNumber from Customers
inner join Orders on Customers.CustomerID = Orders.CustomerID
inner join Order_Details on Orders.OrderNumber = Order_Details.OrderNumber
inner join Products on Order_Details.ProductNumber = Products.ProductNumber
inner join Categories on Products.CategoryID = Categories.CategoryID
where Products.CategoryID = 3
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/75b7b73f-2101-42f5-903d-c9e1e25fec8e)

**This result has 27 rows.**

### 4. Employee names for employees who have sold accessories.

````sql
select distinct Employees.EmpFirstName, Employees.EmpLastName from Employees
inner join Orders on Employees.EmployeeID = Orders.EmployeeID
inner join Order_Details on Orders.OrderNumber = Order_Details.OrderNumber
inner join Products on Order_Details.ProductNumber = Products.ProductNumber
inner join Categories on Products.CategoryID = Categories.CategoryID
where Categories.CategoryID = 1
order by Employees.EmpLastName
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/1bb30a79-367e-4aa6-8fca-05833854c88e)
