# TCS DBMS Interview Preparation - Complete Question Bank

## DBMS Theory Questions

### Database Basics

**1. What is DBMS? Why do we use it?**
DBMS (Database Management System) is software that manages databases. We use it for:
- Data security and access control
- Data integrity and consistency
- Concurrent access by multiple users
- Data independence from applications
- Backup and recovery mechanisms
- Efficient data storage and retrieval

**2. DBMS vs RDBMS vs File system differences?**
| Feature | File System | DBMS | RDBMS |
|---------|-------------|------|-------|
| Data Structure | Files | Any format | Tables with relationships |
| Relationships | No | Limited | Strong (foreign keys) |
| ACID Properties | No | Partial | Full |
| SQL Support | No | Limited | Complete |
| Data Integrity | Manual | Basic | Strong |
| Example | Text files | MongoDB | MySQL, Oracle |

**3. What is a schema? What is an instance?**
- **Schema**: Logical structure/blueprint of database (design)
- **Instance**: Actual data stored at a particular moment (snapshot)
- Example: Schema defines Employee(ID, Name, Salary), Instance contains actual employee records

**4. What is a relation/table/tuple/attribute/domain?**
- **Relation/Table**: Collection of related data organized in rows and columns
- **Tuple**: Single row/record in a table
- **Attribute**: Column/field in a table
- **Domain**: Set of valid values for an attribute

**5. What is data abstraction? (3 levels)**
1. **Physical Level**: How data is actually stored (files, indexes, storage devices)
2. **Logical Level**: What data is stored and relationships between data
3. **View Level**: How users see and interact with data (customized views)

**6. What is data independence? (logical vs physical)**
- **Physical Independence**: Ability to change physical storage without affecting logical structure
- **Logical Independence**: Ability to change logical structure without affecting application programs
- Example: Moving from HDD to SSD (physical) or adding new column (logical)

**7. What is metadata?**
Metadata is "data about data" - information that describes the structure, constraints, and properties of data in the database. Examples: table names, column types, constraints, indexes.

### Keys & Constraints

**8. What is a primary key? Why is it important?**
Primary key uniquely identifies each record in a table.
**Importance:**
- Ensures uniqueness (no duplicate records)
- Cannot contain NULL values
- Creates clustered index automatically
- Referenced by foreign keys from other tables
- Maintains entity integrity

**9. Candidate key vs primary key vs super key**
- **Super Key**: Any combination of attributes that uniquely identifies records
- **Candidate Key**: Minimal super key (no redundant attributes)
- **Primary Key**: One chosen candidate key for the table
- Example: Employee(ID, Email, Phone) - all three are candidate keys, ID chosen as primary

**10. Foreign key and referential integrity**
- **Foreign Key**: Attribute that references primary key of another table
- **Referential Integrity**: Ensures foreign key values exist in referenced table
- Example: Employee.DeptID must exist in Department.ID

**11. Composite key vs surrogate key**
- **Composite Key**: Primary key made of multiple columns combined
- **Surrogate Key**: Artificial key (usually auto-increment) with no business meaning
- Example: OrderDetails(OrderID, ProductID) vs Employee(EmpID auto-increment)

**12. Unique key vs primary key**
| Feature | Primary Key | Unique Key |
|---------|-------------|------------|
| NULL values | Not allowed | One NULL allowed |
| Per table | Only one | Multiple allowed |
| Index | Clustered | Non-clustered |
| Purpose | Entity integrity | Uniqueness constraint |

**13. Null constraint vs default constraint**
- **NULL Constraint**: Specifies whether column can contain NULL values
- **Default Constraint**: Provides default value when no value is specified
- Example: Age INT NOT NULL, Status VARCHAR(10) DEFAULT 'Active'

**14. CHECK constraint with example**
CHECK constraint ensures values in column satisfy specific condition.
```sql
CREATE TABLE Employee (
    Age INT CHECK (Age >= 18 AND Age <= 65),
    Salary DECIMAL CHECK (Salary > 0)
);
```

**15. NOT NULL vs UNIQUE difference**
- **NOT NULL**: Ensures column cannot have empty values
- **UNIQUE**: Ensures all values in column are different (but can have one NULL)
- Can be combined: column can be both NOT NULL and UNIQUE

**16. Can a table have multiple primary keys?**
No, a table can have only ONE primary key. However, primary key can be composite (multiple columns combined).

**17. Can a foreign key be NULL?**
Yes, foreign key can be NULL unless explicitly defined as NOT NULL. NULL means "no relationship exists."

