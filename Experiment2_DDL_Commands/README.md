# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments (
    AssignmentID   INTEGER PRIMARY KEY,
    EmployeeID     INTEGER,
    ProjectID      INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="821" height="152" alt="image" src="https://github.com/user-attachments/assets/26c0ba50-3fd2-41db-812e-5957a7268cfe" />

**Question 2**
---
-- Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).
```sql
ALTER TABLE employee
ADD COLUMN first_name varchar(50);

ALTER TABLE employee
ADD COLUMN last_name varchar(50);
```

**Output:**
<img width="1080" height="184" alt="image" src="https://github.com/user-attachments/assets/28cdc588-5e2f-431e-aa9d-f8a10f75ccdb" />

**Question 3**
---
-- Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Data Science Essentials', 'Jane Doe', 'TechBooks', 2024);
```

**Output:**
<img width="1157" height="123" alt="image" src="https://github.com/user-attachments/assets/0a28ff44-f334-4361-8940-d754c50981ef" />

**Question 4**
---
-- Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies. 

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;
ALTER TABLE Companies ADD COLUMN mobilenumber number;
ALTER TABLE Companies ADD COLUMN DOB Date;
ALTER TABLE Companies ADD COLUMN State varchar(30);
```

**Output:**
<img width="1084" height="265" alt="image" src="https://github.com/user-attachments/assets/265c4623-5594-49e7-89d6-e46186446a0f" />

**Question 5**
---
--Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
```sql
CREATE TABLE Employees (
    EmployeeID    INT PRIMARY KEY,
    FirstName     VARCHAR(50) NOT NULL,
    LastName      VARCHAR(50) NOT NULL,
    Email         VARCHAR(100) UNIQUE,
    Salary        DECIMAL(10,2) CHECK (Salary > 0),
    DepartmentID  INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**
<img width="843" height="282" alt="image" src="https://github.com/user-attachments/assets/775724c8-ae84-424e-919c-6fd6c03b8a50" />

**Question 6**
---
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**
<img width="735" height="163" alt="image" src="https://github.com/user-attachments/assets/dd6b2db1-2ce4-4a72-94e6-c492bee4455b" />

**Question 7**
---
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
CREATE TABLE Department (
    DepartmentID   INTEGER PRIMARY KEY,
    DepartmentName TEXT NOT NULL UNIQUE,
    Location       TEXT
);
```

**Output:**
<img width="903" height="164" alt="image" src="https://github.com/user-attachments/assets/69888ea8-ee12-4eb9-a4e6-154444950578" />

**Question 8**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (302, 'Laura Croft', '456 Elm St', 'Seattle', '98101');

INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (303, 'Bruce Wayne', '789 Oak St', 'Gotham', '10001');
```

**Output:**
<img width="921" height="233" alt="image" src="https://github.com/user-attachments/assets/c2dd14a2-ea21-48e2-a1b1-d9171088e8e7" />

**Question 9**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
```sql
CREATE TABLE item
(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
FOREIGN KEY(icom_id) REFERENCES company(com_id)
on update cascade
on delete cascade
);
```

**Output:**
![image](https://github.com/user-attachments/assets/45c5daeb-3428-40b2-a4f8-3f85f20f5c02)


**Question 10**
---
--Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/069fcc9f-5be0-400e-9cea-ae0a057886b6)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
