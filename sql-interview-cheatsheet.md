# 🚀 SQL Interview Cheat Sheet

A handy reference to cover **basic**, **intermediate**, and **advanced** SQL concepts in a tabular format.

---

## 🔰 1. Basic SQL

| Topic         | Description                                    | Example |
|---------------|-------------------------------------------------|---------|
| SELECT        | Retrieve data from a table                      | `SELECT * FROM employees;` |
| WHERE         | Filter records                                  | `SELECT * FROM employees WHERE salary > 50000;` |
| ORDER BY      | Sort results                                    | `SELECT * FROM employees ORDER BY salary DESC;` |
| DISTINCT      | Remove duplicates                               | `SELECT DISTINCT department_id FROM employees;` |
| LIMIT/OFFSET  | Limit the number of results                     | `SELECT * FROM employees LIMIT 10 OFFSET 5;` |

---

## 🔗 2. Joins

| Join Type    | Description                               | Example |
|--------------|--------------------------------------------|---------|
| INNER JOIN   | Matches records in both tables             | `SELECT e.name, d.name FROM employees e INNER JOIN departments d ON e.dept_id = d.id;` |
| LEFT JOIN    | All from left + matches from right         | `SELECT e.name, d.name FROM employees e LEFT JOIN departments d ON e.dept_id = d.id;` |
| RIGHT JOIN   | All from right + matches from left         | `SELECT e.name, d.name FROM employees e RIGHT JOIN departments d ON e.dept_id = d.id;` |
| FULL JOIN    | All records from both sides                | `SELECT e.name, d.name FROM employees e FULL JOIN departments d ON e.dept_id = d.id;` |

---

## 🔍 3. Aggregate Functions

| Function     | Description                               | Example |
|--------------|--------------------------------------------|---------|
| COUNT()      | Counts rows                               | `SELECT COUNT(*) FROM employees;` |
| SUM()        | Sum of values                             | `SELECT SUM(salary) FROM employees;` |
| AVG()        | Average value                             | `SELECT AVG(salary) FROM employees;` |
| MIN()/MAX()  | Minimum/Maximum values                    | `SELECT MAX(salary) FROM employees;` |

---

## ⚡️ 4. Window Functions

| Function        | Description                                    | Example |
|-----------------|------------------------------------------------|---------|
| OVER()          | Define the window                              | `SELECT salary, AVG(salary) OVER(PARTITION BY department_id) FROM employees;` |
| ROW_NUMBER()    | Row numbering                                  | `SELECT name, ROW_NUMBER() OVER(ORDER BY salary DESC) FROM employees;` |
| RANK()/DENSE_RANK() | Rank rows based on order                   | `SELECT name, RANK() OVER(ORDER BY salary DESC) FROM employees;` |
| SUM() OVER()    | Running total                                  | `SELECT salary, SUM(salary) OVER(ORDER BY hire_date) FROM employees;` |

---

## 🛠️ 5. Performance and Advanced Topics

| Topic              | Description                               | Example |
|--------------------|--------------------------------------------|---------|
| Indexes            | Improve query speed                        | `CREATE INDEX idx_name ON employees(name);` |
| Views              | Save reusable queries                      | `CREATE VIEW high_earners AS SELECT * FROM employees WHERE salary > 100000;` |
| CTEs               | Common Table Expressions                   | `WITH dept_avg AS (SELECT department_id, AVG(salary) avg_sal FROM employees GROUP BY department_id) SELECT * FROM dept_avg;` |
| Transactions       | Atomic operations                          | `BEGIN; UPDATE employees SET salary = salary * 1.05; COMMIT;` |
| Error Handling     | Handling failures                          | e.g. `TRY...CATCH` (varies by DBMS) |

---