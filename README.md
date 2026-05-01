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

## 📘 Day 3: SQL Data Analysis

Topic: Aggregate Functions + GROUP BY + HAVING

Day 3 focuses on analyzing data using aggregate functions, grouping, and grouped filtering.

## 🧠 What Day 3 Covers

🔹 COUNT()  
🔹 SUM()  
🔹 AVG()  
🔹 MAX()  
🔹 MIN()  
🔹 GROUP BY  
🔹 HAVING  
🔹 WHERE vs HAVING  
🔹 GROUP BY vs ORDER BY  

## 🎯 Day 3 Purpose

The purpose of Day 3 is to understand how to summarize and analyze data using SQL.  
This is where SQL starts becoming useful for real Data Analyst work.

## 💻 Day 3 Practical Queries

```sql
-- 1. Count total students
SELECT COUNT(*) AS total_students
FROM students;

-- 2. Find total marks of all students
SELECT SUM(marks) AS total_marks
FROM students;

-- 3. Find average marks of all students
SELECT AVG(marks) AS average_marks
FROM students;

-- 4. Find highest marks
SELECT MAX(marks) AS highest_marks
FROM students;

-- 5. Find lowest marks
SELECT MIN(marks) AS lowest_marks
FROM students;

-- 6. Count students city-wise
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city;

-- 7. Find average marks city-wise
SELECT city, AVG(marks) AS average_marks
FROM students
GROUP BY city;

-- 8. Count students course-wise
SELECT course, COUNT(*) AS total_students
FROM students
GROUP BY course;

-- 9. Find average marks course-wise
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course;

-- 10. Find highest marks course-wise
SELECT course, MAX(marks) AS highest_marks
FROM students
GROUP BY course;

-- 11. Find lowest marks city-wise
SELECT city, MIN(marks) AS lowest_marks
FROM students
GROUP BY city;

-- 12. Count students gender-wise
SELECT gender, COUNT(*) AS total_students
FROM students
GROUP BY gender;

-- 13. Count students admission-year-wise
SELECT admission_year, COUNT(*) AS total_students
FROM students
GROUP BY admission_year;

-- 14. Show cities where student count is more than 5
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city
HAVING COUNT(*) > 5;

-- 15. Show courses where average marks are greater than 70
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course
HAVING AVG(marks) > 70;

-- 16. Show cities where average marks are less than 60
SELECT city, AVG(marks) AS average_marks
FROM students
GROUP BY city
HAVING AVG(marks) < 60;

-- 17. Show course-wise total marks
SELECT course, SUM(marks) AS total_marks
FROM students
GROUP BY course;

-- 18. Show city-wise count sorted from highest to lowest
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city
ORDER BY total_students DESC;

-- 19. Show course-wise average marks sorted highest first
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course
ORDER BY average_marks DESC;

-- 20. Show courses where total students are more than 10, sorted highest first
SELECT course, COUNT(*) AS total_students
FROM students
GROUP BY course
HAVING COUNT(*) > 10
ORDER BY total_students DESC;
🧠 Day 3 Scenario-Based Queries
-- 1. Find how many students are there in each city
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city;

-- 2. Find average marks of each course
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course;

-- 3. Find total marks scored by each course
SELECT course, SUM(marks) AS total_marks
FROM students
GROUP BY course;

-- 4. Find the highest marks in each city
SELECT city, MAX(marks) AS highest_marks
FROM students
GROUP BY city;

-- 5. Find the lowest marks in each course
SELECT course, MIN(marks) AS lowest_marks
FROM students
GROUP BY course;

-- 6. Find cities where more than 5 students are present
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city
HAVING COUNT(*) > 5;

-- 7. Find courses where average marks are greater than 70
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course
HAVING AVG(marks) > 70;

-- 8. Find gender-wise average marks
SELECT gender, AVG(marks) AS average_marks
FROM students
GROUP BY gender;

-- 9. Find admission-year-wise student count
SELECT admission_year, COUNT(*) AS total_students
FROM students
GROUP BY admission_year;

-- 10. Find city-wise average marks only for students with marks greater than 50
SELECT city, AVG(marks) AS average_marks
FROM students
WHERE marks > 50
GROUP BY city;

-- 11. Find course-wise count where only Delhi students are included
SELECT course, COUNT(*) AS total_students
FROM students
WHERE city = 'Delhi'
GROUP BY course;

-- 12. Find cities where average marks are greater than 60, sorted highest first
SELECT city, AVG(marks) AS average_marks
FROM students
GROUP BY city
HAVING AVG(marks) > 60
ORDER BY average_marks DESC;

-- 13. Find courses where total marks are more than 500
SELECT course, SUM(marks) AS total_marks
FROM students
GROUP BY course
HAVING SUM(marks) > 500;

-- 14. Find gender-wise student count in each course
SELECT course, gender, COUNT(*) AS total_students
FROM students
GROUP BY course, gender;

-- 15. Find course-wise average marks for students from Delhi or Mumbai
SELECT course, AVG(marks) AS average_marks
FROM students
WHERE city IN ('Delhi', 'Mumbai')
GROUP BY course;
⚖️ Important Differences
COUNT(*) vs COUNT(column)
COUNT(*)	COUNT(column)
Counts all rows	Counts only non-NULL values in that column
Includes rows even if some columns are NULL	Ignores NULL values in selected column
Best for total records	Best for available values in a column

Memory line: COUNT(*) counts rows, COUNT(column) counts filled values.

WHERE vs HAVING
WHERE	HAVING
Filters rows	Filters groups
Runs before GROUP BY	Runs after GROUP BY
Used on normal columns	Used on aggregate results
Example: WHERE marks > 70	Example: HAVING AVG(marks) > 70

Memory line: WHERE filters raw data, HAVING filters summary data.

GROUP BY vs ORDER BY
GROUP BY	ORDER BY
Combines similar rows into groups	Sorts the final result
Used for analysis	Used for arrangement
Usually used with aggregates	Used for ascending/descending order
Example: city-wise count	Example: highest to lowest marks

Memory line: GROUP BY summarizes, ORDER BY organizes.

SUM() vs AVG()
SUM()	AVG()
Gives total value	Gives average value
Useful for total sales/marks	Useful for performance comparison
Adds all values	Divides total by count

Memory line: SUM tells total, AVG tells typical value.

MIN() vs MAX()
MIN()	MAX()
Finds lowest value	Finds highest value
Useful for minimum marks/salary	Useful for maximum marks/salary
Shows bottom value	Shows top value

Memory line: MIN finds bottom, MAX finds top.

📊 SQL Flow
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY;
🏆 Day 3 Key Takeaway

Day 1 helped me view data.
Day 2 helped me filter data.
Day 3 helped me analyze data using aggregate functions, GROUP BY, and HAVING.

SQL is not about memorizing queries, it is about understanding data and applying logic.


Bhai Day 4 ke liye GitHub README me ye add karo.
README edit करो → Day 3 ke niche bottom me paste करो → Commit message: Add Day 4 SQL joins notes

---

## 📘 Day 4: SQL JOINS

Topic: Table Connection / SQL JOINS

Day 4 focuses on connecting multiple tables using SQL JOINs.

## 🧠 What Day 4 Covers

🔹 What is a JOIN  
🔹 Why JOIN is used in SQL  
🔹 How to connect two tables  
🔹 ON condition  
🔹 Table aliases  
🔹 INNER JOIN  
🔹 LEFT JOIN  
🔹 RIGHT JOIN  
🔹 CROSS JOIN  
🔹 SELF JOIN  
🔹 JOIN with WHERE  
🔹 JOIN with GROUP BY  

## 🎯 Day 4 Purpose

The purpose of Day 4 is to understand how to combine data from two or more tables.  
In real databases, data is usually stored in multiple connected tables, so JOIN is one of the most important SQL concepts for Data Analysts.

## 🧠 Day 4 Short Notes

### What is JOIN?

JOIN is used to combine data from two or more tables based on a related column.

```sql
SELECT s.student_name, c.course_name
FROM students s
JOIN courses c
ON s.course_id = c.course_id;

