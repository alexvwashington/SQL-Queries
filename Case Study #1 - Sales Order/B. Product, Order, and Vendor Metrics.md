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
select Products.ProductName, Products.QuantityOnHand from Products
left join Order_Details on Products.ProductNumber = Order_Details.ProductNumber
where Order_Details.ProductNumber is null 
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/7f0d7007-c767-487b-933b-0c969fc71aca)

### 5. Product names and descriptions for all products order by a vendor with 'bike' in their name. 

````sql
select distinct Products.ProductName, Products.ProductDescription  from Products
inner join Order_Details on Products.ProductNumber = Order_Details.ProductNumber
inner join Product_Vendors on Order_Details.ProductNumber = Product_Vendors.ProductNumber
inner join Vendors on Product_Vendors.VendorID = Vendors.VendorID
where Vendors.VendName like '%bike%'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/49754711-0873-4cfd-865b-13a2db14285f)

**This answer has 32 rows.**

### 6. Most expensive product sold which is purchased from ProFormance. 

````sql
select distinct Products.ProductName from Order_Details
inner join Products on Order_Details.ProductNumber = Products.ProductNumber
inner join Product_Vendors on Products.ProductNumber = Product_Vendors.ProductNumber
inner join Vendors on Product_Vendors.VendorID = Vendors.VendorID
where Vendors.VendorID = 4 and products.RetailPrice = 1200

````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/0b15a64b-1513-49b6-b18b-e75abe3486f5)

### 7. Product names from vendors who do not have a webpage.

````sql
select distinct Products.ProductName from Product_Vendors
left join Products on Product_Vendors.ProductNumber = Products.ProductNumber
where Product_Vendors.VendorID IN (6, 7, 8, 9)
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/12ae84e8-7476-460f-bc77-3d4c5b7286e2)

**This answer has 34 rows**

### 8. Vendor names of all vendors that sell bikes.

````sql
select distinct Vendors.VendName from Vendors
inner join Product_Vendors on Vendors.VendorID = Product_Vendors.VendorID
inner join Products on Product_Vendors.ProductNumber = Products.ProductNumber
where Products.ProductName like '%bike%'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/33b115b0-46de-4255-87bc-c85111c1d48f)

