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