**18. What happens if we delete a referenced row? (ON DELETE CASCADE/SET NULL/RESTRICT)**
- **CASCADE**: Automatically delete dependent records
- **SET NULL**: Set foreign key values to NULL
- **RESTRICT/NO ACTION**: Prevent deletion if references exist
- **SET DEFAULT**: Set foreign key to default value

### Normalization

**19. What is normalization? Why do it?**
Normalization organizes data to reduce redundancy and dependency.
**Benefits:**
- Eliminates data redundancy
- Prevents update, insert, delete anomalies
- Saves storage space
- Maintains data consistency
- Improves data integrity

**20. What is denormalization? When to use?**
Denormalization intentionally introduces redundancy for performance.
**When to use:**
- Read-heavy applications
- Data warehousing
- When query performance is more important than storage
- Reporting systems

**21. 1NF, 2NF, 3NF, BCNF definitions**
- **1NF**: Atomic values, no repeating groups, each cell contains single value
- **2NF**: 1NF + no partial dependency on primary key
- **3NF**: 2NF + no transitive dependency
- **BCNF**: 3NF + every determinant is a candidate key

**22. Examples of partial dependency, transitive dependency**
- **Partial Dependency**: Non-key attribute depends on part of composite primary key
  Example: (StudentID, CourseID) → StudentName (StudentName depends only on StudentID)
- **Transitive Dependency**: Non-key attribute depends on another non-key attribute
  Example: StudentID → DeptID → DeptName

**23. Functional dependency (FD) concept**
If A functionally determines B (A → B), then for same value of A, B value is always the same.
Example: StudentID → StudentName (ID uniquely determines name)

**24. Lossless decomposition vs lossy decomposition**
- **Lossless**: Original relation can be reconstructed from decomposed relations
- **Lossy**: Information is lost during decomposition, cannot reconstruct original
- Lossless decomposition preserves all information and dependencies

**25. Dependency preservation**
After decomposition, all functional dependencies should be preserved in the resulting relations or derivable from them.

**26. When is BCNF preferred over 3NF?**
BCNF is preferred when:
- Every determinant should be a candidate key
- Want to eliminate all redundancy
- Can afford to lose some functional dependencies
- Data integrity is more important than dependency preservation

### Joins & Relationships

**27. What are joins? Why needed?**
Joins combine data from multiple related tables based on common columns.
**Why needed:**
- Retrieve related data from normalized tables
- Avoid data redundancy
- Maintain referential integrity
- Enable complex queries across multiple entities

**28. INNER vs LEFT vs RIGHT vs FULL join**
- **INNER JOIN**: Only matching records from both tables
- **LEFT JOIN**: All records from left table + matching from right
- **RIGHT JOIN**: All records from right table + matching from left
- **FULL OUTER JOIN**: All records from both tables

**29. CROSS join vs self join**
- **CROSS JOIN**: Cartesian product of two tables (every row with every row)
- **SELF JOIN**: Table joined with itself using aliases

**30. Natural join vs equi join**
- **Natural JOIN**: Automatically joins on columns with same name
- **Equi JOIN**: Explicitly specify join condition using equality operator

**31. Join vs subquery (when better?)**
- **JOIN**: Better for performance, retrieving data from multiple tables
- **Subquery**: Better for complex conditions, EXISTS/NOT EXISTS operations
- Use JOIN when possible for better optimization

**32. Many-to-many relationship: how to represent in DB?**
Use junction/bridge/linking table with foreign keys from both related tables.
Example: Student-Course (many-to-many) → Create StudentCourse(StudentID, CourseID)

**33. One-to-one, one-to-many examples**
- **One-to-One**: Person-Passport (one person has one passport)
- **One-to-Many**: Department-Employee (one department has many employees)

**34. What is a junction table?**
Junction table resolves many-to-many relationships by containing foreign keys from both related tables. Also called bridge table or linking table.

### SQL Command Types

**35. DDL vs DML vs DCL vs TCL**
- **DDL (Data Definition Language)**: CREATE, ALTER, DROP, TRUNCATE
- **DML (Data Manipulation Language)**: SELECT, INSERT, UPDATE, DELETE
- **DCL (Data Control Language)**: GRANT, REVOKE
- **TCL (Transaction Control Language)**: COMMIT, ROLLBACK, SAVEPOINT

**36. Examples of each category**
```sql
-- DDL
CREATE TABLE Employee(ID INT, Name VARCHAR(50));
ALTER TABLE Employee ADD Salary DECIMAL;
DROP TABLE Employee;

-- DML
SELECT * FROM Employee;
INSERT INTO Employee VALUES(1, 'John');
UPDATE Employee SET Salary = 50000;
DELETE FROM Employee WHERE ID = 1;

-- DCL
GRANT SELECT ON Employee TO user1;
REVOKE INSERT ON Employee FROM user1;

-- TCL
BEGIN TRANSACTION;
COMMIT;
ROLLBACK;
SAVEPOINT sp1;
```

