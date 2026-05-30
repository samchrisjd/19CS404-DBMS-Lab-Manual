# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

PATIENTS TABLE:
ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

TEST_RESULT TABLES:
ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
SELECT p.*
FROM patients p
INNER JOIN TEST_RESULTS t
    ON p.patient_id = t.patient_id
WHERE t.test_name IN ('Blood Test', 'Blood Pressure')
  AND t.result NOT LIKE '%Normal%';
```

**Output:**

<img width="1269" height="502" alt="image" src="https://github.com/user-attachments/assets/de9a6886-b567-41f3-805c-8adb23ccf003" />


**Question 2**
---
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT p.first_name, s.*
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="1290" height="504" alt="image" src="https://github.com/user-attachments/assets/6ac545f3-8e65-4efe-a149-03232bc3be80" />


**Question 3**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT p.first_name AS patient_name,
       d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="857" height="477" alt="image" src="https://github.com/user-attachments/assets/efeed617-3485-45d1-a15b-9636bee68d4c" />


**Question 4**
---
Write an SQL query to retrieve all columns from the 'customer' table (aliased as 'c') using a LEFT JOIN with the 'orders' table on the 'customer_id' column, and filter the results to include only those orders placed between '2012-07-01' and '2012-07-30'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="1274" height="516" alt="image" src="https://github.com/user-attachments/assets/3266349b-c30f-42b5-83ac-99be7eb6dc59" />


**Question 5**
---
SELECT c.*
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';

```sql
SELECT s.name AS salesman_name,
       c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c
    ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="840" height="965" alt="image" src="https://github.com/user-attachments/assets/913af7fc-c966-4a90-a3f3-3bf4614de301" />


**Question 6**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT o.ord_no,
       o.purch_amt,
       c.cust_name,
       c.city
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="1277" height="592" alt="image" src="https://github.com/user-attachments/assets/20bc91c2-b658-473a-af37-c61c1eca0818" />


**Question 7**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS 'Customer Name',
       c.grade,
       s.name AS Salesman,
       s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1261" height="922" alt="image" src="https://github.com/user-attachments/assets/8f6239d2-3d3e-4ecc-bc8a-4d7fe0f344d3" />


**Question 8**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
SELECT c.cust_name AS 'Customer Name',
       c.city AS city,
       s.name AS Salesman,
       s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**

<img width="1306" height="878" alt="image" src="https://github.com/user-attachments/assets/ba666a5a-5817-4a34-83fe-e78de28b7dcb" />


**Question 9**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT c.cust_name AS 'Customer Name',
       c.city,
       s.name AS Salesman,
       s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1280" height="871" alt="image" src="https://github.com/user-attachments/assets/d6fc2cb7-aa65-46e6-aa3f-1715ddc29811" />


**Question 10**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT s.name AS Salesman,
       c.cust_name,
       c.city
FROM salesman s
INNER JOIN customer c
    ON s.city = c.city;
```

**Output:**

<img width="1283" height="794" alt="image" src="https://github.com/user-attachments/assets/51d17a93-5b68-49be-a949-322c9170abe0" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
