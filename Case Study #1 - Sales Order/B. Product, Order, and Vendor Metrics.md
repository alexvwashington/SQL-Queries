# Case Study #1 - Sales Order Data

## B. Product, Order, and Vendor Metrics

### 1. Product names for all products purchased from a vendor in Texas.

````sql
select distinct Products.ProductName from Products
inner join Order_Details on Products.ProductNumber = Order_Details.ProductNumber
inner join Product_Vendors on Order_Details.ProductNumber = Product_Vendors.ProductNumber
inner join Vendors on Product_Vendors.VendorID = Vendors.VendorID
where Vendors.VendState = 'TX'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/f03cb681-311d-4c83-92c3-cdf197a25379)

**This answer has 29 rows.** 

### 2. Product names for all products purchased from a customer who lives in Texas.

````sql
select distinct Products.ProductName from Products
inner join Order_Details on Products.ProductNumber = Order_Details.ProductNumber
inner join Orders on Order_Details.OrderNumber = Orders.OrderNumber
inner join Customers on Orders.CustomerID = Customers.CustomerID
where Customers.CustState = 'TX'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/38fa7cb9-2bed-4e52-a6ee-39a56f273f05)

**This answer has 38 rows**

### 3. Order numbers and dates for all orders containing bikes. 

````sql
select Orders.OrderNumber, Orders.OrderDate
from Products
inner join Order_Details on Products.ProductNumber = Order_Details.ProductNumber
inner join Orders on Order_Details.OrderNumber = Orders.OrderNumber
where ProductName like '%bike%'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/6e5ff3a0-1c14-48e3-9c8b-085211f3e035)

**This answer has 1,019 rows**

### 4. Product name and quantity for all products that have not been ordered.

````sql

````

**Answer:**

### 5. 

````sql

````

**Answer:**

