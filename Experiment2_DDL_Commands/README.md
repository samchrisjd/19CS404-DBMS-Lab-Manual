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
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
INSERT INTO Student_details
VALUES(201,'David Lee','M','Physics',92);
```

**Output:**

<img width="1233" height="320" alt="image" src="https://github.com/user-attachments/assets/4f2f6d5d-43b9-454c-88bb-a9dfa2a86e65" />


**Question 2**
---
-- Paste Question 2 hereCreate a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
For example:
```sql
CREATE TABLE Employees(
     EmployeeID INT PRIMARY KEY,
     FirstName TEXT NOT NULL,
     LastName TEXT NOT NULL,
     Email VARCHAR(30) UNIQUE,
     Salary INT CHECK(Salary>0),
     DepartmentID INTEGER,
     FOREIGN KEY(DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1232" height="508" alt="image" src="https://github.com/user-attachments/assets/bf5709b9-701b-4ecb-b748-e7fefca67b33" />


**Question 3**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```sql
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

<img width="1234" height="396" alt="image" src="https://github.com/user-attachments/assets/cb79ac12-9e58-4b22-ae57-7e1baee726ae" />


**Question 4**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices(
     InvoiceID INTEGER PRIMARY KEY,
     InvoiceDate DATE,
     DueDate DATE CHECK(DueDate>InvoiceDate),
     Amount REAL CHECK (Amount>0)
);
```

**Output:**

<img width="1234" height="375" alt="image" src="https://github.com/user-attachments/assets/3f0d816e-13bc-4319-8521-ed9d18536b94" />


**Question 5**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
INSERT INTO Customers
VALUES (302,'Laura Croft','456 Elm St','Seattle',98101),
       (303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**

<img width="1219" height="468" alt="image" src="https://github.com/user-attachments/assets/39073de6-dcd3-4904-930c-7df4e8e2cf57" />


**Question 6**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 



```sql
TABLE Companies
RENAME COLUMN name TO first_name;

ALTER TABLE Companies
ADD COLUMN mobilenumb number;

ALTER TABLE Companies
ADD COLUMN DOB Date;
```

**Output:**

<img width="1229" height="480" alt="image" src="https://github.com/user-attachments/assets/5f7ae487-f64b-45fe-86e2-f84c30e2828f" />


**Question 7**
---
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.n 7 here

```sql
ALTER TABLE Student_details
ADD COLUMN Email varchar(50)
ALTER COLUMN MARKS SET DEFAULT 0;
```

**Output:**

![Output7](output.png)

**Question 8**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary


```sql
INSERT INTO Employee(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary
FROM Former_employees;
```

**Output:**

<img width="1240" height="378" alt="image" src="https://github.com/user-attachments/assets/1975d082-6cf9-44aa-b3b6-c8786f37d1d2" />


**Question 9**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
     AssignmentID INTEGER PRIMARY KEY,
     EmployeeID INTEGER,
     ProjectID INTEGER,
     AssignmentDate DATE NOT NULL,
     FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
     FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1242" height="387" alt="image" src="https://github.com/user-attachments/assets/f2862b20-efd3-4015-8943-74d29c41ced7" />


**Question 10**
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
      ord_id TEXT NOT NULL CHECK(LENGTH(ord_id)=4),
      item_id TEXT NOT NULL,
      ord_date DATE,
      ord_qty INTEGER,
      cost INTEGER,
      PRIMARY KEY(item_id,ord_date)
);

```

**Output:**

<img width="1247" height="413" alt="image" src="https://github.com/user-attachments/assets/2d0438f1-fd24-479f-8459-bb5c50fc337c" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
