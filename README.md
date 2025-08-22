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
```sql
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


## 14. 🔗 FOREIGN KEYS

👉 Explanation:

A foreign key links two tables.

It ensures that the value in one table must exist in another (maintains relationships).

👉 Commands:
```sql
CREATE TABLE enrollments (
    enrollment_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
-- Create enrollments with foreign keys → student_id references students, course_id references courses.
-- Try inserting an enrollment with a student_id that doesn’t exist → should fail.
```


## 15. 🤝 JOINS

👉 Explanation:

Combine data from multiple tables.

👉 Types:

INNER JOIN → rows with matching values.

LEFT JOIN → all rows from left table, matching from right.

RIGHT JOIN → all rows from right table, matching from left.

FULL JOIN → all rows from both tables (not directly in MySQL, use UNION).

👉 Commands:
```sql
-- Inner Join: Students + Enrollments
SELECT s.first_name, c.course_name
FROM students s
INNER JOIN enrollments e ON s.id = e.student_id
INNER JOIN courses c ON e.course_id = c.course_id;

-- Left Join: All students even if not enrolled
SELECT s.first_name, c.course_name
FROM students s
LEFT JOIN enrollments e ON s.id = e.student_id
LEFT JOIN courses c ON e.course_id = c.course_id;

```


## 16. 🧮 FUNCTIONS

👉 Explanation:
MySQL has built-in functions for calculations, strings, and dates.

👉 Examples:
```sql
-- Math
SELECT AVG(age), MAX(age), MIN(age) FROM students;

-- String
SELECT UPPER(first_name), LENGTH(last_name) FROM students;

-- Date
SELECT YEAR(dob), MONTH(dob), DAY(dob) FROM students;

```


## 17. ⚖️ AND, OR, NOT

👉 Explanation:

Combine conditions in WHERE.

👉 Commands:
```sql
-- AND
SELECT * FROM students WHERE age > 18 AND last_name = 'Yadav';

-- OR
SELECT * FROM students WHERE age = 20 OR age = 21;

-- NOT
SELECT * FROM students WHERE NOT last_name = 'Yadav';

```


## 18. 🃏 WILD CARDS

👉 Explanation:
Use LIKE with % (any number of chars) and _ (single char).

👉 Commands:
```sql
-- Starts with V
SELECT * FROM students WHERE first_name LIKE 'V%';

-- Ends with s
SELECT * FROM students WHERE first_name LIKE '%s';

-- Contains "ika"
SELECT * FROM students WHERE first_name LIKE '%ika%';

-- 4-letter names
SELECT * FROM students WHERE first_name LIKE '____';

```


## 19. 📑 ORDER BY

👉 Explanation:
Used to sort the results in ascending (ASC) or descending (DESC) order.

👉 Commands:
```sql
-- Ascending (default)
SELECT * FROM students ORDER BY age;

-- Descending
SELECT * FROM students ORDER BY age DESC;

-- Multiple columns
SELECT * FROM students ORDER BY last_name, first_name;

```


## 20. 🎯 LIMIT

👉 Explanation:
Restricts the number of rows returned. Often used for pagination.

👉 Commands:
```sql
-- First 5 students
SELECT * FROM students LIMIT 5;

-- Skip first 3, get next 2
SELECT * FROM students LIMIT 3,2;

```


## 21. 🔗 UNIONS

👉 Explanation:
Combine results of two queries.

UNION removes duplicates.

UNION ALL keeps duplicates.

👉 Commands:
```sql
SELECT first_name FROM students
UNION
SELECT name FROM customers;

-- With duplicates
SELECT first_name FROM students
UNION ALL
SELECT name FROM customers;

```


## 22. 🔁 SELF JOINS

👉 Explanation:
A table joins with itself (useful for hierarchical data like employees and managers).

👉 Commands:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    manager_id INT
);

-- Example self join
SELECT e.emp_name AS Employee, m.emp_name AS Manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.emp_id;

```


## 23. 👓 VIEWS

👉 Explanation:
A view is like a saved query — a virtual table you can query like a normal table.

👉 Commands:
```sql
-- Create view
CREATE VIEW student_courses AS
SELECT s.first_name, s.last_name, c.course_name
FROM students s
JOIN enrollments e ON s.id = e.student_id
JOIN courses c ON e.course_id = c.course_id;

-- Query the view
SELECT * FROM student_courses;

-- Drop view
DROP VIEW student_courses;

```


## 24. 📌 INDEXES

👉 Explanation:
Indexes make searches faster (like an index in a book).

Primary key automatically creates an index.

You can add indexes on other columns.

👉 Commands:
```sql
-- Create index
CREATE INDEX idx_lastname ON students(last_name);

-- Show indexes
SHOW INDEX FROM students;

-- Drop index
DROP INDEX idx_lastname ON students;

```

## 25. 🔍 SUBQUERIES

👉 Explanation:
A query inside another query.

👉 Types:

Single-row (returns one value).

Multi-row (returns multiple values).

👉 Commands:
```sql
-- Find students older than average age
SELECT * FROM students
WHERE age > (SELECT AVG(age) FROM students);

-- Find students enrolled in a course called "Math"
SELECT * FROM students
WHERE id IN (
    SELECT student_id FROM enrollments
    WHERE course_id = (SELECT course_id FROM courses WHERE course_name = 'Math')
);

```

## 26. 📊 GROUP BY

👉 Explanation:
Groups rows and allows aggregate functions (COUNT, SUM, AVG, etc.).

👉 Commands:
```sql
-- Count students by age
SELECT age, COUNT(*) AS total
FROM students
GROUP BY age;

-- Total enrollments per course
SELECT course_id, COUNT(*) AS total_enrolled
FROM enrollments
GROUP BY course_id;

```

## 27. 🔄 ROLLUP

👉 Explanation:
Used with GROUP BY to get subtotals and grand totals.

👉 Commands:
```sql
-- Count students by age + total
SELECT age, COUNT(*) 
FROM students
GROUP BY age WITH ROLLUP;

```


## 28. 🗑 ON DELETE

👉 Explanation:
Defines what happens to child rows when parent rows are deleted (with foreign keys).

👉 Options:

ON DELETE CASCADE → delete child rows too.

ON DELETE SET NULL → set child column to NULL.

ON DELETE RESTRICT → prevent deletion if child exists.
```sql
CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES students(id) ON DELETE CASCADE
);
```

## 29. ⚙️ STORED PROCEDURES

👉 Explanation:
A stored procedure is like a function you save inside MySQL. You can call it anytime instead of rewriting queries.

👉 Commands:
```sql
-- Create procedure
DELIMITER //
CREATE PROCEDURE GetAllStudents()
BEGIN
    SELECT * FROM students;
END //
DELIMITER ;

-- Call procedure
CALL GetAllStudents();

-- Procedure with parameter
DELIMITER //
CREATE PROCEDURE GetStudentsByAge(IN min_age INT)
BEGIN
    SELECT * FROM students WHERE age >= min_age;
END //
DELIMITER ;

-- Call with argument
CALL GetStudentsByAge(20);

```

## 30. ⏱ TRIGGERS

👉 Explanation:
A trigger automatically runs when something happens in a table (INSERT, UPDATE, DELETE).
Used for logging, auditing, enforcing rules, etc.

👉 Commands:
```sql
-- Create trigger: log every new student
CREATE TABLE student_log (
    log_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    action_time DATETIME
);

DELIMITER //
CREATE TRIGGER after_student_insert
AFTER INSERT ON students
FOR EACH ROW
BEGIN
    INSERT INTO student_log(student_id, action_time)
    VALUES (NEW.id, NOW());
END //
DELIMITER ;

-- Test: Insert a student
INSERT INTO students (first_name, last_name, age, dob)
VALUES ('Rohit', 'Sharma', 21, '2004-03-12');

-- Check logs
SELECT * FROM student_log;

```
