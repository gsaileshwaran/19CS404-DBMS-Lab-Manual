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
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.


Products Table 


name          type       
----------    ---------- 
product_id     INT PRIMARY KEY   

product_name   VARCHAR(10) 

category       VARCHAR(50) 

cost_price     DECIMAL(10)

sell_price     DECIMAL(10)

reorder_lvl    INT

quantity       INT  

supplier_id    INT 



```sql
UPDATE products
SET reorder_lvl=reorder_lvl*0.7
WHERE cost_price>50
AND quantity<100;
```

**Output:**

<img width="1080" height="228" alt="Screenshot 2025-10-25 173202" src="https://github.com/user-attachments/assets/f53a0b08-8e8a-4602-9975-c5386a86fbd1" />


**Question 2**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.


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



```sql
UPDATE employees
SET hire_date='2024-01-24'
WHERE department_id=50;
```

**Output:**

<img width="837" height="239" alt="Screenshot 2025-10-25 173427" src="https://github.com/user-attachments/assets/bad7618d-d0c7-4e46-a168-aef2abce22b3" />


**Question 3**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.


Products Table 


name          type

----------    ---------- 

product_id     INT PRIMARY KEY  

product_name   VARCHAR(10)

category       VARCHAR(50) 

cost_price     DECIMAL(10)

sell_price     DECIMAL(10)

reorder_lv     INT 

quantity       INT 

supplier_id    INT  


```sql
UPDATE products
SET sell_price=sell_price*1.15
WHERE quantity<50
AND supplier_id=10;
```

**Output:**

<img width="1047" height="250" alt="Screenshot 2025-10-25 173543" src="https://github.com/user-attachments/assets/c5f155b3-f487-4a04-8930-fec1d91419eb" />


**Question 4**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.


Products table


---------------

product_id

product_name

category

cost_price

sell_price

reorder_lvl

quantity


```sql
UPDATE products
SET product_name='Premium Bread'
WHERE product_id=5;
```

**Output:**
<img width="1030" height="208" alt="Screenshot 2025-10-25 173707" src="https://github.com/user-attachments/assets/f9b5cf6e-cdc1-41f0-b9d3-846d6ac73337" />



**Question 5**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -


1. 'cust_city' should begin with the letter 'L',


Sample table: Customer


+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
DELETE FROM Customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1173" height="375" alt="Screenshot 2025-10-25 173909" src="https://github.com/user-attachments/assets/08a491dd-bbf8-4a12-871a-f99086e2ecce" />


**Question 6**
---

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.


 
Sample table: Customer


+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
DELETE FROM customer
WHERE grade=2;
```

**Output:**

<img width="371" height="291" alt="Screenshot 2025-10-25 174020" src="https://github.com/user-attachments/assets/b8af69b9-cf7e-4bf0-aedc-0917f018a4eb" />


**Question 7**
---

Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000


Sample table: Customer


+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```sql
DELETE FROM customer
WHERE grade = 3
AND cust_name LIKE '%BBB%'
AND payment_amt>2000;
```

**Output:**

<img width="1322" height="243" alt="Screenshot 2025-10-25 174119" src="https://github.com/user-attachments/assets/e75f8b8d-2d8f-4747-92e2-9e9a7df5cd9e" />


**Question 8**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000


Sample table: Customer


+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```sql
DELETE FROM customer
WHERE grade=2
AND cust_name LIKE 'M%'
AND payment_amt<3000;
```

**Output:**

<img width="1322" height="210" alt="Screenshot 2025-10-25 174219" src="https://github.com/user-attachments/assets/8b9612dd-3df9-4aae-a206-2a11636e8325" />


**Question 9**
---

Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.


 
Sample table: Customer


+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```sql
DELETE FROM customer
WHERE agent_code IN ('A003','A008');
```

**Output:**

<img width="340" height="503" alt="Screenshot 2025-10-25 174320" src="https://github.com/user-attachments/assets/14724c6d-ba32-4338-9bae-982c0c95b0ca" />


**Question 10**
---

   Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.


Sample table: customer


 customer_id |   cust_name    |    city    | grade | salesman_id

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002


```sql
SELECT customer_id,cust_name,city,grade,
salesman_id
FROM customer
WHERE grade>100;
```

**Output:**

<img width="584" height="223" alt="Screenshot 2025-10-25 174438" src="https://github.com/user-attachments/assets/18a8572e-359c-4f30-9106-80a06185c761" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
