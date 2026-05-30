# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT medication_id,
       medication_name,
       dosage
FROM Medications
WHERE dosage = (
    SELECT MAX(dosage)
    FROM Medications
);
```

**Output:**
<img width="899" height="489" alt="image" src="https://github.com/user-attachments/assets/f5130183-e920-4066-a7c9-6af1a566b193" />


**Question 2**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

```sql
SELECT name,
       city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="896" height="539" alt="image" src="https://github.com/user-attachments/assets/ebc8cc08-3faa-49d1-8a1c-6f11229e11a8" />


**Question 3**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       o.customer_id,
       o.salesman_id
FROM orders o
JOIN salesman s
  ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**

<img width="1281" height="565" alt="image" src="https://github.com/user-attachments/assets/ee246f11-0453-4754-b459-3d8a9b2e7aa4" />


**Question 4**
---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

```sql
SELECT id,
       name,
       city,
       email,
       phone
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);
```

**Output:**

<img width="1290" height="597" alt="image" src="https://github.com/user-attachments/assets/87e8da7b-552d-438c-a7ed-1ef897ef5e79" />


**Question 5**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

```sql
SELECT id,
       name,
       age,
       city,
       income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```

**Output:**
<img width="1281" height="504" alt="image" src="https://github.com/user-attachments/assets/d453fcd5-fff8-4910-b9ee-520e22094ecc" />


**Question 6**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

```sql
SELECT id,
       name,
       age,
       city,
       income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);
```

**Output:**

<img width="1287" height="628" alt="image" src="https://github.com/user-attachments/assets/dd46adf4-a3d1-4bb6-a997-4550b94213d2" />


**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

<img width="1280" height="516" alt="image" src="https://github.com/user-attachments/assets/d20f1c21-7dc5-4f9c-bb35-250c0a308e0f" />


**Question 8**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT medication_id,
       medication_name,
       dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);
```

**Output:**

<img width="898" height="473" alt="image" src="https://github.com/user-attachments/assets/3a8ca194-0896-49b6-bbf6-6e4f7c69e2bb" />


**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1280" height="692" alt="image" src="https://github.com/user-attachments/assets/ffe81c65-e143-48fc-a718-53150b4e9fe4" />


**Question 10**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_name,
       grade
FROM GRADES g1
WHERE grade = (
    SELECT MAX(g2.grade)
    FROM GRADES g2
    WHERE g1.subject = g2.subject
);
```

**Output:**

<img width="892" height="511" alt="image" src="https://github.com/user-attachments/assets/84f1d41f-939f-4f12-a303-09706e0c011f" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
