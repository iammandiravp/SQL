# **Tables**

### **Dimension Tables**
![Student Table](https://github.com/iammandiravp/SQL/blob/0327ee0b427844cf4382573cd91602963ecaa273/Image/Student%20Table.png)

![Course Table](https://github.com/iammandiravp/SQL/blob/0327ee0b427844cf4382573cd91602963ecaa273/Image/Course%20Table.png)

![Teacher Table](https://github.com/iammandiravp/SQL/blob/0327ee0b427844cf4382573cd91602963ecaa273/Image/Teacher%20Table.png)


### **Fact Table**
![Lecture Table](https://github.com/iammandiravp/SQL/blob/0327ee0b427844cf4382573cd91602963ecaa273/Image/Lecture%20Fact%20Table.png)

### **Create Tables**
```sql
-- Student Table:
CREATE TABLE student(
  id INT,
  first_name VARCHAR(25),
  last_name VARCHAR(25),
  email VARCHAR(25),
  city VARCHAR(25)
)

-- Course Table:
CREATE TABLE course(
  id INT,
  course_name VARCHAR(25),
  student_id INT,
  teacher_id INT
)

-- Teacher Table:
CREATE TABLE teacher(
  id INT,
  teacher_name VARCHAR(25),
  course_id INT
)  

-- Lecture Table:
CREATE TABLE lecture(
  id INT,
  student_id INT,
  course_id INT,
  teacher_id INT,
  hours INT,
  batch VARCHAR(25)
)  
```

### **Insert Values**
```sql
-- Insert values into the Student Table:
INSERT INTO student(id, first_name, last_name, email, city)
VALUES (101, 'Kirankumar', 'Yadav', 'iamkirankumar@gmail.com', 'Mumbai'),
	   (102, 'Mandira', 'Priyadarshini', 'iammandira@gmail.com', 'Chikmaglur'),
       (103, 'Suraj', 'Sanka', 'iamsuraj@gmail.com', 'Rajmandri'),
       (104, 'Sumit', 'Suman', 'iamsumit@gmail.com', 'Noida'),
       (105, 'Shobitha', 'Gowda', 'iamshobitha@gmail.com', 'Hassan')

-- Insert values into the Course Table:       
INSERT INTO course(id, course_name, student_id, teacher_id)
VALUES (201, 'Data Science', 101, 301),
       (202, 'Application Support', 102, 302),
       (203, 'DevOps', 103, 303)

-- Insert values into the Teacher Table:       
INSERT INTO teacher(id, teacher_name, course_id)
VALUES (701, 'Swati Bansal', 202),
       (702, 'Chris Dutton', 201),
       (703, 'Laila Gharani', 204)

-- Insert values into the Lecture Table:       
INSERT INTO lecture(id, student_id, course_id, teacher_id, hours, batch)
VALUEs (111, 101, 201, 702, 7, 'Normal'),
       (222, 101, 201, 702, 3, 'Repeat'),
       (333, 102, 202, 703, 5, 'Normal'),
       (444, 102, 202, 703, 2, 'Repeat'),
       (555, 102, 202, 703, 1, 'Exam'),
       (666, 101, 201, 702, 1, 'Exam'),
       (777, 103, 205, 707, 2, 'Normal')
```

### **Select Tables**

```sql
SELECT * FROm student
SELECT * FROM course
SELECT * FROm teacher
SELECT * FROm lecture
```

### **JOINS**

```sql
-- Total hours spend on each batch:
SELECT lecture.batch, SUM(lecture.hours) AS total_hours
from student
JOIN course ON student.id = course.student_id
JOIN lecture ON lecture.course_id = course.id
GROUP BY lecture.batch
HAVING SUM(lecture.hours) > 2
ORDER BY SUM(lecture.hours) DESC;

-- Total hours spend by each student:
SELECT student.first_name, SUM(lecture.hours) AS total_hours
from student
JOIN course ON student.id = course.student_id
JOIN lecture ON lecture.course_id = course.id
GROUP BY student.first_name
ORDER BY SUM(lecture.hours) DESC;

-- Total hours of lectures taken by teachers:
SELECT teacher.teacher_name, SUM(lecture.hours) AS total_hours
FROM teacher
JOIN lecture ON lecture.teacher_id = teacher.id
GROUP BY teacher.teacher_name
ORDER BY SUM(lecture.hours) DESC;
```
