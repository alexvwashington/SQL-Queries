# Case Study #3 - School Scheduling

## A. Student and Class Data

### 1. List of students and classes they are currently enrolled in.

''''sql

''''

**Answer:**

### 2. List of student names and ages for all students enrolled in an Information Science degree. (descending order by age)

''''sql

''''

**Answer:**

### 3. List of student names enrolled in a class that begins at 11 am. (last name in alphabetical order)

''''sql
select Students.StudFirstName, Students.StudLastName from Students
inner join Student_Schedules on Students.StudentID = Student_Schedules.StudentID 
inner join Classes on Student_Schedules.ClassID = Classes.ClassID
where Classes.StartTime = '11:00:00' and Student_Schedules.ClassStatus = 2
order by Students.StudLastName
''''

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/efde45ce-07b6-4d6a-89cc-b131daf9923e)

### 4. List of student names who attend class in a classroom with a capacity greater than 80.

''''sql
select distinct Students.StudFirstName, Students.StudLastName from Students
inner join Student_Schedules on Students.StudentID = Student_Schedules.StudentID
inner join Classes on Student_Schedules.ClassID = Classes.ClassID
inner join Class_Rooms on Classes.ClassRoomID = Class_Rooms.ClassRoomID
where Student_Schedules.ClassStatus = 1 and Class_Rooms.Capacity < 80
''''

**Answer:**

![image](https://github.com/alexvwashington/SQL-Queries/assets/165182969/b9fdb29a-90e8-48a7-97d2-7c40b729d1e3)

### 5. Class IDs for all classes are assigned to classrooms in buildings with three floors.

''''sql

''''

**Answer:**