**37. COMMIT vs ROLLBACK vs SAVEPOINT**
- **COMMIT**: Permanently saves all changes made in current transaction
- **ROLLBACK**: Undoes all changes made in current transaction
- **SAVEPOINT**: Creates a point within transaction to rollback to

**38. What is AUTOCOMMIT?**
AUTOCOMMIT automatically commits each SQL statement as separate transaction. When enabled, no need for explicit COMMIT.

**39. TRUNCATE vs DELETE vs DROP (most asked)**
| Operation | TRUNCATE | DELETE | DROP |
|-----------|----------|--------|------|
| Purpose | Remove all rows | Remove specific rows | Remove entire table |
| WHERE clause | No | Yes | No |
| Rollback | No (DDL) | Yes (DML) | No (DDL) |
| Speed | Fastest | Slower | Fast |
| Auto-increment | Reset to seed | Not reset | N/A |
| Triggers | Not fired | Fired | N/A |

**40. ALTER vs UPDATE difference**
- **ALTER**: Changes table structure (DDL) - add/drop columns, constraints
- **UPDATE**: Changes data values (DML) - modify existing records

### Indexes

**41. What is an index? Why use it?**
Index is a data structure that improves query performance by providing fast access paths to data.
**Why use:**
- Faster SELECT queries
- Faster WHERE, ORDER BY, JOIN operations
- Improved query performance
- Faster sorting and grouping

**42. Pros/cons of indexes**
**Pros:**
- Faster data retrieval
- Improved query performance
- Faster joins and sorting

**Cons:**
- Slower INSERT/UPDATE/DELETE operations
- Additional storage space required
- Index maintenance overhead
- Can slow down bulk operations

**43. Clustered vs non-clustered index**
- **Clustered Index**: Data physically sorted by index key, one per table
- **Non-clustered Index**: Separate structure pointing to data rows, multiple allowed

**44. When indexes hurt performance?**
- Small tables (overhead > benefit)
- Frequent INSERT/UPDATE/DELETE operations
- Columns with low selectivity (many duplicate values)
- Too many indexes on single table
- Bulk data loading operations

**45. Index on which columns is useful? (high selectivity)**
- Primary key columns
- Foreign key columns
- Columns frequently used in WHERE clauses
- Columns used in JOIN conditions
- Columns with high selectivity (unique or near-unique values)

**46. Can primary key create index automatically?**
Yes, primary key automatically creates a clustered index (in most RDBMS systems).

**47. B-tree index vs hash index (basic idea)**
- **B-tree Index**: Balanced tree structure, good for range queries, ordered data
- **Hash Index**: Hash table structure, very fast for equality searches, no ordering

### Views

**48. What is a view?**
View is a virtual table based on result of SQL query. It contains rows and columns like real table but doesn't store data physically.

**49. Why use views?**
- Data security (hide sensitive columns)
- Simplify complex queries
- Data abstraction
- Consistent interface for applications
- Restrict data access

**50. View vs table differences**
| Feature | Table | View |
|---------|-------|------|
| Storage | Physical | Virtual |
| Data | Stores actual data | Shows data from tables |
| Performance | Faster | Depends on underlying query |
| Updates | Always possible | Sometimes possible |

**51. Are views updatable? When not?**
Views are updatable when:
- Based on single table
- No aggregate functions
- No DISTINCT, GROUP BY, HAVING
- No calculated columns

**Not updatable when:**
- Multiple tables (joins)
- Contains aggregate functions
- Has DISTINCT or GROUP BY
- Contains calculated fields

**52. Materialized view vs normal view (basic)**
- **Normal View**: Virtual, executes query each time accessed
- **Materialized View**: Physical storage, pre-computed results, needs refresh

**53. How to drop a view?**
```sql
DROP VIEW view_name;
```

### Transactions, Concurrency & Locks

**54. What is a transaction?**
Transaction is a logical unit of work that must be completed entirely or not at all. It's a sequence of database operations treated as single unit.

**55. ACID properties (very common)**
- **Atomicity**: All operations succeed or all fail (all-or-nothing)
- **Consistency**: Database remains in valid state before and after transaction
- **Isolation**: Concurrent transactions don't interfere with each other
- **Durability**: Committed changes are permanent and survive system failures

