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
	  ('Suraj', 'Sanka', 28, '1996-07-13', 'M', 'DevOps Engineer', 'Andra Pradesh'),
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
```
