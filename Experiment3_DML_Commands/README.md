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
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
UPDATE Customer
SET grade =5
WHERE city='Chennai';
```

**Output:**

<img width="1228" height="568" alt="image" src="https://github.com/user-attachments/assets/a912a073-c60a-493b-a5f2-bbcb1159d083" />


**Question 2**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table 


```sql
UPDATE products
SET reorder_lvl=(0.7*reorder_lvl)
WHERE cost_price>50 AND quantity<100;
```

**Output:**

<img width="1234" height="542" alt="image" src="https://github.com/user-attachments/assets/9baf474e-05e2-45e8-8602-69e7a9252400" />


**Question 3**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE


```sql
UPDATE PRODUCTS
SET sell_price=ROUND(1.1*sell_price)
WHERE supplier_id=6;
```

**Output:**

<img width="1237" height="630" alt="image" src="https://github.com/user-attachments/assets/e787da4d-882e-4857-b6e5-2a38c04e64ad" />


**Question 4**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```sql
DELETE FROM Customer
WHERE CUST_CITY LIKE 'L%';
```

**Output:**

<img width="1213" height="879" alt="image" src="https://github.com/user-attachments/assets/f24bc098-8ea6-470c-9577-ae32ba7f728c" />


**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Specialization
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE specialization IS Null;
```

**Output:**

<img width="1229" height="944" alt="image" src="https://github.com/user-attachments/assets/7dfdd053-3f2a-4c3a-99e4-eab973cf7992" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

```sql
DELETE FROM Customer
WHERE WORKING_AREA='New York';
```

**Output:**

<img width="1222" height="825" alt="image" src="https://github.com/user-attachments/assets/6cece693-0633-44bc-ade1-e3e1eefc6b6a" />


**Question 7**
---
Write a query to Select all the records from the EmployeeInfo table, where the departments are either HR or Account.

```sql
SELECT *
FROM Employeeinfo
WHERE Department IN ('HR','Account');
```

**Output:**
<img width="1233" height="368" alt="image" src="https://github.com/user-attachments/assets/181d500c-aca3-492d-be39-7afa7b5b7fbb" />

**Question 8**
---
Write a SQL statement to Display the order number, orderdate and the purchase amount of
orders table which will be delivered by the salesman with ID 5001.

orders table

name                 type
---------------     ---------------
order_no            int
purch_amt         real
order_date        text
customer_id      int
salesman_id      int

```sql
SELECT order_no,order_date,purch_amt
FROM orders
WHERE salesman_id=5001;
```

**Output:**

<img width="1049" height="492" alt="image" src="https://github.com/user-attachments/assets/1ed25a19-36ca-4b18-bbb7-4f8bb7fcd27d" />


**Question 9**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table

```sql
SELECT id, decimal,
    CASE
        WHEN decimal >100 THEN 'High'
        WHEN decimal BETWEEN 50 AND 100 THEN 'Medium'
        ELSE 'Low'
    END AS category
FROM Calculations;
```

**Output:**

<img width="849" height="544" alt="image" src="https://github.com/user-attachments/assets/747eb82c-0e3e-4a03-b37b-f089640c9691" />


**Question 10**
---
write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE city='New York' OR grade<=100;
```

**Output:**

<img width="1233" height="528" alt="image" src="https://github.com/user-attachments/assets/4945c81d-5fec-41b4-acde-065213cf331b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
