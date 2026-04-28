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
