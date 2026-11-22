# SQL Fundamentals - [11-21-2026]

## What This Covers

This lab covers database fundamentals and the practical use of SQL (Structured Query Language) to interact with relational databases. It begins with understanding database structures, relational and non-relational databases, tables, rows, columns, primary keys, and foreign keys. I worked with MySQL through the Linux terminal, created a database and table, inspected database structures, and modified an existing table using SQL statements. The lab further explores CRUD operations (Create, Read, Update, Delete), SQL clauses, logical and comparison operators, and built-in string and aggregate functions. I also worked with the provided thm_books, thm_books2, task_4_db, and tools_db databases to practise retrieving, filtering, grouping, sorting, and analysing stored information.

## Key Concepts

* Understanding databases as organised collections of structured information that can be accessed, modified, and analysed.
* Understanding the difference between relational databases (SQL) and non-relational databases (NoSQL).
* Understanding database structures, including tables, rows, and columns.
* Understanding common data types such as strings, integers, decimals, and dates.
* Understanding primary keys and their role in uniquely identifying records within a table.
* Understanding foreign keys and how they establish relationships between tables.
* Understanding Database Management Systems (DBMS) such as MySQL, MongoDB, Oracle Database, and MariaDB.
* Understanding SQL as a language used to query, define, and manipulate relational database information.
* Connecting to MySQL through the Linux terminal.
* Creating, listing, selecting, and managing databases using SQL statements.
* Creating tables with defined columns, data types, primary keys, AUTO_INCREMENT, and NOT NULL constraints.
* Inspecting database structures using SHOW DATABASES, SHOW TABLES, and DESCRIBE.
* Modifying existing table structures using the ALTER TABLE statement.
* Understanding CRUD operations using INSERT, SELECT, UPDATE, and DELETE.
* Retrieving complete or specific columns from database tables using SELECT.
* Understanding how WHERE filters records based on specified conditions.
* Using DISTINCT to retrieve unique values and GROUP BY to group records.
* Using ORDER BY with ASC and DESC to sort query results.
* Using HAVING to filter grouped results after aggregation.
* Understanding logical operators such as LIKE, AND, OR, NOT, and BETWEEN.
* Using comparison operators such as =, !=, <, >, <=, and >= to filter database records.
* Using string functions such as CONCAT(), GROUP_CONCAT(), SUBSTRING(), and LENGTH().
* Using aggregate functions such as COUNT(), SUM(), MAX(), and MIN().
* Querying the provided tools_db database and its hacking_tools table to retrieve and analyse tool information.
* Using SQL queries to identify specific records, categories, counts, and values within database tables.

## Commands/Tools Used

```bash
# Connecting to MySQL:
mysql -u root -p
```

```sql
-- Database Statements:

-- Create a Database:
CREATE DATABASE thm_bookmarket_db;

-- Display Available Databases:
SHOW DATABASES;

-- Select an Active Database:
USE thm_bookmarket_db;


-- Table Statements:

-- Create a Table:
CREATE TABLE book_inventory (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    book_name VARCHAR(255) NOT NULL,
    publication_date DATE
);

-- Display Tables:
SHOW TABLES;

-- Describe Table Structure:
DESCRIBE book_inventory;

-- Add a New Column:
ALTER TABLE book_inventory
ADD page_count INT;
```

```sql
-- Database Enumeration:

SHOW DATABASES;

-- Select the Challenge Database:
USE task_4_db;

-- Enumerate Tables:
SHOW TABLES;


-- Working with the Provided Databases:

USE thm_books;

USE thm_books2;

USE tools_db;
```

```sql
-- CRUD Operations:

-- CREATE - INSERT:
INSERT INTO books (id, name, published_date, description)
VALUES (
    1,
    "Android Security Internals",
    "2014-10-14",
    "An In-Depth Guide to Android's Security Architecture"
);

-- READ - SELECT All Columns:
SELECT * FROM books;

-- READ - SELECT Specific Columns:
SELECT name, description FROM books;

-- UPDATE Existing Records:
UPDATE books
SET description = "An In-Depth Guide to Android's Security Architecture."
WHERE id = 1;

-- DELETE Syntax Covered:
-- The example was not executed to preserve the provided records.
DELETE FROM books WHERE id = 1;
```

