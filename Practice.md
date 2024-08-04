# **Practice**

```sql
-- Create a table for employee details:
CREATE TABLE employee(
  employee_id INT IDENTITY PRIMARY KEY,
  first_name VARCHAR(25),
  last_name VARCHAR(25),
  age INT CHECK (Age >= 18) NOT NULL,
  birth_date DATE,
  gender VARCHAR(1),
  designation VARCHAR(25),
  city VARCHAR(25) DEFAULT 'Bengaluru'
);
```
```sql
-- Create a table for department details:
CREATE TABLE department(
  department_id INT PRIMARY KEY IDENTITY,
  department_name VARCHAR(25),
  employee_id INT NOT NULL,
  project VARCHAR(25),
  team VARCHAR(25) DEFAULT 'Apple',
  FOREIGN KEY (employee_id) REFERENCES employee(employee_id)
);
```
```sql
-- Insert some values in the employee table:  
INSERT INTO employee(first_name, last_name, age, birth_date, gender, designation, city)
VALUES('Kirankumar', 'Yadav', 28, '1996-02-07', 'M', 'Data Science Specialist', 'Mumbai'),
      ('Mandira', 'Priyadarshini', 26, '1998-06-28', 'F', 'Support Executive', DEFAULT),
      ('Suraj', 'Sanka', 28, '1996-07-13', 'M', 'DevOps Engineer', 'Andhra Pradesh'),
      ('Sumit', 'Suman', 26, '1998-12-06', 'M', 'Python Developer', 'Noida'),
      ('Shobitha', 'Gowda', 26, '1998-09-18', 'F', 'Java Developer', DEFAULT);
```
```sql
-- Insert some values in the department table:
INSERT INTO department(department_name, employee_id, project, team)
VALUES('Data Science', 1, 'DSA', DEFAULT),
      ('Apple Decision Support', 2, 'Apple Support', DEFAULT),
      ('SAP BTP', 3, 'APIM', 'SAP'),
      ('Data Analytics', 4, 'DSA', DEFAULT),
      ('Java Core', 5, 'JDK', 'IBM');
```
```sql
-- Select employee and department table:
SELECT *
FROM employee

SELECT *
FROM department
```

### **employee table**
employee_id | first_name | last_name | age | birth_date | gender | designation | city
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
1 | Kirankumar | Yadav | 28 | 1996-02-07 | M | Data Science Specialist | Mumbai
2 | Mandira | Priyadarshini | 26 | 1998-06-28 | F | Support Executive | Bengaluru
3 | Suraj | Sanka | 28 | 1996-07-13 | M | DevOps Engineer | Andhra Pradesh
4 | Sumit | Suman | 26 | 1998-12-06 | M | Python Developer | Noida
5 | Shobitha | Gowda | 26 | 1998-09-18 | F | Java Developer | Bengaluru

### **department table**
department_id | department_name | employee_id | project | team
:--- | :--- | :--- | :--- | :---
1 | Data Science | 1 | DSA | Apple
2 | Apple Decision Support | 2 | Apple Support | Apple
3 | SAP BTP | 3 | APIM | SAP
4 | Data Analytics | 4 | DSA | Apple
5 | Java Core | 5 | JDK | IBM

```sql
-- Extract Year, Month and Day using the birth_date column:
SELECT 
YEAR(birth_date) AS birth_year, 
MONTH(birth_date) AS birth_month, 
DAY(birth_date) AS birth_day
FROM employee
```
birth_year | birth_month | birth_day
:--- | :--- | :---
1996 | 2 | 7
1998 | 6 | 28
1996 | 7 | 13
1998 | 12 | 6
1998 | 9 | 18

```sql
-- Concat the first_name and last_name as a name:
SELECT first_name + ' ' + last_name AS name FROM employee
SELECT CONCAT(first_name, ' ',last_name) AS Name from employee
```
name
:---
Kirankumar Yadav
Mandira Priyadarshini
Suraj Sanka
Sumit Suman
Shobitha Gowda

```sql
-- String operations:
SELECT
UPPER(first_name) AS uppercase, 
LOWER(last_name) AS lowercase
FROM employee
```
uppercase | lowercase
:--- | :---
KIRANKUMAR | yadav
MANDIRA | priyadarshini
SURAJ | sanka
SUMIT | suman
SHOBITHA | gowda

```sql
-- Subquery:
SELECT first_name, designation, city 
FROM employee
WHERE employee_id IN (SELECT employee_id FROM department WHERE team = 'Apple')
```
first_name | designation | city
:--- | :--- | :---
Kirankumar | Data Science Specialist | Mumbai
Mandira | Support Executive | Bengaluru
Sumit | Python Developer | Noida

```sql
-- Join:
SELECT employee.first_name, employee.last_name, employee.designation, department.department_name, department.project
FROm employee
INNER JOIN department
ON employee.employee_id = department.employee_id
```
first_name | last_name | designation | department_name | project
:--- | :--- | :--- | :--- | :---
Kirankumar | Yadav | Data Science Specialist | Data Science | DSA 
Mandira | Priyadarshini | Support Executive | Apple Decision Support | Apple Support
Suraj | Sanka | DevOps Engineer | SAP BTP | APIM
Sumit | Suman | Python Developer | Data Analytics | DSA
Shobitha | Gowda | Java Developer | Java Core | JDK

```sql
-- CASE (Condition with only equal to operator and values):
SELECT first_name, last_name,
CASE gender
  WHEN 'M' THEN 'Male'
  WHEN 'F' THEN 'Female'
  ELSE 'Transgender'
END AS gender, age
FROM Employee;
```
first_name | last_name | gender | age 
:--- | :--- | :--- | :---
Kirankumar | Yadav | Male | 28
Mandira | Priyadarshini | Female | 26
Suraj | Sanka | Male | 28
Sumit | Suman | Male | 26
Shobitha | Gowda | Female | 26

```sql
-- CASE (Conditions with <, >, <=, >=, !=, <> operators):
SELECT first_name, last_name, 
CASE 
  WHEN YEAR(birth_date) < 1998 THEN 'Millenial'
  WHEN YEAR(birth_date) BETWEEN 1998 AND 2000 THEN 'GenZ'
  ELSE 'Monkeys'
END AS generation, age
FROM employee
```
first_name | last_name | generation | age 
:--- | :--- | :--- | :---
Kirankumar | Yadav | Millenial | 28
Mandira | Priyadarshini | GenZ | 26
Suraj | Sanka | Millenial | 28
Sumit | Suman | GenZ | 26
Shobitha | Gowda | GenZ | 26

```sql
-- Pattern matching:
SELECT *
FROM employee
WHERE first_name LIKE 'k%'      -- starts with character 'k'

SELECT *
FROM employee
WHERE first_name LIKE '%a'      -- ends with character 'a'

SELECT *
FROM employee
WHERE first_name LIKE '%an%'    -- 'an' at any position in the middle

SELECT *
FROM employee
WHERE first_name LIKE '__n%'    -- Any two character in the starting and 'n' at 3rd place.

SELECT *
FROM employee
WHERE first_name LIKE 'su[rm]%' -- Starts with su and can continue with r or m

SELECT *
FROM employee
WHERE first_name LIKE '[K-M]%'  -- Starts with any character between K to M

SELECT *
FROM employee
WHERE first_name LIKE '_____'   -- Exactly 5 character word
```