Memory line: JOIN = connecting related tables.

ON Condition

ON tells SQL which columns should match between two tables.

ON s.course_id = c.course_id

Memory line: ON = matching condition.

INNER JOIN

INNER JOIN returns only matching records from both tables.

SELECT s.student_name, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id;

Memory line: INNER JOIN = only matching data.

LEFT JOIN

LEFT JOIN returns all records from the left table and matching records from the right table.
If there is no match, right table columns show NULL.

SELECT s.student_name, c.course_name
FROM students s
LEFT JOIN courses c
ON s.course_id = c.course_id;

Memory line: LEFT JOIN = full left table + matching right data.

RIGHT JOIN

RIGHT JOIN returns all records from the right table and matching records from the left table.

SELECT s.student_name, c.course_name
FROM students s
RIGHT JOIN courses c
ON s.course_id = c.course_id;

Memory line: RIGHT JOIN = full right table + matching left data.

CROSS JOIN

CROSS JOIN returns all possible combinations between rows of two tables.

SELECT *
FROM students
CROSS JOIN courses;

Memory line: CROSS JOIN = all combinations.

SELF JOIN

SELF JOIN means joining a table with itself.

SELECT e.emp_name, m.emp_name AS manager_name
FROM employees e
JOIN employees m
ON e.manager_id = m.emp_id;

