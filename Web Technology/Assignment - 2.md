
---

### MySQL Introduction
1. **What is MySQL, and how does it differ from other relational databases?**  
   MySQL is an open-source relational database management system (RDBMS) that uses SQL to manage data in tables. It differs from others like Oracle or PostgreSQL by being lightweight, fast, and widely used for web applications.

2. **Explain the role of a primary key in a MySQL database.**  
   A primary key uniquely identifies each row in a table and ensures no duplicate or NULL values. It helps maintain data integrity and enables efficient retrieval.

3. **What is the purpose of the MySQL Workbench?**  
   MySQL Workbench is a graphical tool for designing, managing, and querying MySQL databases. It simplifies tasks like creating tables, running SQL queries, and visualizing database structures.

4. **Define a schema in MySQL with an example.**  
   A schema in MySQL is a logical collection of database objects like tables and views. For example, a "school" schema might contain tables like "students" and "teachers."

5. **What are the advantages of using MySQL over a flat-file database?**  
   MySQL supports relational data, multiple users, and complex queries, unlike flat-file databases, which are simple but lack scalability and data relationships.

---

### Data Types in MySQL
1. **What is the difference between CHAR and VARCHAR data types in MySQL?**  
   CHAR is a fixed-length string, padding spaces if shorter, while VARCHAR is variable-length, storing only the actual data. CHAR is faster for fixed-size data, VARCHAR saves space.

7. **Explain the use of the INT and TINYINT data types.**  
   INT stores integers from -2,147,483,648 to 2,147,483,647, while TINYINT stores smaller values from -128 to 127. TINYINT uses less storage (1 byte) than INT (4 bytes).

8. **How does the DATETIME data type store values in MySQL?**  
   DATETIME stores date and time in the format 'YYYY-MM-DD HH:MM:SS', ranging from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'. It’s used for timestamped data.

9. **What is the purpose of the ENUM data type in MySQL?**  
   ENUM allows a column to store one value from a predefined list, like ('Yes', 'No'). It saves space and ensures data consistency.

10. **Differentiate between TEXT and BLOB data types in MySQL.**  
    TEXT stores large text data (e.g., articles), while BLOB stores binary data (e.g., images). TEXT is character-based, BLOB is byte-based.

---

### Data Definition Language (DDL)
11. **Write a MySQL command to create a table named "Students" with two columns.**  
    `CREATE TABLE Students (id INT, name VARCHAR(50));`  
    This creates a table with an integer "id" and a variable-length "name" column.

12. **What is the purpose of the ALTER TABLE statement in MySQL?**  
    ALTER TABLE modifies an existing table’s structure, such as adding columns or changing data types. For example, `ALTER TABLE Students ADD age INT;`.

13. **Explain the DROP TABLE command with its syntax.**  
    DROP TABLE deletes a table and its data permanently. Syntax: `DROP TABLE table_name;` e.g., `DROP TABLE Students;`.

14. **How do you add a new column to an existing table in MySQL?**  
    Use `ALTER TABLE table_name ADD column_name datatype;`. Example: `ALTER TABLE Students ADD grade CHAR(2);`.

15. **What does the TRUNCATE TABLE command do in MySQL?**  
    TRUNCATE TABLE removes all rows from a table but keeps its structure. Example: `TRUNCATE TABLE Students;` resets the table.

---

### Data Manipulation Language (DML)
16. **Write a MySQL query to insert a row into a table named "Employees."**  
    `INSERT INTO Employees (id, name) VALUES (1, 'John');`  
    This adds a row with id 1 and name "John."

17. **What is the difference between DELETE and DROP in MySQL?**  
    DELETE removes specific rows from a table (DML), while DROP deletes the entire table and its structure (DDL). DELETE is reversible with conditions, DROP is not.

18. **Explain the purpose of the UPDATE statement with an example.**  
    UPDATE modifies existing data in a table. Example: `UPDATE Employees SET name = 'Jane' WHERE id = 1;` changes the name for id 1.

19. **How do you retrieve all columns from a table in MySQL?**  
    Use `SELECT * FROM table_name;`. Example: `SELECT * FROM Employees;` fetches all columns and rows.

20. **What happens if you omit the WHERE clause in an UPDATE query?**  
    All rows in the table are updated with the new value. Example: `UPDATE Employees SET salary = 5000;` sets every salary to 5000.

---

### Data Control Language (DCL)
21. **What is the difference between GRANT and REVOKE in MySQL?**  
    GRANT gives privileges to a user (e.g., SELECT), while REVOKE removes them. Both control access to database objects.

22. **Write a MySQL command to grant SELECT privilege to a user.**  
    `GRANT SELECT ON database_name.table_name TO 'user'@'host';`  
    Example: `GRANT SELECT ON company.Employees TO 'john'@'localhost';`.

23. **Explain the purpose of the DCL in database security.**  
    DCL (Data Control Language) manages access permissions using commands like GRANT and REVOKE. It ensures only authorized users perform specific actions.

24. **How do you revoke all privileges from a user in MySQL?**  
    Use `REVOKE ALL PRIVILEGES ON database_name.* FROM 'user'@'host';`. Example: `REVOKE ALL PRIVILEGES ON company.* FROM 'john'@'localhost';`.

25. **What is the role of the WITH GRANT OPTION in a GRANT statement?**  
    It allows the user to grant the same privileges to others. Example: `GRANT SELECT ON Employees TO 'john'@'localhost' WITH GRANT OPTION;`.

---

### Pattern Matching
26. **What is the purpose of the LIKE operator in MySQL?**  
    LIKE is used for pattern matching in strings with wildcards (% and _). It filters data based on partial matches.