**56. What is a schedule?**
Schedule is the chronological order of execution of operations from multiple concurrent transactions.

**57. Serial vs serializable schedule**
- **Serial Schedule**: Transactions execute one after another (no concurrency)
- **Serializable Schedule**: Concurrent execution equivalent to some serial schedule

**58. Conflict serializability idea**
Two operations conflict if they access same data item and at least one is write operation. Schedule is conflict serializable if can be transformed to serial schedule by swapping non-conflicting operations.

**59. What is isolation level?**
Isolation level determines how transaction changes are visible to other concurrent transactions. Levels: READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE.

**60. Dirty read, non-repeatable read, phantom read**
- **Dirty Read**: Reading uncommitted data from another transaction
- **Non-repeatable Read**: Same query returns different results within transaction
- **Phantom Read**: New rows appear/disappear between reads in same transaction

**61. Lost update problem**
Occurs when two transactions read same data and both update it, causing one update to be lost.

**62. Locking: shared vs exclusive locks**
- **Shared Lock (S)**: Multiple transactions can read same data simultaneously
- **Exclusive Lock (X)**: Only one transaction can write, blocks all other access

**63. Deadlock in DBMS and how to prevent/handle**
Deadlock occurs when two or more transactions wait for each other indefinitely.
**Prevention:**
- Lock timeout
- Lock ordering
- Deadlock detection and rollback
- Two-phase locking protocol

**64. Two-phase locking (2PL) basics**
Protocol with two phases:
1. **Growing Phase**: Acquire locks, cannot release any lock
2. **Shrinking Phase**: Release locks, cannot acquire new locks

**65. Optimistic vs pessimistic concurrency**
- **Pessimistic**: Lock data before accessing (assumes conflicts will occur)
- **Optimistic**: Check for conflicts before committing (assumes conflicts are rare)

### ER Model

**66. What is an ER diagram?**
Entity-Relationship diagram is a visual representation of database design showing entities, attributes, and relationships between entities.

**67. Entity vs attribute vs relationship**
- **Entity**: Real-world object (Student, Course)
- **Attribute**: Property of entity (Name, Age)
- **Relationship**: Association between entities (Student enrolls in Course)

**68. Strong entity vs weak entity**
- **Strong Entity**: Has primary key, exists independently
- **Weak Entity**: No primary key, depends on strong entity for identification

**69. Cardinality & participation constraints**
- **Cardinality**: Number of instances in relationship (1:1, 1:M, M:N)
- **Participation**: Total (every entity participates) vs Partial (some entities participate)

**70. Generalization/specialization (ISA)**
- **Generalization**: Bottom-up approach, combine similar entities
- **Specialization**: Top-down approach, create subclasses from general entity
- **ISA**: "Is-A" relationship between superclass and subclass

**71. Aggregation (basic)**
Aggregation treats relationship as higher-level entity, allowing relationships between relationships.

### Relational Algebra (Sometimes)

**72. Selection vs projection**
- **Selection (σ)**: Selects rows that satisfy given condition (horizontal subset)
- **Projection (π)**: Selects specific columns (vertical subset)

**73. Union vs intersection vs difference**
- **Union (∪)**: All tuples from both relations (no duplicates)
- **Intersection (∩)**: Common tuples in both relations
- **Difference (-)**: Tuples in first relation but not in second

**74. Cartesian product meaning**
Cartesian product (×) combines every tuple from first relation with every tuple from second relation.

**75. Join operation concept**
Join combines tuples from two relations based on specified condition, typically equality of common attributes.

### Stored Procedures, Functions, Triggers (Sometimes)

**76. Stored procedure vs function**
| Feature | Stored Procedure | Function |
|---------|------------------|----------|
| Return value | Optional | Must return value |
| Call method | CALL/EXEC | SELECT statement |
| Parameters | IN, OUT, INOUT | Only IN |
| Usage | Complex operations | Calculations |

**77. Trigger: what and why?**
Trigger is special stored procedure that automatically executes in response to database events (INSERT, UPDATE, DELETE).
**Why use:**
- Enforce business rules
- Audit changes
- Maintain derived data
- Log activities

**78. When to use triggers?**
- Automatic auditing
- Data validation beyond constraints
- Maintaining calculated fields
- Logging database changes
- Enforcing complex business rules

**79. Example use-case of trigger**
```sql
CREATE TRIGGER update_last_modified
BEFORE UPDATE ON employees
FOR EACH ROW
SET NEW.last_modified = NOW();
```

## SQL Query Question Bank (Most Important)

### Basic SELECT

**80. Select all columns from a table**
```sql
SELECT * FROM employees;
```