Memory line: SELF JOIN = same table joined with itself.

Table Alias

Alias means short temporary name for a table.

students s
courses c

Memory line: Alias = short name for table.

💻 Day 4 Practical JOIN Queries

Assume 2 tables:

students(student_id, student_name, city, course_id, marks)
courses(course_id, course_name, fees)
-- 1. Show student name with course name
SELECT s.student_name, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id;

-- 2. Show all students with their course details
SELECT s.*, c.course_name, c.fees
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id;

-- 3. Show students from Delhi with course name
SELECT s.student_name, s.city, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
WHERE s.city = 'Delhi';

-- 4. Show students with marks greater than 80 and course name
SELECT s.student_name, s.marks, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
WHERE s.marks > 80;

-- 5. Show all students even if course is not assigned
SELECT s.student_name, c.course_name
FROM students s
LEFT JOIN courses c
ON s.course_id = c.course_id;

-- 6. Find students who have no matching course
SELECT s.student_name, s.course_id
FROM students s
LEFT JOIN courses c
ON s.course_id = c.course_id
WHERE c.course_id IS NULL;

-- 7. Show all courses even if no student enrolled
SELECT c.course_name, s.student_name
FROM students s
RIGHT JOIN courses c
ON s.course_id = c.course_id;

-- 8. Find courses with no students
SELECT c.course_name
FROM students s
RIGHT JOIN courses c
ON s.course_id = c.course_id
WHERE s.student_id IS NULL;

-- 9. Count students in each course
SELECT c.course_name, COUNT(s.student_id) AS total_students
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name;

-- 10. Find average marks in each course
SELECT c.course_name, AVG(s.marks) AS average_marks
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name;

-- 11. Show course-wise highest marks
SELECT c.course_name, MAX(s.marks) AS highest_marks
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name;

-- 12. Show course-wise lowest marks
SELECT c.course_name, MIN(s.marks) AS lowest_marks
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name;

-- 13. Show courses having more than 5 students
SELECT c.course_name, COUNT(s.student_id) AS total_students
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name
HAVING COUNT(s.student_id) > 5;

-- 14. Show course-wise average marks greater than 70
SELECT c.course_name, AVG(s.marks) AS average_marks
FROM courses c
LEFT JOIN students s
ON c.course_id = s.course_id
GROUP BY c.course_name
HAVING AVG(s.marks) > 70;

-- 15. Show student name, city, course name, and fees
SELECT s.student_name, s.city, c.course_name, c.fees
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id;

-- 16. Show students enrolled in BCA course
SELECT s.student_name, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
WHERE c.course_name = 'BCA';

