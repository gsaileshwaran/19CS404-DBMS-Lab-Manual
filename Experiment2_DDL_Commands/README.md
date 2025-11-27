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
Create a table named Events with the following columns:

EventID as INTEGER

EventName as TEXT

EventDate as DATE

--

```
CREATE TABLE Events (

EventID INTEGER,
EventName TEXT,
EventDate DATE

);

```

**Output:**

<img width="1189" height="271" alt="Screenshot 2025-10-25 170434" src="https://github.com/user-attachments/assets/5eb10f3d-0def-483a-b1a5-44bf4c13e87c" />

**Question 2**
---
Create a new table named item with the following specifications and constraints:

item_id as TEXT and as primary key.

item_desc as TEXT.

rate as INTEGER.

icom_id as TEXT with a length of 4.

icom_id is a foreign key referencing com_id in the company table.

The foreign key should set NULL on updates and deletes.

item_desc and rate should not accept NULL.


```sql
CREATE TABLE item (
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK (LENGTH(icom_id)=4),
FOREIGN KEY (icom_id)
REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**

<img width="980" height="262" alt="Screenshot 2025-10-25 170708" src="https://github.com/user-attachments/assets/9dd2dfff-2d33-440f-a0a5-8bad136c362c" />


**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.

FirstName and LastName should be NOT NULL.

Email should be unique.

Salary should be greater than 0.

DepartmentID should be a foreign key referencing the Departments table.


```sql
CREATE TABLE Employees(
EmployeeID INTEGER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary REAL CHECK (salary >0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID)
REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1214" height="315" alt="Screenshot 2025-10-25 170824" src="https://github.com/user-attachments/assets/116f3825-60af-46db-ae53-133605ad1393" />


**Question 4**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.


RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M       


Note: The Subject and MARKS columns will use their default values.


```sql
INSERT INTO Student_details(RollNo,Name,Gender)
VALUES(204,'Samuel Black','M');
```

**Output:**
<img width="764" height="245" alt="Screenshot 2025-10-25 170933" src="https://github.com/user-attachments/assets/7bd1635c-21e0-456a-a5a0-0eba6ad7e1ef" />


**Question 5**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:

designation as VARCHAR(50)

net_salary as NUMBER

dob as DATE
 

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number; 

ALTER TABLE Companies
ADD COLUMN dob date; 
```

**Output:**

<img width="1086" height="311" alt="Screenshot 2025-10-25 171026" src="https://github.com/user-attachments/assets/4272d7be-2069-42ed-a3ec-3ef658e43e69" />


**Question 6**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number; 
```

**Output:**

<img width="1126" height="293" alt="Screenshot 2025-10-25 171140" src="https://github.com/user-attachments/assets/db3f5e8b-de25-416e-92b0-f9b81c99e731" />


**Question 7**
---
Create a new table named contacts with the following specifications:

contact_id as INTEGER and primary key.

first_name as TEXT and not NULL.

last_name as TEXT and not NULL.

email as TEXT.

phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.


```sql
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
)
```

**Output:**

<img width="1113" height="175" alt="Screenshot 2025-10-25 171252" src="https://github.com/user-attachments/assets/2dfa4cf6-b973-4e70-8d91-cf120d5f56a3" />


**Question 8**
---
Create a new table named orders with the following specifications:

ord_id as TEXT with a length of 4.

item_id as TEXT.

ord_date as DATE.

ord_qty as INTEGER.

cost as INTEGER.

The primary key is a composite key consisting of item_id and ord_date.

ord_id and item_id should not accept NULL


```sql
CREATE TABLE orders (
    ord_id TEXT NOT NULL CHECK (LENGTH(ord_id)=4),
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGER,
    cost INTEGER,
    PRIMARY KEY (item_id,ord_date)
);
```

**Output:**

<img width="959" height="165" alt="Screenshot 2025-10-25 171416" src="https://github.com/user-attachments/assets/421d0c60-e8e8-4a55-a640-78d5e935b89a" />


**Question 9**
---
Write a SQL Query for inserting the below values in the table Customers


ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000


```sql
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY)VALUES
(1,'Ramesh',32,'Ahmedabad',2000),
(2,'Khilan',25 ,'Delhi',1500),
(3,'Kaushik',23,'Kota',2000 );
```

**Output:**

<img width="1240" height="289" alt="Screenshot 2025-10-25 171528" src="https://github.com/user-attachments/assets/67f2b77e-8200-4325-914e-3b1a4753d3a8" />


**Question 10**
---
Insert all products from Discontinued_products into Products.


Table attributes are ProductID, ProductName, Price, Stock


```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock
FROM Discontinued_products;
```

**Output:**

<img width="1074" height="294" alt="Screenshot 2025-10-25 171645" src="https://github.com/user-attachments/assets/09a86b71-9b17-40f0-a71b-67cac2eb81a5" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