```sql
-- SQL Clauses:

-- DISTINCT - Retrieve Unique Values:
SELECT DISTINCT name FROM books;

-- GROUP BY - Group Records:
SELECT name, COUNT(*)
FROM books
GROUP BY name;

-- ORDER BY - Ascending Order:
SELECT *
FROM books
ORDER BY published_date ASC;

-- ORDER BY - Descending Order:
SELECT *
FROM books
ORDER BY published_date DESC;

-- HAVING - Filter Grouped Results:
SELECT name, COUNT(*)
FROM books
GROUP BY name
HAVING name LIKE '%Hack%';
```

```sql
-- Logical Operators:

-- LIKE:
SELECT *
FROM books
WHERE description LIKE "%guide%";

-- AND:
SELECT *
FROM books
WHERE category = "Offensive Security"
AND name = "Bug Bounty Bootcamp";

-- OR:
SELECT *
FROM books
WHERE name LIKE "%Android%"
OR name LIKE "%iOS%";

-- NOT:
SELECT *
FROM books
WHERE NOT description LIKE "%guide%";

-- BETWEEN:
SELECT *
FROM books
WHERE id BETWEEN 2 AND 4;
```

```sql
-- Comparison Operators:

-- Equal To:
SELECT *
FROM books
WHERE name = "Designing Secure Software";

-- Not Equal To:
SELECT *
FROM books
WHERE category != "Offensive Security";

-- Less Than:
SELECT *
FROM books
WHERE published_date < "2020-01-01";

-- Greater Than:
SELECT *
FROM books
WHERE published_date > "2020-01-01";

-- Less Than or Equal To:
SELECT *
FROM books
WHERE published_date <= "2021-11-15";

-- Greater Than or Equal To:
SELECT *
FROM books
WHERE published_date >= "2021-11-02";
```

```sql
-- String Functions:

-- CONCAT:
SELECT CONCAT(name, " is a type of ", category, " book.") AS book_info
FROM books;

-- GROUP_CONCAT:
SELECT category, GROUP_CONCAT(name SEPARATOR ", ") AS books
FROM books
GROUP BY category;

-- SUBSTRING:
SELECT SUBSTRING(published_date, 1, 4) AS published_year
FROM books;

-- LENGTH:
SELECT LENGTH(name) AS name_length
FROM books;


-- Aggregate Functions:

-- COUNT:
SELECT COUNT(*) AS total_books
FROM books;

-- SUM:
-- Demonstrated as an example in the lesson.
SELECT SUM(price) AS total_price
FROM books;

-- MAX:
SELECT MAX(published_date) AS latest_book
FROM books;

-- MIN:
SELECT MIN(published_date) AS earliest_book
FROM books;
```

## What I learned

I learned how relational databases are structured and how SQL can be used to retrieve and manipulate stored information. I started by understanding database types, tables, rows, columns, primary keys, and foreign keys. I then connected to MySQL through the terminal, created my own database and book_inventory table, listed available databases and tables, inspected table structures, and added a new column using ALTER TABLE. I explored the provided databases, including task_4_db, thm_books, thm_books2, and tools_db, and practised retrieving records using SELECT and modifying existing records using UPDATE. I then worked with DISTINCT, GROUP BY, ORDER BY, and HAVING to organise and filter query results. I also practised logical and comparison operators to retrieve records based on specific conditions and used string and aggregate functions to combine, count, calculate, and analyse database values. Finally, I applied these SQL concepts to the hacking_tools table in tools_db to investigate tool names, categories, amounts, and other database information. This lab gave me practical experience in database enumeration and SQL-based data analysis, which are important skills for understanding how web applications store and manage information and for investigating SQL-related security vulnerabilities.
