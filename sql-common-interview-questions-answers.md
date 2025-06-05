# 🎯 SQL Interview Questions & Answers

---

### Q: Explain the following SQL keywords: `COALESCE`, `NULL`, `HAVING`, `GROUP BY`, `SELF JOIN`, `CASE`, `DISTINCT`, and `TOP`. When and where are they used? Provide example queries with results.

---

**Answer:**

| Keyword  | Explanation | Example Query | Result Explanation |
|----------|-------------|---------------|--------------------|
| **COALESCE** | Returns the first non-NULL value from a list of expressions. Useful for replacing NULL with a default value. | ```sql SELECT name, COALESCE(phone, 'N/A') AS phone_contact FROM employees; ``` | If `phone` is NULL, it shows 'N/A' instead. |
| **NULL** | Represents missing or unknown data in SQL. NULL is not zero or empty string. Use `IS NULL` or `IS NOT NULL` to check. | ```sql SELECT * FROM employees WHERE phone IS NULL; ``` | Retrieves rows where `phone` has no value. |
| **HAVING** | Filters groups created by `GROUP BY` clause. Unlike `WHERE`, it works on aggregated data. | ```sql SELECT department_id, COUNT(*) AS emp_count FROM employees GROUP BY department_id HAVING COUNT(*) > 2; ``` | Shows departments with more than 2 employees. |
| **GROUP BY** | Groups rows sharing the same value(s) in specified column(s). Used with aggregate functions. | ```sql SELECT department_id, AVG(salary) FROM employees GROUP BY department_id; ``` | Calculates average salary per department. |
| **SELF JOIN** | Joins a table to itself to compare rows within the same table. Useful for hierarchical data. | ```sql SELECT e1.name AS Employee, e2.name AS Manager FROM employees e1 LEFT JOIN employees e2 ON e1.manager_id = e2.employee_id; ``` | Lists employees with their managers (if any). |
| **CASE** | Implements conditional logic in SQL queries to return different values based on conditions. | ```sql SELECT name, salary, CASE WHEN salary > 60000 THEN 'High' ELSE 'Low' END AS salary_level FROM employees; ``` | Classifies employees as 'High' or 'Low' salary. |
| **DISTINCT** | Removes duplicate rows from the result set. | ```sql SELECT DISTINCT department_id FROM employees; ``` | Returns unique department IDs only. |
| **TOP** | Limits the number of rows returned by a query (SQL Server, some other DBs). | ```sql SELECT TOP 3 * FROM employees ORDER BY salary DESC; ``` | Returns top 3 highest-paid employees. |

---

### Q: Explain database normalization, its use cases, and where each normal form is applied.

---

**Answer:**

**Normalization** is a process in database design that organizes tables and their relationships to reduce data redundancy and improve data integrity. It involves dividing large tables into smaller ones and defining relationships.

| Normal Form      | Purpose / Use Case                                         | Description                                                        |
|------------------|------------------------------------------------------------|--------------------------------------------------------------------|
| **1NF (First Normal Form)** | Eliminate repeating groups and ensure atomicity of data. | Each column holds atomic values; no repeating groups or arrays.     |
| **2NF (Second Normal Form)** | Remove partial dependencies (dependency on part of a composite key). | Table is in 1NF and all non-key columns depend on the whole primary key. |
| **3NF (Third Normal Form)** | Remove transitive dependencies (non-key depends on another non-key). | Table is in 2NF and no non-key attribute depends on another non-key. |
| **BCNF (Boyce-Codd Normal Form)** | Stronger version of 3NF; every determinant is a candidate key. | Used when 3NF doesn't fully resolve anomalies.                       |
| **4NF and beyond** | Handle multi-valued dependencies and further refine schema. | Rarely used, but important in complex scenarios.                    |

**Use cases:**

- Normalize **OLTP (transactional)** databases to avoid update anomalies and maintain consistency.
- Denormalize for **OLAP (analytics)** databases where read performance is critical and some redundancy is acceptable.
- Apply **1NF to 3NF** typically in most relational databases.

---

**Example:**

A table storing `Orders` with repeated product lists violates 1NF. Normalization separates orders and products into related tables, making data clean and easier to maintain.

---

### Q: What are **Window Functions** in SQL? Why are they used and what are common use cases?

---

**Answer:**

**Window Functions** perform calculations across a set of table rows that are related to the current row. Unlike aggregate functions that group rows and return one result per group, window functions return a value for every row while still allowing access to individual row details.

They are called **“window”** functions because they operate on a “window” (subset) of rows defined by an OVER() clause without collapsing rows into a single output.

---

**Why use Window Functions?**

- To compute running totals, moving averages, ranks, and row numbers without losing the original row details.
- To perform calculations that require data from multiple rows without grouping and losing row-level granularity.
- Simplifies complex queries that otherwise require self-joins or subqueries.
- Window functions enable powerful, row-aware calculations without losing detail. They are widely used in analytics, reporting, and ranking scenarios.

---

**Common Use Cases:**

| Use Case                | Example Query | Explanation |
|-------------------------|---------------|-------------|
| **ROW_NUMBER()**: Assign unique sequential numbers to rows within partitions. | ```sql SELECT name, department_id, ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank FROM employees; ``` | Ranks employees by salary within each department. |
| **RANK() / DENSE_RANK()**: Assign ranks with gaps (RANK) or without gaps (DENSE_RANK). | ```sql SELECT name, salary, RANK() OVER (ORDER BY salary DESC) AS salary_rank FROM employees; ``` | Shows salary ranks across all employees. |
| **SUM() OVER()**: Calculate running totals or cumulative sums. | ```sql SELECT name, salary, SUM(salary) OVER (ORDER BY employee_id) AS running_total FROM employees; ``` | Calculates cumulative salary by employee ID order. |
| **AVG() OVER()**: Calculate moving averages. | ```sql SELECT name, salary, AVG(salary) OVER (PARTITION BY department_id) AS avg_dept_salary FROM employees; ``` | Calculates average salary per department alongside each row. |

---