-- 17. Show students whose course fee is greater than 50000
SELECT s.student_name, c.course_name, c.fees
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
WHERE c.fees > 50000;

-- 18. Show city-wise student count with course name
SELECT s.city, c.course_name, COUNT(s.student_id) AS total_students
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
GROUP BY s.city, c.course_name;

-- 19. Show all students sorted by course fee highest first
SELECT s.student_name, c.course_name, c.fees
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
ORDER BY c.fees DESC;

-- 20. Show top 5 students with course name based on marks
SELECT s.student_name, s.marks, c.course_name
FROM students s
INNER JOIN courses c
ON s.course_id = c.course_id
ORDER BY s.marks DESC
LIMIT 5;
⚖️ Important Differences
INNER JOIN vs LEFT JOIN
INNER JOIN	LEFT JOIN
Shows only matching records	Shows all records from left table
Unmatched records are removed	Unmatched left records remain with NULL
Best when only connected data is needed	Best when missing/unmatched data is also needed

Memory line: INNER = only match, LEFT = all left + match.

LEFT JOIN vs RIGHT JOIN
LEFT JOIN	RIGHT JOIN
Keeps all records from left table	Keeps all records from right table
Right side becomes NULL if no match	Left side becomes NULL if no match
More commonly used	Less commonly used

Memory line: LEFT keeps left, RIGHT keeps right.

INNER JOIN vs CROSS JOIN
INNER JOIN	CROSS JOIN
Matches rows based on a condition	Combines every row with every row
Uses ON condition	Usually does not need ON
Gives meaningful related data	Gives all possible combinations

Memory line: INNER matches, CROSS combines everything.

ON vs WHERE
ON	WHERE
Defines how tables connect	Filters final result
Used for matching columns	Used for conditions
Connection rule	Filtering rule

Memory line: ON connects, WHERE filters.

JOIN vs UNION
JOIN	UNION
Combines columns from multiple tables	Combines rows from multiple queries
Data is placed side by side	Data is stacked vertically
Needs related columns for matching	Needs same number of columns

Memory line: JOIN adds columns, UNION adds rows.

📊 Complete SQL Flow Till Day 4
SELECT column_name
FROM table1
JOIN table2
ON table1.common_column = table2.common_column
WHERE condition
GROUP BY column_name
HAVING aggregate_condition
ORDER BY column_name;
🏆 Day 4 Key Takeaway

Day 1 helped me view data.
Day 2 helped me filter data.
Day 3 helped me analyze data.
Day 4 helped me connect multiple tables using JOINs.

JOIN is used when required data is stored in more than one table.



-- SQL MASTER — DAY 5
-- Topic: Subqueries
-- ==========================================

CREATE DATABASE sql_master_day5;
USE sql_master_day5;

-- ==========================================
-- TABLE 1: students
-- ==========================================

CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    city VARCHAR(50),
    course_id INT,
    marks INT
);

INSERT INTO students (student_id, student_name, city, course_id, marks)
VALUES
(1, 'Rahul', 'Delhi', 101, 85),
(2, 'Amit', 'Mumbai', 102, 72),
(3, 'Neha', 'Delhi', 101, 91),
(4, 'Riya', 'Pune', 103, 64),
(5, 'Karan', 'Jaipur', NULL, 55),
(6, 'Simran', 'Mumbai', 104, 88),
(7, 'Mohit', 'Delhi', 102, 45),
(8, 'Anjali', 'Pune', 105, 78);

-- ==========================================
-- TABLE 2: courses
-- ==========================================

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50),
    fees INT
);

INSERT INTO courses (course_id, course_name, fees)
VALUES
(101, 'BCA', 40000),
(102, 'BBA', 55000),
(103, 'B.Tech', 90000),
(104, 'MBA', 120000),
(105, 'Data Analytics', 70000),
(106, 'Digital Marketing', 30000);

-- ==========================================
-- DAY 5 PRACTICAL SUBQUERY QUESTIONS
-- ==========================================