**81. Select specific columns**
```sql
SELECT name, salary, department FROM employees;
```

**82. DISTINCT usage**
```sql
SELECT DISTINCT department FROM employees;
```

**83. WHERE with AND/OR/NOT**
```sql
SELECT * FROM employees 
WHERE salary > 50000 AND department = 'IT' OR NOT status = 'Inactive';
```

**84. BETWEEN / IN / LIKE patterns**
```sql
SELECT * FROM employees WHERE salary BETWEEN 40000 AND 80000;
SELECT * FROM employees WHERE department IN ('IT', 'HR', 'Finance');
SELECT * FROM employees WHERE name LIKE 'J%' OR name LIKE '%son';
```

**85. ORDER BY ascending/descending**
```sql
SELECT * FROM employees ORDER BY salary DESC, name ASC;
```

**86. LIMIT / TOP usage (based on DB)**
```sql
-- MySQL
SELECT * FROM employees LIMIT 10;
-- SQL Server
SELECT TOP 10 * FROM employees;
```

### Aggregates + GROUP BY

**87. COUNT, SUM, AVG, MIN, MAX**
```sql
SELECT COUNT(*) as total_employees,
       SUM(salary) as total_salary,
       AVG(salary) as avg_salary,
       MIN(salary) as min_salary,
       MAX(salary) as max_salary
FROM employees;
```

**88. GROUP BY on department/product/category**
```sql
SELECT department, COUNT(*) as emp_count, AVG(salary) as avg_salary
FROM employees
GROUP BY department;
```

**89. HAVING vs WHERE (very common)**
```sql
-- WHERE filters rows before grouping
SELECT department, AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department;

-- HAVING filters groups after grouping
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

**90. Count employees in each department**
```sql
SELECT d.name, COUNT(e.id) as employee_count
FROM departments d
LEFT JOIN employees e ON d.id = e.department_id
GROUP BY d.id, d.name;
```

**91. Department having count > N**
```sql
SELECT department, COUNT(*) as emp_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

**92. Find duplicate records using GROUP BY HAVING**
```sql
SELECT email, COUNT(*) as count
FROM employees
GROUP BY email
HAVING COUNT(*) > 1;
```

### Joins (Very Common)

**93. Employee table + Department table join**
```sql
SELECT e.name, e.salary, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;
```

**94. Get employee name + department name**
```sql
SELECT e.name as employee_name, d.name as department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;
```

**95. Find employees with no department (LEFT join + NULL)**
```sql
SELECT e.name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id
WHERE d.id IS NULL;
```

**96. Self join: employee-manager mapping**
```sql
SELECT e.name as employee, m.name as manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id;
```

**97. Find customers who placed no orders (LEFT join)**
```sql
SELECT c.name
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
WHERE o.customer_id IS NULL;
```

### Top N / Nth Highest (TCS Classic)

**98. Highest salary in company**
```sql
SELECT MAX(salary) as highest_salary FROM employees;
```

**99. Second highest salary**
```sql
SELECT MAX(salary) as second_highest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);

-- OR using LIMIT
SELECT salary FROM employees
ORDER BY salary DESC LIMIT 1 OFFSET 1;
```

**100. Nth highest salary (general)**
```sql
SELECT salary FROM employees
ORDER BY salary DESC LIMIT 1 OFFSET (N-1);

-- OR using window function
SELECT DISTINCT salary FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) as rank
    FROM employees
) ranked WHERE rank = N;
```

**101. Second highest salary per department**
```sql
SELECT department_id, salary FROM (
    SELECT department_id, salary,
           DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) as rank
    FROM employees
) ranked WHERE rank = 2;
```

**102. Top 3 salaries per department**
```sql
SELECT department_id, name, salary FROM (
    SELECT department_id, name, salary,
           DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) as rank
    FROM employees
) ranked WHERE rank <= 3;
```

**103. Highest paid employee in each department**
```sql
SELECT e.department_id, e.name, e.salary
FROM employees e
WHERE e.salary = (
    SELECT MAX(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e.department_id
);
```

**104. Employees earning more than department average**
```sql
SELECT e1.name, e1.salary, e1.department_id
FROM employees e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

### Window Functions (Asked When Panel is Strong)

**105. ROW_NUMBER vs RANK vs DENSE_RANK**
```sql
SELECT name, salary,
       ROW_NUMBER() OVER (ORDER BY salary DESC) as row_num,
       RANK() OVER (ORDER BY salary DESC) as rank_val,
       DENSE_RANK() OVER (ORDER BY salary DESC) as dense_rank_val
