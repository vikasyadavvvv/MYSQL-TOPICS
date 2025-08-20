# MYSQL-TOPICS
## 1. 🏗 DATABASES
👉 Explanation:
- A database is a collection of data organized in tables. In MySQL, a database contains tables, and tables contain rows (records) and columns (fields).
```sql
-- Create a new database
 CREATE DATABASE school;

-- See all databases
 SHOW DATABASES;

-- Use a database
 USE school;

-- Delete a database
 DROP DATABASE school;
```

## 2.📋 TABLES

👉 Explanation:
Tables store your data in rows and columns. Each column has a data type (INT, VARCHAR, DATE, etc.).
```sql
-- Create table
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    dob DATE
);

-- Show all tables
SHOW TABLES;

-- See table structure
DESCRIBE students;

```


## 3. 📝 INSERT ROWS

👉 Explanation:
INSERT adds new data into a table.
```sql
INSERT INTO students (first_name, last_name, age, dob)
VALUES ('Vikas', 'Yadav', 20, '2005-04-02');

```


## 4. SELECT

👉 Explanation:
SELECT fetches data from tables.

👉 Commands:
```sql
-- Get all data
SELECT * FROM students;

-- Get specific columns
SELECT first_name, age FROM students;

-- With condition
SELECT * FROM students WHERE age > 18;

```


## 5. ✏ UPDATE & ❌ DELETE

👉 Explanation:

UPDATE modifies data.

DELETE removes data.

👉 Commands:
```sql
-- Update
UPDATE students SET age = 21 WHERE id = 1;

-- Delete
DELETE FROM students WHERE id = 2;

```


## 6. AUTOCOMMIT, COMMIT, ROLLBACK

👉 Explanation:

By default, MySQL runs in autocommit mode → every query is saved immediately.

If you turn autocommit OFF, you can group queries in a transaction.

COMMIT = save changes permanently.

ROLLBACK = undo changes before commit.

👉 Commands:
```sql
-- Turn off autocommit
SET autocommit = 0;

-- Insert without committing
INSERT INTO students (first_name, last_name, age, dob) 
VALUES ('Test', 'User', 22, '2002-01-01');

-- Rollback
ROLLBACK;

-- Commit
COMMIT;

```


## 7.⏰ CURRENT_DATE() & CURRENT_TIME()

👉 Explanation:
These functions return today’s date and current time.

👉 Commands:
```sql
SELECT CURRENT_DATE();
SELECT CURRENT_TIME();
SELECT NOW(); -- both date and time

```


## 8.🔑 UNIQUE

👉 Explanation:
Ensures all values in a column are different.

👉 Commands:
```sql
CREATE TABLE teachers (
    teacher_id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100) UNIQUE,
    name VARCHAR(50)
);

```

## 9. 🚫 NOT NULL

👉 Explanation:
Column must always have a value.

👉 Commands:
```sql
CREATE TABLE departments (
    dept_id INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL
);

```


## 10. ✅ CHECK

👉 Explanation:
Places a condition on column values.

👉 Commands:
```sql
CREATE TABLE employees (
    emp_id INT AUTO_INCREMENT PRIMARY KEY,
    emp_name VARCHAR(50),
    age INT CHECK (age >= 18)
);

```


## 11. 📌 DEFAULT

👉 Explanation:
If no value is given, a column uses a default value.

👉 Commands:
```sql
CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    status VARCHAR(20) DEFAULT 'available'
);
```


## 12. 🔑 PRIMARY KEYS

👉 Explanation:

Uniquely identifies each row.

A table can have only one primary key.

Automatically NOT NULL + UNIQUE.

👉 Commands:
```sal
CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    email VARCHAR(100)
);

```


## 13.🔢 AUTO_INCREMENT

👉 Explanation:
Automatically generates numbers for a column (usually IDs).

👉 Commands:
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE
);

```