-- 1. Find students whose marks are greater than average marks
SELECT student_name, marks
FROM students
WHERE marks > (SELECT AVG(marks) FROM students);

-- 2. Find the student with highest marks
SELECT student_name, marks
FROM students
WHERE marks = (SELECT MAX(marks) FROM students);

-- 3. Find the student with lowest marks
SELECT student_name, marks
FROM students
WHERE marks = (SELECT MIN(marks) FROM students);

-- 4. Find students whose marks are less than average marks
SELECT student_name, marks
FROM students
WHERE marks < (SELECT AVG(marks) FROM students);

-- 5. Find students enrolled in courses with fees greater than 50000
SELECT student_name, course_id
FROM students
WHERE course_id IN (
    SELECT course_id
    FROM courses
    WHERE fees > 50000
);

-- 6. Find students enrolled in courses with fees less than 60000
SELECT student_name, course_id
FROM students
WHERE course_id IN (
    SELECT course_id
    FROM courses
    WHERE fees < 60000
);

-- 7. Find students enrolled in the course with highest fee
SELECT student_name, course_id
FROM students
WHERE course_id = (
    SELECT course_id
    FROM courses
    WHERE fees = (SELECT MAX(fees) FROM courses)
);

-- 8. Find students enrolled in the course with lowest fee
SELECT student_name, course_id
FROM students
WHERE course_id = (
    SELECT course_id
    FROM courses
    WHERE fees = (SELECT MIN(fees) FROM courses)
);

-- 9. Find students whose course fee is equal to 40000
SELECT student_name, course_id
FROM students
WHERE course_id IN (
    SELECT course_id
    FROM courses
    WHERE fees = 40000
);

-- 10. Find students whose course is BCA
SELECT student_name, course_id
FROM students
WHERE course_id = (
    SELECT course_id
    FROM courses
    WHERE course_name = 'BCA'
);

-- 11. Find students whose course is BBA
SELECT student_name, course_id
FROM students
WHERE course_id = (
    SELECT course_id
    FROM courses
    WHERE course_name = 'BBA'
);

-- 12. Find students whose course fee is above average course fee
SELECT student_name, course_id
FROM students
WHERE course_id IN (
    SELECT course_id
    FROM courses
    WHERE fees > (SELECT AVG(fees) FROM courses)
);

-- 13. Find courses whose fees are greater than average fees
SELECT course_name, fees
FROM courses
WHERE fees > (SELECT AVG(fees) FROM courses);

-- 14. Find courses whose fees are less than average fees
SELECT course_name, fees
FROM courses
WHERE fees < (SELECT AVG(fees) FROM courses);

-- 15. Find students who have no course assigned
SELECT student_name, course_id
FROM students
WHERE course_id IS NULL;

-- 16. Find students whose course exists in the courses table
SELECT student_name, course_id
FROM students
WHERE course_id IN (
    SELECT course_id
    FROM courses
);

-- 17. Find courses where at least one student is enrolled
SELECT course_name
FROM courses
WHERE course_id IN (
    SELECT course_id
    FROM students
);

-- 18. Find courses where no student is enrolled
SELECT course_name
FROM courses
WHERE course_id NOT IN (
    SELECT course_id
    FROM students
    WHERE course_id IS NOT NULL
);

-- 19. Find students whose marks are greater than Rahul's marks
SELECT student_name, marks
FROM students
WHERE marks > (
    SELECT marks
    FROM students
    WHERE student_name = 'Rahul'
);

-- 20. Find students whose marks are less than Amit's marks
SELECT student_name, marks
FROM students
WHERE marks < (
    SELECT marks
    FROM students
    WHERE student_name = 'Amit'
);

-- 21. Find second highest marks
SELECT MAX(marks) AS second_highest_marks
FROM students
WHERE marks < (
    SELECT MAX(marks)
    FROM students
);

-- 22. Find student with second highest marks
SELECT student_name, marks
FROM students
WHERE marks = (
    SELECT MAX(marks)
    FROM students
    WHERE marks < (SELECT MAX(marks) FROM students)
);