FROM employees;
```

**106. Find duplicates using ROW_NUMBER**
```sql
SELECT * FROM (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY email ORDER BY id) as rn
    FROM employees
) WHERE rn > 1;
```

**107. Running total salary by date**
```sql
SELECT name, salary, hire_date,
       SUM(salary) OVER (ORDER BY hire_date) as running_total
FROM employees;
```

**108. Moving average (basic)**
```sql
SELECT name, salary,
       AVG(salary) OVER (ORDER BY hire_date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) as moving_avg
FROM employees;
```

**109. Top N per group using DENSE_RANK**
```sql
SELECT * FROM (
    SELECT department_id, name, salary,
           DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) as rank
    FROM employees
) WHERE rank <= 3;
```

### Subqueries (Very Common)

**110. Employees whose salary > average salary**
```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**111. Employees in departments located in "X"**
```sql
SELECT e.name
FROM employees e
WHERE e.department_id IN (
    SELECT d.id FROM departments d WHERE d.location = 'New York'
);
```

**112. Correlated subquery example**
```sql
SELECT e1.name, e1.salary
FROM employees e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

**113. EXISTS vs IN difference + use case**
```sql
-- EXISTS (better for performance with NULLs)
SELECT c.name FROM customers c
WHERE EXISTS (SELECT 1 FROM orders o WHERE o.customer_id = c.id);

-- IN (simpler syntax)
SELECT c.name FROM customers c
WHERE c.id IN (SELECT customer_id FROM orders);
```

**114. Find departments with no employees**
```sql
SELECT d.name
FROM departments d
WHERE NOT EXISTS (
    SELECT 1 FROM employees e WHERE e.department_id = d.id
);
```

### String Queries

**115. Names starting with 'A', ending with 'n'**
```sql
SELECT name FROM employees WHERE name LIKE 'A%';
SELECT name FROM employees WHERE name LIKE '%n';
SELECT name FROM employees WHERE name LIKE 'A%n';
```

**116. Find length of strings**
```sql
SELECT name, LENGTH(name) as name_length FROM employees;
```

**117. Convert to uppercase/lowercase**
```sql
SELECT UPPER(name) as upper_name, LOWER(name) as lower_name FROM employees;
```

**118. Extract substring**
```sql
SELECT name, SUBSTRING(name, 1, 3) as first_three_chars FROM employees;
```

**119. Replace characters**
```sql
SELECT name, REPLACE(name, 'a', '@') as modified_name FROM employees;
```

**120. Concatenate first and last name**
```sql
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM employees;
```

### Date/Time Queries

**121. Current date/time**
```sql
SELECT NOW() as current_datetime, CURDATE() as current_date, CURTIME() as current_time;
```

**122. Orders in last 30 days**
```sql
SELECT * FROM orders WHERE order_date >= DATE_SUB(NOW(), INTERVAL 30 DAY);
```

**123. Group by month/year**
```sql
SELECT YEAR(order_date) as year, MONTH(order_date) as month, COUNT(*) as order_count
FROM orders
GROUP BY YEAR(order_date), MONTH(order_date);
```

**124. Find day difference between two dates**
```sql
SELECT DATEDIFF(end_date, start_date) as days_difference FROM projects;
```

**125. Find oldest/newest record by date**
```sql
SELECT * FROM employees WHERE hire_date = (SELECT MIN(hire_date) FROM employees);
SELECT * FROM employees WHERE hire_date = (SELECT MAX(hire_date) FROM employees);
```

### NULL Handling

**126. IS NULL / IS NOT NULL**
```sql
SELECT * FROM employees WHERE manager_id IS NULL;
SELECT * FROM employees WHERE phone IS NOT NULL;
```

**127. COALESCE / NVL use**
```sql
SELECT name, COALESCE(phone, 'No Phone') as contact FROM employees;
```

**128. Count NULL vs non-NULL entries**
```sql
SELECT 
    COUNT(*) as total_records,
    COUNT(phone) as non_null_phones,
    COUNT(*) - COUNT(phone) as null_phones
FROM employees;
```

### Set Operations (Sometimes)

**129. UNION vs UNION ALL**
```sql
-- UNION (removes duplicates)
SELECT name FROM employees UNION SELECT name FROM contractors;

-- UNION ALL (keeps duplicates)
SELECT name FROM employees UNION ALL SELECT name FROM contractors;
```

**130. INTERSECT**
```sql
SELECT name FROM employees INTERSECT SELECT name FROM contractors;
```

**131. EXCEPT / MINUS**
```sql
SELECT name FROM employees EXCEPT SELECT name FROM contractors;
```

### Update/Delete/DDL Practical

**132. Create a table with constraints**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    salary DECIMAL(10,2) CHECK (salary > 0),
    department_id INT,
    hire_date DATE DEFAULT CURRENT_DATE,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```

