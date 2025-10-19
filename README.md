# SQL-CrashCourse

🎓 The Backend & Data Engineer's SQL Masterclass
🎯 Course Objective
By the end of this course, you will be able to:
1. Design, create, and manage relational databases using DDL.
2. Write complex analytical and transactional SQL queries using DQL.
3. Apply advanced techniques like Window Functions and CTEs.
4. Understand and implement database concepts: normalization, constraints, indexing, and optimization.
5. Model real-world data systems, reason about production design, and confidently solve data engineering SQL interview problems from companies like Scribd, Airbnb, Meta, and Netflix.

Course Syllabus
| Section | Title                                   | Key Concepts & Deliverables |
|----------|-----------------------------------------|------------------------------|
| 1 | SQL & Database Foundations | Database concepts, DDL, DML, DQL, DCL, TCL, ACID properties. (Detailed content below) |
| 2 | Building the Base Dataset | Schema design (ERD), Data types, CREATE TABLE with constraints, Sample INSERT data. |
| 3 | Querying Fundamentals | SELECT, WHERE, ORDER BY, Aggregations, GROUP BY, HAVING, JOINs, Subqueries, CTEs, CASE WHEN. |
| 4 | Intermediate SQL | Derived tables, Self-joins, UNION vs UNION ALL, Views, Materialized views, Date/time functions, Handling NULLs. |
| 5 | Advanced SQL | Window functions (RANK, LAG, LEAD, SUM OVER), Pivoting, Query optimization (indexing, execution plans), Recursive CTEs. |
| 6 | Database Design & Normalization | 1NF, 2NF, 3NF, BCNF, Denormalization, ER modeling, Schema evolution (ALTER TABLE). |
| 7 | Real-Life Case Studies & Interview Scenarios | 10+ complex, multi-step analytical challenges on the engagement data, each with SQL, complexity, and production context. |
| 8 | Productionization & ETL Thinking | ETL pipelines, Airflow/dbt concepts, Summary tables, Schema migrations, Error handling, Pseudocode design tasks. |
| 9 | Capstone & Mock Interview | System design challenge: Schema updates, complex SQL query, pseudocode automation, and scaling discussion. |
| 10 | Assessments & Projects | Section Quizzes, 3 Projects, Final Mock Interview Simulation. |


# Section 1 — SQL & Database Foundations
This section lays the groundwork by introducing core database terminology and the five categories of SQL commands.

1.1 The Database Landscape

| Concept | Explanation | Analogy |
|----------|--------------|----------|
| Database | An organized collection of related data, usually stored electronically on a computer system. | A filing cabinet that holds many folders. |
| Table (Relation) | A collection of data organized into rows (records) and columns (fields). | A single folder inside the cabinet, holding similar types of documents. |
| Schema | The structure/design of the database—it defines how the data is organized, including tables, columns, data types, and relationships. | The index or blueprint that shows all the folders, what papers they hold, and how they relate. |

1.2 Keys and Constraints
Keys and Constraints are rules enforced by the database to ensure Data Integrity (accuracy and consistency).

| Concept | Explanation | Example (from users table) |
|----------|--------------|-----------------------------|
| Primary Key (PK) | A column (or set of columns) that uniquely identifies each row in a table. Must be NOT NULL and UNIQUE. | user_id |
| Foreign Key (FK) | A column (or set of columns) in one table that refers to the Primary Key of another table. It establishes a link between tables. | user_id in the engagement table references user_id in the users table. |
| Composite Key | A Primary Key composed of two or more columns that, when combined, uniquely identify a row. | In the engagement table, a combination of (user_id, content_id, event_time) might form a composite key to track specific interactions. |
| NOT NULL | Ensures a column cannot contain a NULL value. | name in the users table should be NOT NULL. |
| UNIQUE | Ensures all values in a column are different. (A table can have multiple UNIQUE constraints, but only one PK). | email (if it existed) in the users table. |

📝 Exercise 1.2
1.2.1 Identify the Primary Key (PK) for the subscriptions table:

* user_id
* plan
* A composite key of (user_id, start_date)

1.2.2. What key is needed in the engagement table to link it to the content table?
 - Solution 1: The PK is a composite of (user_id, start_date) because a single user can have multiple subscriptions over time.
 - Solution 2: A Foreign Key to content_id.

1.3 DDL (Data Definition Language)

DDL commands are used to define or modify the structure of the database objects.

| Command | Purpose | Example |
|----------|----------|----------|
| CREATE DATABASE | Creates a new database. | CREATE DATABASE UserEngagementDB; |
| CREATE TABLE | Creates a new table with its specified columns, data types, and constraints. | CREATE TABLE users (user_id INT PRIMARY KEY, name VARCHAR(100), signup_date DATE); |
| ALTER TABLE | Changes the structure of an existing table (e.g., adding/dropping columns, modifying constraints). | ALTER TABLE users ADD COLUMN email VARCHAR(100) UNIQUE; |
| DROP TABLE | Completely removes a table and all its data from the database. | DROP TABLE users; |