-- 23. Find students from the same city as Rahul
SELECT student_name, city
FROM students
WHERE city = (
    SELECT city
    FROM students
    WHERE student_name = 'Rahul'
);

-- 24. Find students who are not from Rahul's city
SELECT student_name, city
FROM students
WHERE city <> (
    SELECT city
    FROM students
    WHERE student_name = 'Rahul'
);

-- 25. Find students whose marks are greater than the lowest marks
SELECT student_name, marks
FROM students
WHERE marks > (
    SELECT MIN(marks)
    FROM students
);

GitHub README ke liye title:

# SQL Master - Day 5: Subqueries

Today I practiced SQL Subqueries.

## Topics Covered
- What is a Subquery
- Inner Query and Outer Query
- Single-row Subquery
- Multiple-row Subquery
- Subquery with WHERE
- Subquery with IN
- Subquery with MAX(), MIN(), AVG()
- Above Average Records
- Highest and Lowest Records
- Second Highest Marks
- Subquery vs JOIN

## Key Learning
A subquery is a query written inside another query.  
It is used when one query depends on the result of another query.

## Memory Line
Subquery = Query inside Query.




-- SQL MASTER — DAY 6
-- Topic: CTE + Views
-- ==========================================

CREATE DATABASE sql_master_day6;
USE sql_master_day6;

-- ==========================================
-- TABLE: students
-- ==========================================

CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    city VARCHAR(50),
    course VARCHAR(50),
    gender VARCHAR(10),
    admission_year INT,
    marks INT
);

INSERT INTO students 
(student_id, student_name, city, course, gender, admission_year, marks)
VALUES
(1, 'Rahul', 'Delhi', 'BCA', 'Male', 2023, 85),
(2, 'Amit', 'Mumbai', 'BBA', 'Male', 2022, 72),
(3, 'Neha', 'Delhi', 'BCA', 'Female', 2023, 91),
(4, 'Riya', 'Pune', 'B.Tech', 'Female', 2024, 64),
(5, 'Karan', 'Jaipur', 'BCA', 'Male', 2021, 55),
(6, 'Simran', 'Mumbai', 'MBA', 'Female', 2022, 88),
(7, 'Mohit', 'Delhi', 'BBA', 'Male', 2024, 45),
(8, 'Anjali', 'Pune', 'Data Analytics', 'Female', 2023, 78),
(9, 'Vikas', 'Delhi', 'BCA', 'Male', 2021, 69),
(10, 'Pooja', 'Mumbai', 'MBA', 'Female', 2024, 82);

-- ==========================================
-- PART A: CTE PRACTICE
-- ==========================================

-- 1. Create a CTE to show students with marks greater than 80
WITH high_marks AS (
    SELECT student_id, student_name, marks
    FROM students
    WHERE marks > 80
)
SELECT *
FROM high_marks;

-- 2. Create a CTE to show only Delhi students
WITH delhi_students AS (
    SELECT student_id, student_name, city
    FROM students
    WHERE city = 'Delhi'
)
SELECT *
FROM delhi_students;

-- 3. Create a CTE to calculate average marks
WITH avg_marks AS (
    SELECT AVG(marks) AS average_marks
    FROM students
)
SELECT *
FROM avg_marks;

-- 4. Create a CTE to show students above average marks
WITH avg_marks AS (
    SELECT AVG(marks) AS average_marks
    FROM students
)
SELECT student_name, marks
FROM students
WHERE marks > (SELECT average_marks FROM avg_marks);

-- 5. Create a CTE for city-wise student count
WITH city_count AS (
    SELECT city, COUNT(*) AS total_students
    FROM students
    GROUP BY city
)
SELECT *
FROM city_count;

-- 6. Create a CTE to show cities where student count is greater than 2
WITH city_count AS (
    SELECT city, COUNT(*) AS total_students
    FROM students
    GROUP BY city
)
SELECT *
FROM city_count
WHERE total_students > 2;