**133. Add a column**
```sql
ALTER TABLE employees ADD COLUMN phone VARCHAR(15);
```

**134. Drop a column**
```sql
ALTER TABLE employees DROP COLUMN phone;
```

**135. Rename column/table**
```sql
ALTER TABLE employees RENAME COLUMN phone TO contact_number;
ALTER TABLE employees RENAME TO staff;
```

**136. Update salary for a department**
```sql
UPDATE employees SET salary = salary * 1.1 WHERE department_id = 1;
```

**137. Delete rows with condition**
```sql
DELETE FROM employees WHERE status = 'Inactive' AND last_login < '2023-01-01';
```

**138. TRUNCATE vs DELETE example**
```sql
-- DELETE (can rollback, slower, can use WHERE)
DELETE FROM temp_employees WHERE created_date < '2023-01-01';

-- TRUNCATE (cannot rollback, faster, removes all rows)
TRUNCATE TABLE temp_employees;
```

### Classic "Edge-Case" SQL Problems

**139. Find employees with same salary**
```sql
SELECT salary, GROUP_CONCAT(name) as employees
FROM employees
GROUP BY salary
HAVING COUNT(*) > 1;
```

**140. Find consecutive login dates / streaks (basic)**
```sql
SELECT user_id, login_date,
       ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) as rn,
       DATE_SUB(login_date, INTERVAL ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) DAY) as group_date
FROM user_logins;
```

**141. Find customers with more than one order**
```sql
SELECT customer_id, COUNT(*) as order_count
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

**142. Find the most purchased product**
```sql
SELECT product_id, SUM(quantity) as total_quantity
FROM order_items
GROUP BY product_id
ORDER BY total_quantity DESC
LIMIT 1;
```

**143. Find the second most purchased product**
```sql
SELECT product_id, total_quantity FROM (
    SELECT product_id, SUM(quantity) as total_quantity,
           DENSE_RANK() OVER (ORDER BY SUM(quantity) DESC) as rank
    FROM order_items
    GROUP BY product_id
) ranked WHERE rank = 2;
```

**144. Find duplicate emails/phone numbers**
```sql
SELECT email, COUNT(*) as count
FROM employees
GROUP BY email
HAVING COUNT(*) > 1;
```

**145. Swap gender values ('M' ↔ 'F') using UPDATE**
```sql
UPDATE employees 
SET gender = CASE 
    WHEN gender = 'M' THEN 'F'
    WHEN gender = 'F' THEN 'M'
    ELSE gender
END;
```

**146. Retrieve records present in table A but not in table B**
```sql
SELECT * FROM table_a
WHERE id NOT IN (SELECT id FROM table_b WHERE id IS NOT NULL);

-- OR using LEFT JOIN
SELECT a.* FROM table_a a
LEFT JOIN table_b b ON a.id = b.id
WHERE b.id IS NULL;
```

**147. Find number of employees joined each year**
```sql
SELECT YEAR(hire_date) as year, COUNT(*) as employees_joined
FROM employees
GROUP BY YEAR(hire_date)
ORDER BY year;
```

## "Interview Twister" Questions (They Love These)

**148. Difference between WHERE and HAVING with an example query**
WHERE filters individual rows before grouping, HAVING filters groups after GROUP BY.
```sql
-- WHERE example (filters rows)
SELECT department, AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department;

-- HAVING example (filters groups)
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

**149. Can we use aggregate function in WHERE?**
No, aggregate functions cannot be used in WHERE clause. Use HAVING instead.
```sql
-- WRONG
SELECT * FROM employees WHERE AVG(salary) > 50000;

-- CORRECT
SELECT department FROM employees 
GROUP BY department 
HAVING AVG(salary) > 50000;
```

**150. Why GROUP BY requires non-aggregated columns?**
Because GROUP BY creates groups, and non-aggregated columns must be functionally dependent on the grouping columns to ensure deterministic results.

**151. What is the difference between UNION and JOIN?**
- **UNION**: Combines rows from multiple tables vertically (same structure required)
- **JOIN**: Combines columns from multiple tables horizontally (based on relationships)

**152. Why indexes speed up reads but slow down writes?**
- **Reads**: Index provides direct path to data like a book's index
- **Writes**: Must update both table data and all associated indexes, causing overhead