27. **Write a query to find names starting with "A" using pattern matching.**  
    `SELECT name FROM Students WHERE name LIKE 'A%';`  
    This retrieves names like "Anna" or "Alex."

28. **Explain the use of the % wildcard in MySQL with an example.**  
    % matches any sequence of characters. Example: `SELECT * FROM Employees WHERE name LIKE '%son';` finds "Johnson" or "Mason."

29. **How does the _ wildcard differ from the % wildcard in MySQL?**  
    _ matches exactly one character, while % matches zero or more. Example: `WHERE name LIKE 'J_n'` matches "Jon," but not "John."

30. **Write a query to find records ending with "ing" in a column.**  
    `SELECT title FROM Books WHERE title LIKE '%ing';`  
    This finds titles like "Running" or "Singing."

---

### GROUP BY
31. **What is the purpose of the GROUP BY clause in MySQL?**  
    GROUP BY groups rows with identical values into summary rows, often used with aggregate functions like COUNT or SUM.

32. **Write a query to count the number of employees in each department.**  
    `SELECT department, COUNT(*) FROM Employees GROUP BY department;`  
    This counts employees per department.

33. **How does GROUP BY work with aggregate functions?**  
    GROUP BY organizes data into groups, and aggregate functions (e.g., SUM, AVG) calculate a single value per group. Example: `SUM(salary)` per department.

34. **Explain the difference between GROUP BY and ORDER BY.**  
    GROUP BY groups rows for aggregation, while ORDER BY sorts the result set. GROUP BY affects data structure, ORDER BY affects display.

35. **Write a query to find the total salary per department.**  
    `SELECT department, SUM(salary) FROM Employees GROUP BY department;`  
    This sums salaries for each department.

---

### IS NULL
36. **What does the IS NULL operator do in MySQL?**  
    IS NULL checks if a column contains a NULL value. It’s used to filter rows with missing data.

37. **Write a query to find records where the "email" column is null.**  
    `SELECT * FROM Employees WHERE email IS NULL;`  
    This retrieves rows with no email.

38. **How does IS NULL differ from = NULL in MySQL?**  
    IS NULL correctly tests for NULL values, while = NULL always fails because NULL isn’t equal to anything, including itself.

39. **Explain the use of IS NOT NULL with an example.**  
    IS NOT NULL finds non-NULL values. Example: `SELECT name FROM Students WHERE grade IS NOT NULL;` retrieves students with grades.

40. **Why does a direct comparison with NULL fail in MySQL?**  
    NULL represents an unknown value, so comparisons like `column = NULL` are undefined. Use IS NULL instead.

---

### DISTINCT
41. **What is the purpose of the DISTINCT keyword in MySQL?**  
    DISTINCT eliminates duplicate rows from the result set, returning only unique values.

42. **Write a query to retrieve unique cities from a "Customers" table.**  
    `SELECT DISTINCT city FROM Customers;`  
    This lists each city once, removing duplicates.

43. **How does DISTINCT affect query performance?**  
    DISTINCT requires sorting or hashing to remove duplicates, which can slow queries on large datasets. Indexes may help.

44. **Can DISTINCT be used with multiple columns? Give an example.**  
    Yes, it applies to the combination. Example: `SELECT DISTINCT city, country FROM Customers;` returns unique city-country pairs.

45. **What is the difference between DISTINCT and GROUP BY?**  
    DISTINCT removes duplicate rows from the result, while GROUP BY groups rows for aggregation. DISTINCT is simpler, GROUP BY is for summaries.

---

### Optimization, MAX, and MIN Functions
46. **What is the role of the MAX() function in MySQL? Give an example.**  
    MAX() finds the highest value in a column. Example: `SELECT MAX(salary) FROM Employees;` returns the top salary.

47. **Write a query to find the minimum salary from an "Employees" table.**  
    `SELECT MIN(salary) FROM Employees;`  
    This retrieves the lowest salary.

48. **How can indexes improve query optimization in MySQL?**  
    Indexes speed up searches by creating a data structure for quick lookups. They reduce the need to scan entire tables.

49. **Explain the difference between MAX() and MIN() with an example.**  
    MAX() finds the largest value, MIN() finds the smallest. Example: `SELECT MAX(score), MIN(score) FROM Scores;` returns highest and lowest scores.

50. **Write a query to find the highest and lowest scores in a "Scores" table.**  
    `SELECT MAX(score) AS highest, MIN(score) AS lowest FROM Scores;`  
    This returns both values in one query.

---

### Using AUTO_INCREMENT
51. **What is the purpose of AUTO_INCREMENT in MySQL?**  
    AUTO_INCREMENT automatically generates unique, sequential numbers for a column, typically used for primary keys.

52. **Write a CREATE TABLE statement with an AUTO_INCREMENT column.**  
    `CREATE TABLE Students (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(50));`  
    The "id" column auto-increments from 1.

53. **How does MySQL assign values to an AUTO_INCREMENT column?**  
    MySQL assigns the next integer (e.g., 1, 2, 3) when a row is inserted without specifying the column value. It increments from the last used number.

54. **Can you reset the AUTO_INCREMENT value? If yes, how?**  
    Yes, use `ALTER TABLE table_name AUTO_INCREMENT = value;`. Example: `ALTER TABLE Students AUTO_INCREMENT = 100;` starts from 100.

55. **What happens if you insert a specific value into an AUTO_INCREMENT column?**  
    MySQL uses the specified value instead of auto-incrementing. The next auto-generated value adjusts to be higher than the inserted value.

---
