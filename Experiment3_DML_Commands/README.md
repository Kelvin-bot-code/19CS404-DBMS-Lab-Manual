# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to double the availability of the product with product_id 1. products table

product_id product_name category_id availability

```sql
update products
set availability = availability * 2
where product_id = 1;
```

**Output:**

<img width="817" height="156" alt="509078872-64439a85-b499-421a-ac0a-7756886fd282" src="https://github.com/user-attachments/assets/f487d92b-80b2-44d3-a13f-5ebc41d9633c" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN' Employees table
```
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

```sql
update Employees 
set SALARY = SALARY * 2 
where job_id like "%MAN"
```

**Output:**

<img width="817" height="235" alt="509079363-5e734feb-30b1-4ed9-beff-1e6da07bacdf" src="https://github.com/user-attachments/assets/f07ce6fe-8dce-4ec4-8fc8-e6461a150989" />


**Question 3**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.
```
Suppliers Table
name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```

```sql
update Suppliers
set address = '58 Lakeview, Magnolia'
where supplier_id=5
```

**Output:**

<img width="817" height="265" alt="509079812-ba38ace7-746a-4860-bc84-8bb13a8ada7c" src="https://github.com/user-attachments/assets/9321d10c-5075-4a4d-9c13-e1dca8fbfc1b" />



**Question 4**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.
```
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
update Employees 
set EMAIL = 'Unavailable'
```

**Output:**


<img width="812" height="312" alt="509080927-ba794059-6846-4d87-8e5c-2673d5f38dfc" src="https://github.com/user-attachments/assets/81a26d79-121d-4394-82fd-967e25b6c580" />


**Question 5**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE
```
name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```

```sql
UPDATE  PRODUCTS 
set reorder_lvl = reorder_lvl * 0.7
where product_name like '%cream%' and quantity > reorder_lvl;
```

**Output:**


<img width="817" height="332" alt="509081409-7fff9558-0599-4b92-b8b5-ff7b37902efd" src="https://github.com/user-attachments/assets/51d016c8-9a5c-405a-9323-648b7b636ee0" />

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 |BBBBSBB      | A008
```

```sql
delete FROM Customer
where CUST_CITY <>'New York' and OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="822" height="385" alt="509085522-1320a9fc-f385-4b3d-9add-2b0a4788e415" src="https://github.com/user-attachments/assets/1669766f-cdbf-4b92-83cc-f534ff9d6245" />



**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008
```

```sql
delete from Customer
where grade%2=1;
```

**Output:**

<img width="817" height="287" alt="509085944-97d682a0-9c13-4d16-b8b7-39bbc4c1fe87" src="https://github.com/user-attachments/assets/909185e9-4d89-4c36-8c18-fbb0f2a3df21" />


**Question 8**
---

Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from Doctors
where specialization is null;
```

**Output:**

<img width="812" height="627" alt="509087326-edb46473-d7ff-45d7-8621-4a0fbb6775fc" src="https://github.com/user-attachments/assets/ef18a6f8-ba10-4c59-b710-15117819e94a" />


**Question 9**
Show the categoryName and description from the categories table sorted by categoryName.
```
name                     type
---------------       ---------------
CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)
```
```sql
select CategoryName,Description from categories
order by CategoryName ASC;
```

**Output:**


<img width="813" height="331" alt="509088370-01db0404-37f0-44bf-a3aa-4f6be0689855" src="https://github.com/user-attachments/assets/eb6098df-ce7f-4f52-a381-b7ad9ce6ebf7" />

**Question 10**
---
Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.
```
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```

```sql
select id,value1,
    case
        when value1 > 50 then 'High'
        else 'Low'
    end as value_category
from Calculations;
```

**Output:**

<img width="778" height="247" alt="509094042-8c290305-6058-49d8-99b7-4ae62768800e" src="https://github.com/user-attachments/assets/c9b38be4-ccd0-4c4e-9514-4f085fb645ec" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