**153. Why DELETE is slower than TRUNCATE?**
- **DELETE**: Logs each row deletion, can be rolled back, fires triggers
- **TRUNCATE**: Deallocates data pages, minimal logging, cannot be rolled back

**154. What is referential integrity? Give real example**
Referential integrity ensures foreign key values exist in referenced table.
**Example:** Employee.DepartmentID must exist in Department.ID table. Cannot assign employee to non-existent department.

**155. When will FULL OUTER JOIN return NULLs?**
- NULLs from left table when no matching record in right table
- NULLs from right table when no matching record in left table

**156. What is the difference between RANK and DENSE_RANK?**
- **RANK**: Skips numbers after ties (1,2,2,4,5)
- **DENSE_RANK**: No gaps after ties (1,2,2,3,4)

**157. What happens if primary key has NULL? (it can't)**
Primary key cannot have NULL values. It will result in constraint violation error.

**158. Can a table have multiple foreign keys?**
Yes, a table can have multiple foreign keys referencing different tables or even the same table.

**159. If you use LEFT JOIN then apply WHERE condition on right table, what happens?**
WHERE condition on right table converts LEFT JOIN to INNER JOIN because NULL values from unmatched left table records are filtered out.

## Mini "Must-Practice SQL Set" (Top 20 for Prime Interviews)

**160. 2nd highest salary**
```sql
SELECT MAX(salary) FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**161. Nth highest salary**
```sql
SELECT salary FROM employees 
ORDER BY salary DESC LIMIT 1 OFFSET (N-1);
```

**162. Top 3 salary per department**
```sql
SELECT * FROM (
    SELECT *, DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) as rank
    FROM employees
) WHERE rank <= 3;
```

**163. Highest salary per department**
```sql
SELECT department_id, MAX(salary) FROM employees GROUP BY department_id;
```

**164. Employee > avg salary**
```sql
SELECT * FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);
```

**165. Dept with no employees**
```sql
SELECT d.* FROM departments d
LEFT JOIN employees e ON d.id = e.department_id
WHERE e.department_id IS NULL;
```

**166. Customers with no orders**
```sql
SELECT c.* FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
WHERE o.customer_id IS NULL;
```

**167. Duplicate rows detection**
```sql
SELECT *, COUNT(*) FROM employees 
GROUP BY name, email 
HAVING COUNT(*) > 1;
```

**168. RANK vs DENSE_RANK query**
```sql
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) as rank_val,
       DENSE_RANK() OVER (ORDER BY salary DESC) as dense_rank_val
FROM employees;
```

**169. Employees and manager (self join)**
```sql
SELECT e.name as employee, m.name as manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id;
```

**170. JOIN employee + dept**
```sql
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;
```

**171. GROUP BY + HAVING**
```sql
SELECT department_id, COUNT(*), AVG(salary)
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

**172. COUNT per department**
```sql
SELECT d.name, COUNT(e.id) as employee_count
FROM departments d
LEFT JOIN employees e ON d.id = e.department_id
GROUP BY d.id, d.name;
```

**173. MAX salary overall**
```sql
SELECT MAX(salary) as highest_salary FROM employees;
```

**174. Delete vs truncate vs drop (theory)**
- **DELETE**: Removes rows, can rollback, uses WHERE
- **TRUNCATE**: Removes all rows, cannot rollback, faster
- **DROP**: Removes entire table structure

**175. Index and view (theory)**
- **Index**: Improves query performance, physical structure
- **View**: Virtual table, logical structure, simplifies queries

**176. ACID properties**
- **Atomicity**: All or nothing
- **Consistency**: Valid state maintained
- **Isolation**: Transactions don't interfere
- **Durability**: Changes are permanent

**177. Normalization (1NF–BCNF)**
- **1NF**: Atomic values
- **2NF**: No partial dependency
- **3NF**: No transitive dependency
- **BCNF**: Every determinant is candidate key

**178. Foreign key + cascade behavior**
- **CASCADE**: Delete/update related records
- **SET NULL**: Set foreign key to NULL
- **RESTRICT**: Prevent operation if references exist

**179. Transaction + COMMIT/ROLLBACK/SAVEPOINT**
```sql
BEGIN TRANSACTION;
INSERT INTO employees VALUES (1, 'John', 50000);
SAVEPOINT sp1;
UPDATE employees SET salary = 55000 WHERE id = 1;
ROLLBACK TO sp1;  -- Undo update, keep insert
COMMIT;  -- Save insert
```

---

**Total Questions Covered: 179**

This comprehensive guide covers ALL questions from your DBMS.txt file with detailed answers, examples, and SQL queries. Perfect for TCS interview preparation! 🎯