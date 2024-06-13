# Case Study #2 - Entertainment Agency Database

## Customer, Member, and Entertainer Metrics

### 1. Customer names who have a preference for Jass or Classic Rock & Roll.

````sql
select Customers.CustFirstName, Customers.CustLastName from Customers
inner join Musical_Preferences on Customers.CustomerID = Musical_Preferences.CustomerID
inner join Musical_Styles on Musical_Preferences.StyleID = Musical_Styles.StyleID
where Musical_Preferences.StyleID = 8 or Musical_Preferences.StyleID = 15
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/9690dc6f-5aa9-4d6b-869b-f32bc98c9266)

### 2. Customer names who have booked an engagement & prefer salsa.

````sql
select distinct Customers.CustFirstName, Customers.CustLastName from Customers
inner join Musical_Preferences on Customers.CustomerID = Musical_Preferences.CustomerID
inner join Engagements on Customers.CustomerID = Engagements.CustomerID
where Musical_Preferences.StyleID = 24 
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/e0476971-cfab-4737-a51c-709e99f8d282)

### 3. Member names who have contracted the entertainer with the stage name 'Coldwater Cattle Company'.

````sql
select Members.MbrFirstName, Members.MbrLastName from Members
inner join Entertainer_Members on Members.MemberID = Entertainer_Members.MemberID
inner join Entertainers on Entertainer_Members.EntertainerID = Entertainers.EntertainerID
where Entertainer_Members.EntertainerID = 1007
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/ebfde2eb-f393-4725-8ac3-b4cefe18f800)

### 4. Entertainer names who had an engagement set up by agent Maria Patterson. (no duplicates & in alphabetical order)

````sql
select distinct Entertainers.EntStageName from Entertainers
inner join Engagements on Entertainers.EntertainerID = Engagements.EntertainerID
inner join Agents on Engagements.AgentID = Agents.AgentID
where Engagements.AgentID = 8
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/700b10af-f21a-4389-bf99-0411f767ebcf)

### 5. Entertainer name and number of engagements.

````sql
select Entertainers.EntStageName, 
(select count(*) from Engagements where Engagements.EntertainerID = Entertainers.EntertainerID) as 'entertainers engagements'
from Entertainers
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/220f00c4-a5ba-492d-ab4f-2d18d2bd7b09)

### 6. Entertainer stage names who have played an engagement for customers from Bellevue. (no duplicates)

````sql
select distinct Entertainers.EntStageName from Entertainers
inner join Engagements on Entertainers.EntertainerID = Engagements.EntertainerID
inner join Customers on Engagements.CustomerID = Customers.CustomerID
where Customers.CustCity like 'Bellevue'
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/b16a7d0a-754e-4b34-8847-a0b18d2c713b)

### 7. Entertainer names of all entertainers who have not been booked to an engagement.

````sql
select Entertainers.EntStageName from Entertainers
left join Engagements on Entertainers.EntertainerID = Engagements.EntertainerID
where Engagements.EntertainerID is null 
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/17dccaaf-34e7-45f9-a235-7b622d1a0cba)