-- 7. Create a CTE for course-wise average marks
WITH course_avg AS (
    SELECT course, AVG(marks) AS average_marks
    FROM students
    GROUP BY course
)
SELECT *
FROM course_avg;

-- 8. Create a CTE to show courses where average marks are greater than 70
WITH course_avg AS (
    SELECT course, AVG(marks) AS average_marks
    FROM students
    GROUP BY course
)
SELECT *
FROM course_avg
WHERE average_marks > 70;

-- 9. Create a CTE for gender-wise student count
WITH gender_count AS (
    SELECT gender, COUNT(*) AS total_students
    FROM students
    GROUP BY gender
)
SELECT *
FROM gender_count;

-- 10. Create a CTE for admission-year-wise student count
WITH year_count AS (
    SELECT admission_year, COUNT(*) AS total_students
    FROM students
    GROUP BY admission_year
)
SELECT *
FROM year_count;

-- ==========================================
-- PART B: VIEWS PRACTICE
-- ==========================================

-- 11. Create a View for high marks students
CREATE VIEW high_marks_students AS
SELECT student_id, student_name, marks
FROM students
WHERE marks > 80;

SELECT *
FROM high_marks_students;

-- 12. Create a View for Delhi students
CREATE VIEW delhi_students_view AS
SELECT student_id, student_name, city
FROM students
WHERE city = 'Delhi';

SELECT *
FROM delhi_students_view;

-- 13. Create a View for basic student details
CREATE VIEW student_basic AS
SELECT student_id, student_name, city, course
FROM students;

SELECT *
FROM student_basic;

-- 14. Create a View for course-wise average marks
CREATE VIEW course_average_marks AS
SELECT course, AVG(marks) AS average_marks
FROM students
GROUP BY course;

SELECT *
FROM course_average_marks;

-- 15. Create a View for city-wise student count
CREATE VIEW city_student_count AS
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city;

SELECT *
FROM city_student_count;

-- 16. Create a View for students above average marks
CREATE VIEW above_average_students AS
SELECT student_id, student_name, marks
FROM students
WHERE marks > (SELECT AVG(marks) FROM students);

SELECT *
FROM above_average_students;

-- 17. Create a View for female students
CREATE VIEW female_students AS
SELECT student_id, student_name, gender, marks
FROM students
WHERE gender = 'Female';

SELECT *
FROM female_students;

-- 18. Create a View for BCA students
CREATE VIEW bca_students AS
SELECT student_id, student_name, course, marks
FROM students
WHERE course = 'BCA';

SELECT *
FROM bca_students;

-- 19. Create a View for students sorted by marks
CREATE VIEW students_by_marks AS
SELECT student_id, student_name, marks
FROM students
ORDER BY marks DESC;

SELECT *
FROM students_by_marks;

-- 20. Create a View for yearly admission summary
CREATE VIEW yearly_admission_summary AS
SELECT admission_year, COUNT(*) AS total_students
FROM students
GROUP BY admission_year;

SELECT *
FROM yearly_admission_summary;

-- ==========================================
-- MEMORY LINE
-- CTE = temporary result for one query
-- View = saved query for reuse
-- ==========================================
✅ README.md Content
# SQL Master - Day 6: CTE + Views

Today I learned and practiced **CTE and Views** in SQL.

## Topics Covered

- What is CTE
- WITH keyword
- CTE with WHERE
- CTE with GROUP BY
- CTE for average marks
- CTE for city-wise count
- CTE for course-wise average
- What is View
- Simple View
- Complex View
- Updatable View
- Read-only View
- CTE vs View
- View vs Table
- CTE vs Subquery

## Key Learning

A CTE is a temporary result set created using the WITH keyword.  
It is mainly used to make complex queries clean and readable.

A View is a saved SQL query that behaves like a virtual table.  
It is mainly used when we want to reuse the same query again and again.

## Memory Lines

CTE = temporary result for one query.  
View = saved query for reuse.

## Confidence Statement

I can retrieve, filter, analyze, join, use subqueries, and write reusable SQL logic using CTEs and Views.
