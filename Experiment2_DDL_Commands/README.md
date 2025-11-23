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
<img width="1031" height="345" alt="image" src="https://github.com/user-attachments/assets/fd4d1b43-2aba-4f7b-b26d-8dc8d906c6da" />


```sql
CREATE TABLE Departments (
    DepartmentID INTEGER,
    DepartmentName TEXT
); 
```

**Output:**

<img width="1231" height="440" alt="image" src="https://github.com/user-attachments/assets/090969c9-49e8-4f5e-bb0e-c52425eb87cb" />


**Question 2**
---
<img width="1236" height="460" alt="image" src="https://github.com/user-attachments/assets/d826c4dd-9958-47a4-ba06-ac71b1dfb633" />


```sql
CREATE TABLE orders (
    ord_id TEXT NOT NULL CHECK (LENGTH(ord_id) = 4),
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGER,
    cost INTEGER,
    PRIMARY KEY (item_id, ord_date)
);
```

**Output:**

<img width="1222" height="415" alt="image" src="https://github.com/user-attachments/assets/63fb1a13-909c-492a-9774-67b73ce78fb4" />


**Question 3**
---
<img width="1222" height="368" alt="image" src="https://github.com/user-attachments/assets/202549b7-b5a6-4505-b786-6ec6501da3e4" />


```sql
ALTER TABLE employee
ADD COLUMN first_name varchar(50);

ALTER TABLE employee
ADD COLUMN last_name varchar(50);
```

**Output:**

<img width="1247" height="387" alt="image" src="https://github.com/user-attachments/assets/064f5775-dff8-49c2-b91b-d8f257b92989" />


**Question 4**
---
<img width="1010" height="435" alt="image" src="https://github.com/user-attachments/assets/7697b614-54c4-4155-96be-174730680a80" />


```sql
INSERT INTO Customers (CustomerID, Name, Address)
VALUES (304, 'Peter Parker', 'Spider St');
```

**Output:**

<img width="1232" height="383" alt="image" src="https://github.com/user-attachments/assets/49c04ac9-a498-4454-8dcd-7cc81fc114a5" />


**Question 5**
---
<img width="1058" height="492" alt="image" src="https://github.com/user-attachments/assets/2c8d3ef2-a656-4af3-b60d-4d73097d7e52" />


```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
SELECT RollNo, Name, Gender, Subject, MARKS
FROM Archived_students;
```

**Output:**

<img width="1232" height="385" alt="image" src="https://github.com/user-attachments/assets/c94afb42-1adc-4a02-b7fc-ee3752bbf094" />

**Question 6**
---
<img width="1227" height="312" alt="image" src="https://github.com/user-attachments/assets/afe5c610-9079-4a2b-97f6-570768e25611" />


```sql
REATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1225" height="357" alt="image" src="https://github.com/user-attachments/assets/47f20691-48a2-43c6-a488-2af205c52d07" />


**Question 7**
---
<img width="1218" height="521" alt="image" src="https://github.com/user-attachments/assets/e5630886-20cc-4c49-9e35-ab3ac2860840" />


```sql
INSERT INTO Products (ProductID, Name, Category)
VALUES (106, 'Fitness Tracker', 'Wearables');

INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (107, 'Laptop', 'Electronics', 999.99, 50);

INSERT INTO Products (ProductID, Name, Category, Stock)
VALUES (108, 'Wireless Earbuds', 'Accessories', 100);
```

**Output:**

<img width="1232" height="376" alt="image" src="https://github.com/user-attachments/assets/1f2596af-53da-4555-a2b0-01a23f616032" />

**Question 8**
---
<img width="1125" height="435" alt="image" src="https://github.com/user-attachments/assets/1a32a1f2-bcd0-421a-8869-84d2e3d96625" />


```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id)
        REFERENCES company(com_id)
        ON UPDATE SET NULL
        ON DELETE SET NULL
);
```

**Output:**

<img width="1217" height="425" alt="image" src="https://github.com/user-attachments/assets/e85c80b1-2a5a-4d98-84e4-ff1ea32a90e1" />


**Question 9**
---
<img width="896" height="361" alt="image" src="https://github.com/user-attachments/assets/ce3972ca-fa66-49f6-b513-e265c7db8ecb" />


```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL,
    Price REAL CHECK (Price > 0),
    Stock INTEGER CHECK (Stock >= 0)
);
```

**Output:**

<img width="1237" height="356" alt="image" src="https://github.com/user-attachments/assets/2c147e53-aefe-451b-b819-a42ea9eb9cc2" />


**Question 10**
---
<img width="1152" height="617" alt="image" src="https://github.com/user-attachments/assets/d6db0d7b-0476-4ab3-9f6d-26db87537562" />


```sql
ALTER TABLE Student_details
ADD COLUMN State TEXT;
```

**Output:**

<img width="1220" height="326" alt="image" src="https://github.com/user-attachments/assets/ce3e048e-140b-4615-b63b-59cb52bd73a5" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
