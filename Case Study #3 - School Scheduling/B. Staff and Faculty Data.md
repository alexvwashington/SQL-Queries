# Case Study #3 - School Scheduling

## B. Staff and Faculty Data

### 1. List of class ids assigned to staff member, Robert Brown.

````sql
select ClassID from Faculty_Classes
where StaffID = 98012
````
**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/2c73bc0f-d3e4-418e-a0f7-41396912bdeb)

### 2. List of staff names and tenure for staff members with a proficiency rating 10. (ascending by last name within tenure)

````sql
select distinct StfFirstName, StfLastname, DATEDIFF(YY, DateHired, GETDATE()) as 'tenure' from Staff
inner join Faculty_Subjects on Staff.StaffID = Faculty_Subjects.StaffID
where Faculty_Subjects.ProficiencyRating = 10
order by tenure, Staff.StfLastname
````
**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/6615fd54-237a-4247-ba02-17a4589d4219)

### 3. List of subject names of all subjects taught by staffers with more than 20 years of tenure. (ascending order and no duplicates)

````sql
select distinct Subjects.SubjectName from Staff
inner join Faculty_Subjects on Staff.StaffID = Faculty_Subjects.StaffID
inner join Subjects on Faculty_Subjects.SubjectID = Subjects.SubjectID
where DATEDIFF(YY, DateHired, GETDATE()) >20
````

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/ff9efff3-486c-4185-88e0-c0141039c3b6)

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
