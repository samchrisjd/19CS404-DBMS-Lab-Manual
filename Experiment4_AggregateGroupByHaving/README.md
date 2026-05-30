# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

```sql
select InsuranceCompany, avg(EndDate-StartDate)as AvgCoverageDurationDays
from Insurance
group by InsuranceCompany;
```

**Output:**

<img width="876" height="772" alt="image" src="https://github.com/user-attachments/assets/f1352480-345b-44e2-9661-1a377bc17fc0" />


**Question 2**
---
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```sql
select DoctorID, count(appointmentID)as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

<img width="856" height="715" alt="image" src="https://github.com/user-attachments/assets/668b36ab-3db9-4b4a-a319-b522f866e254" />


**Question 3**
---
How many medical records are there for each patient?

Sample table:MedicalRecords Table

```sql
select PatientID,count(patientID) as TotalRecords
from MedicalRecords
group by PatientID;
```

**Output:**

<img width="869" height="726" alt="image" src="https://github.com/user-attachments/assets/5a6a4475-424a-4da0-95f9-0e97c57aad6e" />


**Question 4**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

```sql
select avg(length(name))as avg_name_length
from customer
where city='Chennai';
```

**Output:**

<img width="867" height="397" alt="image" src="https://github.com/user-attachments/assets/8ed7a9e6-6810-46f3-89f2-cc9397a2a48a" />


**Question 5**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

```sql
select count(city) as COUNT
from customer
where city='Noida';
```

**Output:**
<img width="571" height="401" alt="image" src="https://github.com/user-attachments/assets/cb1b04b4-210b-4fc4-881f-f46e5aef789d" />


**Question 6**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer
```sql
select count(city) as COUNT
from customer
where city != 'Noida';
```

**Output:**

<img width="787" height="408" alt="image" src="https://github.com/user-attachments/assets/e1d24e46-d829-4488-92e5-f88905d8270c" />


**Question 7**
---
Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

```sql
select min(purch_amt) as MINIMUM
from orders;
```

**Output:**

<img width="630" height="393" alt="image" src="https://github.com/user-attachments/assets/42fccaa3-c572-4b3a-a7c4-9a6016135e6e" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee

```sql
select age,min(income)as Income
from employee
group by age
having Income<1000000;
```

**Output:**
<img width="867" height="504" alt="image" src="https://github.com/user-attachments/assets/5acb27ef-7518-4610-b896-039ec7016e7a" />


**Question 9**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products

```sql
select category_id, AVG(Price)
from products
group by category_id
having price between 10 and 15;
```

**Output:**

<img width="867" height="420" alt="image" src="https://github.com/user-attachments/assets/b9988bad-bb91-4b6d-a042-3e2256a58c81" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1

```sql
select jdate,SUM(workhour)
from employee1
group by jdate
having Sum(workhour)>40;
```

**Output:**

<img width="858" height="457" alt="image" src="https://github.com/user-attachments/assets/bc1c4bea-2a8c-42fe-b53c-9d15c58efa64" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
