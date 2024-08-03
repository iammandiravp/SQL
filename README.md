# **SQL**
### **Structured Query Language**
- A programming language designed to communicate with data stored in the **relational database management system**.
- **SQL** syntax is similar to the english language. Which makes it relatively easy to read, write, and interpret.
- **RDBMS** use SQL to access, manage, manipulate, update the data in tables stored in the database schemas.

### **Database**
- A database is a collection of structured information stored so it can be easily accessed and updated.
- In a computer system, databases are commonly accessed through a database management system.
- **Database Objects:** Table, View, Index, etc.

### **Relational Database** 
- A store of structured data organized in tables made up of rows and columns.
- Multiple tables can have relationships based on the values in key columns (Primary or Foreign)
- They provide an efficient and flexible way to access structured information.
- Data is typically queried and manipulated using Structured Query Language (SQL).
- The software that controls a relational database is called relational DBMS.
- Example: MySQL, SQLite, PostgreSQL, Microsoft SQL Server, Microsoft Access, Microsoft Azure SQL, etc.

### **ACID Properties**
- ACID is an acronym that stands for Atomicity, Consistency, Isolation, and Durability.
- ACID are four key properties that define the reliability and consistency of SQL operations in a DBMS.
- **Atomicity:** All or nothing. Either all the operations are completed successfully or None.
- **Consistency:** The database must remain consistent before and after the SQL operations.
- **Isolation:** SQL operations are independent of one another, and do not interfere with each other.
- **Durability:** SQL operation once completed, is permanent and persists even if a system failure occurs.

### **Type of Statements**
**Data Query Language (DQL)**
- SQL commands for performing queries on data within database.
- `SELECT` retrieves data from the database.

**Data Definition Language (DDL)** 
- SQL commands used to define database schema
- These commands are used to create and modify the structure of database objects.
- `CREATE` creates an objects in the database.
- `DROP` deletes an object from the database.
- `ALTER` changes the definition of an existing object in the database.

**Data Manipulation Language (DML)**  
- SQL commands used to modify the data stored in the database.
- `INSERT` inserts new data into a database table.
- `UPDATE` alter data in a database table.
- `DELETE` removes data from a database table.

**Data Control Language (DCL)**
- SQL commands dealing with the controls and properties of the DBMS, such as rights and permissions to database objects.
- `GRANT` grants a user permissions on a database object.
- `REVOKE` removes a user's permissions on a database object.
