# Case Study #3 - School Scheduling

## B. Staff and Faculty Data

### 1. List of class ids assigned to staff member, Robert Brown.

````sql

````
**Answer:**

### 2. List of staff names and tenure for staff members with a proficiency rating 10. (ascending by last name within tenure)

````sql

````
**Answer:**

### 3. List of subject names of all subjects taught by staffers with more than 20 years of tenure. (ascending order and no duplicates)

````sql

````

**Answer:**

### 4. List of staff members and the number of classes they teach.
````sql
select Staff.StfFirstName, Staff.StfLastname, 
(select count(*) from Faculty_Classes where Faculty_Classes.StaffID = Staff.StaffID) as 'Class Count'
from Staff
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/55ec8a49-bf41-483f-abf7-76ca7e44467c)

**This list has 27 rows**

### 5. List of faculty member names who teach in a class without a phone. (no duplicates)

````sql
select distinct Staff.StfFirstName, Staff.StfLastname from Staff
inner join Faculty on Staff.StaffID = Faculty.StaffID
inner join Faculty_Classes on Faculty.StaffID = Faculty_Classes.StaffID
inner join Classes on Faculty_Classes.ClassID = Classes.ClassID
inner join Class_Rooms on Classes.ClassRoomID = Class_Rooms.ClassRoomID
where Class_Rooms.PhoneAvailable = 0
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/0c9f4fe6-7eb3-4bc6-8a40-abf919d0993e)
