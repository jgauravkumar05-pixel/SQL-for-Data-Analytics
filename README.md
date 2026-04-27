# SQL for Data Analytics

This repository contains beginner-friendly SQL notes and practical queries for Data Analytics.

## 📘 Day 1: SQL Basics

Topics covered:

🔹 SQL basics  
🔹 Database and DBMS  
🔹 Table, Row, and Column  
🔹 Primary Key and Foreign Key  
🔹 Basic SELECT queries  
🔹 WHERE filtering  
🔹 ORDER BY and LIMIT  
🔹 UPDATE and DELETE basics  
🔹 Practical scenario-based queries  

## 🎯 Purpose

The purpose of this repository is to organize my SQL notes and practice queries in a simple and structured way.

## 💻 Day 1 Practical Queries

```sql
CREATE TABLE students (
  id INT,
  name VARCHAR(50),
  marks INT
);

INSERT INTO students VALUES
(1, 'Rahul', 85),
(2, 'Amit', 90),
(3, 'Neha', 78),
(4, 'Riya', 88),
(5, 'Karan', 70);

SELECT * FROM students;

SELECT name FROM students;

SELECT name, marks FROM students;

SELECT * FROM students WHERE marks > 80;

SELECT * FROM students WHERE marks < 80;

SELECT * FROM students WHERE name = 'Rahul';

SELECT * FROM students WHERE name LIKE 'R%';

SELECT * FROM students ORDER BY marks DESC;

SELECT * FROM students ORDER BY marks DESC LIMIT 3;

UPDATE students SET marks = 95 WHERE name = 'Rahul';


## 📘 Day 2: SQL Filtering Master

Day 2 focuses on filtering and controlling data using SQL conditions.

## 🧠 What Day 2 Covers

🔹 WHERE clause  
🔹 AND operator  
🔹 OR operator  
🔹 BETWEEN operator  
🔹 IN operator  
🔹 NOT operator  
🔹 IS NULL  
🔹 IS NOT NULL  
🔹 Combination filtering  
🔹 Brackets in SQL conditions  

## 🎯 Day 2 Purpose

The purpose of Day 2 is to understand how to filter only the required data from a table.  
In real data analysis, we usually do not work with the full table. We filter data based on business requirements.

## 💻 Day 2 Practical Queries

```sql
-- 1. Show students who scored more than 80 marks
SELECT * FROM students WHERE marks > 80;

-- 2. Show students from Delhi who scored more than 70
SELECT * FROM students WHERE city = 'Delhi' AND marks > 70;

-- 3. Show students from Delhi or Mumbai
SELECT * FROM students WHERE city = 'Delhi' OR city = 'Mumbai';

-- 4. Show students whose marks are between 60 and 90
SELECT * FROM students WHERE marks BETWEEN 60 AND 90;

-- 5. Show students whose names are Rahul or Amit
SELECT * FROM students WHERE name IN ('Rahul', 'Amit');

-- 6. Show students who are not from Delhi
SELECT * FROM students WHERE city != 'Delhi';

-- 7. Show students whose marks are missing
SELECT * FROM students WHERE marks IS NULL;

-- 8. Show students whose marks are present
SELECT * FROM students WHERE marks IS NOT NULL;

-- 9. Show students whose name starts with S and marks greater than 60
SELECT * FROM students WHERE name LIKE 'S%' AND marks > 60;

-- 10. Show students who scored more than 70 in Delhi OR belong to BCA course
SELECT * FROM students
WHERE (marks > 70 AND city = 'Delhi') OR course = 'BCA';
🧠 Day 2 Scenario-Based Queries
-- 1. Students with marks greater than 80 and city Delhi
SELECT * FROM students WHERE marks > 80 AND city = 'Delhi';

-- 2. Students from Delhi or Pune
SELECT * FROM students WHERE city IN ('Delhi', 'Pune');

-- 3. Marks between 50 and 70
SELECT * FROM students WHERE marks BETWEEN 50 AND 70;

-- 4. Students not from Delhi
SELECT * FROM students WHERE city != 'Delhi';

-- 5. Students whose name starts with S and marks greater than 60
SELECT * FROM students WHERE name LIKE 'S%' AND marks > 60;

-- 6. Students with missing marks
SELECT * FROM students WHERE marks IS NULL;

-- 7. Students with valid marks
SELECT * FROM students WHERE marks IS NOT NULL;

-- 8. Students from BCA course
SELECT * FROM students WHERE course = 'BCA';

-- 9. Students from Delhi with marks greater than 70 OR from Mumbai
SELECT * FROM students
WHERE (marks > 70 AND city = 'Delhi') OR city = 'Mumbai';

-- 10. Students not in Pune or Jaipur
SELECT * FROM students WHERE city NOT IN ('Pune', 'Jaipur');
⚖️ Important Differences
AND vs OR
AND	OR
All conditions must be true	At least one condition must be true
Gives narrow result	Gives broad result
Used for strict filtering	Used for flexible filtering
Use when accuracy is needed	Use when options are needed
BETWEEN vs IN
BETWEEN	IN
Used for range	Used for specific values
Used with continuous data	Used with discrete values
Example: marks between 60 and 90	Example: city in Delhi, Pune
NULL vs NOT NULL
NULL	NOT NULL
Missing data	Available data
Use IS NULL	Use IS NOT NULL
Cannot use = NULL	Needs special operator
🏆 Day 2 Key Takeaway

Day 1 made me look at data.
Day 2 helped me filter and control data using conditions.

A Data Analyst is known by how well they filter data.
