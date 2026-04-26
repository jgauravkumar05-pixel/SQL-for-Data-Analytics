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
