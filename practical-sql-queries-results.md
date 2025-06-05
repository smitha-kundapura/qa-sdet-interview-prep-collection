# 🚀 Practical SQL: Sample Data, Queries, and Results

SQL is a must-have skill for working with databases, analytics, and reporting. Let’s walk through **sample data**, **queries**, and **results** using essential SQL concepts like `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, joins, and aggregate functions.

---

## 🗂️ Sample Data in Table for Department and Employees

<table border="1" cellpadding="5" cellspacing="0" style="border-collapse: collapse;">
  <tr>
    <th colspan="2">📄 Departments</th>
    <th colspan="4" style="border-left: 4px double #000;">📄 Employees</th>
  </tr>
  <tr>
    <td><strong>department_id</strong></td>
    <td><strong>department_name</strong></td>
    <td style="border-left: 4px double #000;"><strong>employee_id</strong></td>
    <td><strong>name</strong></td>
    <td><strong>department_id</strong></td>
    <td><strong>salary</strong></td>
  </tr>
  <tr>
    <td>1</td>
    <td>HR</td>
    <td style="border-left: 4px double #000;">101</td>
    <td>Alice</td>
    <td>1</td>
    <td>50000</td>
  </tr>
  <tr>
    <td>2</td>
    <td>IT</td>
    <td style="border-left: 4px double #000;">102</td>
    <td>Bob</td>
    <td>2</td>
    <td>60000</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Finance</td>
    <td style="border-left: 4px double #000;">103</td>
    <td>Charlie</td>
    <td>2</td>
    <td>55000</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Marketing</td>
    <td style="border-left: 4px double #000;">104</td>
    <td>Diana</td>
    <td>3</td>
    <td>70000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">105</td>
    <td>Ethan</td>
    <td>4</td>
    <td>45000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">106</td>
    <td>Fiona</td>
    <td>4</td>
    <td>47000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">107</td>
    <td>George</td>
    <td>3</td>
    <td>75000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">108</td>
    <td>Hannah</td>
    <td>2</td>
    <td>58000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">109</td>
    <td>Ian</td>
    <td>1</td>
    <td>52000</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td style="border-left: 4px double #000;">110</td>
    <td>Jane</td>
    <td>2</td>
    <td>61000</td>
  </tr>
</table>


---

## 📝 Sample Queries and Results

| Use Case | Query | Result |
|----------|-------|--------|
| **Select all employees** | `SELECT * FROM Employees;` | Returns all 10 rows from Employees. |
| **Filter by salary** | `SELECT * FROM Employees WHERE salary > 55000;` | Bob, Diana, George, Hannah, Jane |
| **Group by department** | `SELECT department_id, COUNT(*) AS num_employees FROM Employees GROUP BY department_id;` | 1:2, 2:4, 3:2, 4:2 |
| **Filter groups with HAVING** | `SELECT department_id, AVG(salary) AS avg_salary FROM Employees GROUP BY department_id HAVING avg_salary > 55000;` | Departments 2 and 3 |
| **Order employees by salary descending** | `SELECT * FROM Employees ORDER BY salary DESC;` | George, Diana, Jane, Bob, Hannah, Charlie, Ian, Alice, Fiona, Ethan |
| **INNER JOIN (employees with departments)** | `SELECT e.name, d.department_name FROM Employees e INNER JOIN Departments d ON e.department_id = d.department_id;` | All employees matched with their department names. |
| **LEFT JOIN (all employees)** | `SELECT e.name, d.department_name FROM Employees e LEFT JOIN Departments d ON e.department_id = d.department_id;` | Same as INNER JOIN since all employees have a department. |
| **RIGHT JOIN (all departments)** | `SELECT e.name, d.department_name FROM Employees e RIGHT JOIN Departments d ON e.department_id = d.department_id;` | All departments, plus employees where available. |
| **FULL JOIN** | `SELECT e.name, d.department_name FROM Employees e FULL JOIN Departments d ON e.department_id = d.department_id;` | All employees and departments, with NULLs if no match (none here). |
| **Count employees in IT** | `SELECT COUNT(*) FROM Employees WHERE department_id = 2;` | 4 |
| **Sum of salaries in HR** | `SELECT SUM(salary) FROM Employees WHERE department_id = 1;` | 102000 |
| **Average salary in Finance** | `SELECT AVG(salary) FROM Employees WHERE department_id = 3;` | 72500 |
| **Minimum salary overall** | `SELECT MIN(salary) FROM Employees;` | 45000 |
| **Maximum salary overall** | `SELECT MAX(salary) FROM Employees;` | 75000 |

---

## 🔑 Key Concepts
## 🗂️ SQL Keywords Explained (Interview Style)

| Keyword | Interview Answer |
|---------|------------------|
| **SELECT** | "SELECT is used to retrieve specific columns or all columns from one or more tables. It’s the most basic SQL statement to pull data you need." |
| **FROM** | "FROM specifies the table(s) where the data is stored. It tells SQL which table to query data from." |
| **WHERE** | "WHERE filters the result set based on conditions. It allows you to select only those rows that meet your criteria." |
| **GROUP BY** | "GROUP BY groups rows that have the same values in specified columns. It’s used with aggregate functions like COUNT, SUM, AVG, etc." |
| **HAVING** | "HAVING filters groups after they’ve been formed by GROUP BY. It’s like WHERE but applies to aggregated results." |
| **ORDER BY** | "ORDER BY sorts the result set in ascending (default) or descending order based on one or more columns." |
| **INNER JOIN** | "INNER JOIN returns rows where there’s a match in both tables based on a specified condition, like a shared key." |
| **LEFT JOIN** | "LEFT JOIN returns all rows from the left table, and matches from the right table where possible; unmatched rows from the right table will have NULLs." |
| **RIGHT JOIN** | "RIGHT JOIN is the opposite of LEFT JOIN. It returns all rows from the right table, plus matches from the left table; unmatched rows from the left table will have NULLs." |
| **FULL JOIN** | "FULL JOIN returns all rows from both tables. When there’s no match, it returns NULLs in the columns from the missing table." |
| **COUNT()** | "COUNT() returns the number of rows that match a given condition or the total number of rows if no condition is specified." |
| **SUM()** | "SUM() calculates the total of numeric column values." |
| **AVG()** | "AVG() returns the average value of a numeric column." |
| **MIN() / MAX()** | "MIN() returns the smallest value in a column; MAX() returns the largest value." |

---

## 🛠️ Online SQL Practice Tools

| Tool | Link | Features | Pros | Cons |
|------|------|----------|------|------|
| **SQL Fiddle** | [SQL Fiddle](http://sqlfiddle.com/) | Interactive SQL editor; supports MySQL, PostgreSQL, SQLite, Oracle, SQL Server; allows custom schema and sharing. | Fast, easy sharing, supports schema building. | Can be slow or unavailable at times. |
| **Mode SQL Editor** | [Mode SQL Editor](https://mode.com/sql-tutorial/) | Free interactive SQL editor with embedded datasets and tutorials. | Clean interface, real-world data, built-in visualizations. | Requires free signup. |
| **LeetCode SQL Playground** | [LeetCode SQL](https://leetcode.com/problemset/database/) | Practice SQL queries with a large question bank; ideal for interview prep. | High-quality questions, real-world scenarios, graded solutions. | Some advanced features require premium account. |
| **DB-Fiddle** | [DB-Fiddle](https://www.db-fiddle.com/) | Lightweight SQL playground; supports MySQL, PostgreSQL, SQLite; easy sharing. | Easy to use, quick testing and sharing. | No tutorials or guided learning. |

---

💡 *Tip*: Try implementing these queries in your preferred SQL environment (MySQL, PostgreSQL, SQL Server, etc.) to see the results in action!
