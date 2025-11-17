## Q. Explain normalization and briefly describe the different normal forms
Normalization organizes relational data to minimize redundancy and prevent update/insert/delete anomalies by splitting tables based on dependencies while preserving meaning.

- 1NF requires each column to hold atomic values and no repeating groups.
- 2NF is 1NF plus no partial dependence on a composite key—every non-key must depend on the whole key.
- 3NF is 2NF plus no transitive dependencies—non-keys depend only on the key, not on other non-keys.
- BCNF strengthens 3NF: for every functional dependency X→Y, X must be a candidate key (fixes edge cases like overlapping keys)
- 4NF removes multi-valued dependencies .
- 5NF (PJNF) eliminates join dependencies, decomposing so tables can be losslessly recombined without spurious tuple.

## Q.What are the main types of SQL commands?
SQL commands are broadly classified into:

- DDL (Data Definition Language): CREATE, ALTER, DROP, TRUNCATE.
- DML (Data Manipulation Language): SELECT, INSERT, UPDATE, DELETE.
- DCL (Data Control Language): GRANT, REVOKE.
- TCL (Transaction Control Language): COMMIT, ROLLBACK, SAVEPOINT.

## Q. What are the different operators available in SQL?
- Arithmetic Operators: +, -, *, /, %
- Comparison Operators: =, !=, <>, >, <, >=, <=
- Logical Operators: AND, OR, NOT
- Set Operators: UNION, INTERSECT, EXCEPT
- Special Operators: BETWEEN, IN, LIKE, IS NULL
- Concatenation Operators:|| (Oracle, PostgreSQL) or + (SQL Server) to combine strings.

## Q. What are the types of Joins in SQL Server?
SQL joins combine rows from two tables based on a matching condition (typically keys) to answer questions that span both tables.

- An INNER JOIN returns only matches that exist in both tables (the intersection).
- A LEFT JOIN returns all rows from the left table and the matching rows from the right; when there’s no match, right-side columns are NULL.
- A RIGHT JOIN is the mirror image: all rows from the right table plus matches from the left, NULL when absent.
- A FULL (OUTER) JOIN returns all rows from either table, filling in NULL where a counterpart is missing.
- A CROSS JOIN returns the cartesian product of two tables—every row from A paired with every row from B so the result size is rows(A) × rows(B), and it doesn’t use a join condition


An INNER JOIN returns only the rows where the specified join condition matches between the two tables (e.g., matching keys), so its result is a filtered subset, not every combination

Use a cross join for generating combinations (dates × products, sizes × colors) .
When you intentionally need all pairings; use an inner join to combine related records.

## Q. What are aggregate functions in SQL?
Aggregate functions perform calculations on a set of values and return a single value. Common aggregate functions include:

- COUNT(): Returns the number of rows.
- SUM(): Returns the total sum of values.
- AVG(): Returns the average of values.
- MIN(): Returns the smallest value.
- MAX(): Returns the largest value.

## Q. What is Self-Join?

## Q. What is lef-Join, Right-Join, Corss-join, full-join?

## Q. What are Indexes in SQL Server?
Indexes are database objects that improve query performance by allowing faster retrieval of rows. They function like a book’s index, making it quicker to find specific data without scanning the entire table. However, indexes require additional storage and can slightly slow down data modification operations. Types of Indexes:

- **Clustered Index:** Sorts and stores data rows in order of the key (only one per table).
- **Non-Clustered Index:** Separate structure with pointers to data rows (can be many per table).
- **Unique Index:** Ensures no duplicate values.
- **Composite Index:** Index on multiple columns.

## Q. What is Clustered index?

## Q. What is Non-Clustered index?

## Q.Explain foreign keys and how they enforce referential integrity
A foreign key (FK) is a column (or set of columns) in a child table that references a primary/unique key in a parent table to ensure the child’s values actually exist in the parent. This enforces referential integrity by preventing actions that would create “orphan” rows.

## Q. What is the difference between Clustered and Non-Clustered index?
A clustered index stores table rows in the physical order of the index key (the data pages are the index), so you can have only one; it’s ideal for range scans and primary-key lookups.

- Key is narrow, stable, and increasing (e.g., order_id, order_date).
- Queries often do range scans or ORDER BY on that key.
A non-clustered index is a separate structure (key → row locator) and you can have many; it accelerates specific filters, joins, and sorts without changing the table’s row order.

- You need fast point lookups or high-selectivity filters (WHERE email=?).
- Columns are common JOIN/GROUP BY/ORDER BY targets.
- You can cover queries via INCLUDEd columns.

## Q. How to create Clustered and Non-Clustered index in a table?

## Q. In which column you will apply the indexing to optimize this query?
Apply clustered index on columns which ar ebeing searched or have where condition to optimize search output. 

## Q. How to handle null in t-sql. to set some default value?
IsNull() or collese()

## Q. what is the difference between RANK(), DENSE_RANK() and ROW_NUMBER()
ROW_NUMBER() assigns a unique sequential number to each row within a partition based on the order—no ties share a number (ties are broken arbitrarily by the ORDER BY). RANK() assigns the same rank to tied rows but leaves gaps after ties (1,1,3…). DENSE_RANK() also assigns the same rank to ties but doesn’t leave gaps (1,1,2…).


## Q. Tips to optimize t-sql 
- First measure: reproduce the issue, capture timings, and run EXPLAIN/EXPLAIN ANALYZE to see the plan, row estimates, and bottlenecks
- Next, fix fundamentals: ensure current statistics, right indexes
- sargable predicates (avoid functions on columns, leading % wildcards, or expressions that prevent
- Reduce data early with selective WHERE filters, fetch only needed columns (no SELECT *), and prefer EXISTS over IN for semi-joins
- Tame row explosion by checking JOIN selectivity, de-duplicating before joins, and pre-aggregating where helpful.
- Rewrite problematic patterns (split wide ORs into UNION ALL, replace correlated subqueries with joins, consider window functions carefully)
- For large sets, use keyset pagination (seek method) instead of OFFSET, and consider materialized views, caching, or partitioning for heavy, recurring analytics.

## Q. Difference between Fucntions and SP ? 

## Q. Difference between delete , trucate and drop? 
TRUNCATE is a DDL command, while DELETE is a DML command, which is why they differ in speed and logging behavior.

- **DELETE:** Removes rows one at a time and records each deletion in the transaction log, allowing rollback. It can have a WHERE clause. Identity value does not reset with DELETE
- **TRUNCATE:** Removes all rows at once without logging individual row deletions. It cannot have a WHERE clause and is faster than DELETE for large data sets. ˇIdentity value get reset with TRUNCATE
- **DROP:** drop table , you make need to Create DDL to recreate table

## Q. Waht is CTE? 
A CTE (Common Table Expression) is a temporary, named result set defined with WITH that exists only for the duration of a single statement. You use CTEs to break complex logic into steps, avoid repeating the same subquery, improve readability/maintenance, enable recursion (e.g., org charts, folder trees), and make debugging easier.

## Q. Waht is filter Index?

## Q. What is Index View?

## Q. What is view? 
A view is a virtual table created by a SELECT query. It does not store data itself, but presents data from one or more tables in a structured way. Views simplify complex queries, improve readability, and enhance security by restricting access to specific rows or columns.

## Q. what is updateable view?

## Q. What is ouptput of below SQL 

Select 1 from Employee 
if Emplyee table has below data 
| id   | Name  | departmeent name  | 
| --------| -------- | -------| 
| 1  | Rakesh  | Account | 
| 1  | Sunil   | Finace  | 
| 1  | Mukesh  | Timeoffice | 

Ans: <br>
1<br>
1<br>
1

## Q. Write a SQL query to find the second highest salary from an Employee table.
```
SELECT MAX(Salary) AS SecondHighestSalary
FROM Employees
WHERE Salary < (SELECT MAX(Salary) FROM Employees);
```

## Q. How to get nth maximum salary with employee id 
## Q. Write a query to fetch top 3 highest salaries in each department.
```
SELECT *
FROM (
    SELECT 
        DepartmentId,
        EmployeeName,
        Salary,
        RANK() OVER (PARTITION BY DepartmentId ORDER BY Salary DESC) AS RankNo
    FROM Employees
) AS Ranked
WHERE RankNo <= 3;
```
## Q. How to get duplicate records from table 

## Q. What is the purpose of the UNIQUE constraint?
The UNIQUE constraint ensures that all values in a column (or combination of columns) are distinct. This prevents duplicate values and helps maintain data integrity.

## Q. What is a composite primary key?
A composite primary key uses two or more columns together to uniquely identify each row when one column alone isn’t sufficient.

## Q. Describe a PRIMARY KEY and how it differs from a UNIQUE key
A PRIMARY KEY uniquely identifies each row in a table: it combines UNIQUE + NOT NULL, there can be only one per table (though it can be composite across multiple columns), and it’s the default target for foreign keys.

A UNIQUE key also enforces uniqueness, but doesn’t require NOT NULL and you can have many UNIQUE constraints per table.

## Q. Explain the difference between the WHERE and HAVING clauses
WHERE filters individual rows before grouping or aggregation, so it can’t use aggregate functions like SUM or COUNT; it’s best for narrowing raw data early (e.g., a date range or status).

HAVING filters the resulting groups after GROUP BY, so it’s meant for conditions on aggregates (e.g., groups with totals above a threshold).

```
SELECT customer_id, COUNT(*) AS orders_2025
FROM orders
WHERE order_date >= '2025-01-01' AND order_date < '2026-01-01'      
GROUP BY customer_id
HAVING COUNT(*) > 5;      
```

## Q. What is the difference between UNION and UNION ALL?
UNION combines results from two (or more) SELECTs and removes duplicates (it performs a DISTINCT across all columns), which adds sorting/hash work and can be slower.

UNION ALL keeps duplicates and usually runs faster because it simply appends result sets.

Example:
```
SELECT Name FROM Customers  
UNION  
SELECT Name FROM Employees
```
Example:
```
SELECT Name FROM Customers  
UNION ALL  
SELECT Name FROM Employees;
```

## Q. Describe set operations like UNION, INTERSECT and EXCEPT and when each is useful
UNION, INTERSECT, and EXCEPT are SQL set operations that combine results from two queries with the same number of columns and compatible data types. UNION returns the distinct union of both result sets (removes duplicates).

Use it to merge similar data from multiple sources
INTERSECT returns only rows common to both queries—ideal for finding overlap.
EXCEPT (called MINUS in Oracle) returns rows in the first query that aren’t in the second.

## Q.Explain correlated subqueries and provide an example use case
A correlated subquery is a subquery that depends on the current row of the outer query—i.e., it references columns from the outer query and is re-evaluated for each outer row.

Example use case employees paid above their own department’s average:
```
SELECT e.employee_id, e.name, e.salary, e.department_id
FROM employees e
WHERE e.salary >
      (SELECT AVG(e2.salary)
       FROM employees e2
       WHERE e2.department_id = e.department_id);
```

## Q.What are the differences between SQL and NoSQL databases?
SQL is best for structured, reliable transactions, while NoSQL shines in handling massive, fast-changing, and unstructured data.

**SQL Databases:**

- Use structured tables with rows and columns.
- Rely on a fixed schema.
- Offer ACID properties.

**NoSQL Databases:**

- Use flexible, schema-less structures (e.g., key-value pairs, document stores).
- Are designed for horizontal scaling.
- Often focus on performance and scalability over strict consistency.

## Q.What are the types of constraints in SQL?
Constraints enforce rules that the data must follow, preventing invalid or inconsistent data from being entered:
Common constraints include:

- NOT NULL: Ensures a column cannot have NULL values.
- UNIQUE: Ensures all values in a column are distinct.
- PRIMARY KEY: Uniquely identifies each row in a table.
- FOREIGN KEY: Ensures referential integrity by linking to a primary key in another table.
- CHECK: Ensures that all values in a column satisfy a specific condition.
- DEFAULT: Sets a default value for a column when no value is specified.

## Q.What is a cursor in SQL?
A cursor is a database object used to retrieve, manipulate, and traverse through rows in a result set one row at a time. Cursors are helpful when performing operations that must be processed sequentially rather than in a set-based manner.

Types of Cursors (SQL Server):

- **STATIC**: Snapshot of result set, does not reflect changes.
- **DYNAMIC**: Reflects all changes made while the cursor is open.
- **FORWARD_ONLY**: Can only move forward through the result set.
- **KEYSET**: Uses a key to fetch rows; changes to non-key columns are visible.

## Q.What is a trigger in SQL?
A trigger is a set of SQL statements that automatically execute in response to certain events on a table, such as INSERT, UPDATE, or DELETE. Triggers help maintain data consistency, enforce business rules, and implement complex integrity constraints.

- **Types:** BEFORE or AFTER triggers (depending on DB).
- **Uses**: Enforce business rules, maintain audit logs, check data consistency.

## Q. What are temporary tables, and how are they used?
Temporary tables are tables that exist only for the duration of a session or a transaction. They are useful for storing intermediate results, simplifying complex queries, or performing operations on subsets of data without modifying the main tables.

**1. Local Temporary Tables:**

- Prefixed with # (e.g., #TempTable).
- Only visible to the session that created them.
- Automatically dropped when the session ends.

**2. Global Temporary Tables:**

- Prefixed with ## (e.g., ##GlobalTempTable).
- Visible to all sessions.
- Dropped when all sessions that reference them are closed.

## Q.What is a materialized view, and how does it differ from a standard view?
**Standard View:**

- A virtual table defined by a query.
- Does not store data; the underlying query is executed each time the view is referenced.
- A standard view shows real-time data.

**Materialized View:**

- A physical table that stores the result of the query.
- Data is precomputed and stored, making reads faster.
- Requires periodic refreshes to keep data up to date.
- materialized view is used to store aggregated sales data, updated nightly, for fast reporting.

## Q. What is the purpose of the SQL MERGE statement?
The MERGE statement combines multiple operations INSERT, UPDATE, and DELETE into one. It is used to synchronize two tables by:

- Inserting rows that don’t exist in the target table.
- Updating rows that already exist.
- Deleting rows from the target table based on conditions
- In SQL Server, MERGE can cause concurrency issues (race conditions or deadlocks).

```
MERGE INTO TargetTable T  
USING SourceTable S  
ON T.ID = S.ID  
WHEN MATCHED THEN  
    UPDATE SET T.Value = S.Value  
WHEN NOT MATCHED THEN  
    INSERT (ID, Value) VALUES (S.ID, S.Value);
```
## Q. How can you handle duplicates in a query without using DISTINCT?
**1. GROUP BY: **Aggregate rows to eliminate duplicates
```
SELECT Column1, MAX(Column2)  
FROM TableName  
GROUP BY Column1;
```
**2. ROW_NUMBER():** Assign a unique number to each row and filter by that
```
WITH CTE AS (  
    SELECT Column1, Column2, ROW_NUMBER() OVER (PARTITION BY Column1 ORDER BY Column2) AS RowNum  
    FROM TableName  
)  
SELECT * FROM CTE WHERE RowNum = 1;
```

## Q. What are the ACID properties of a transaction?
ACID is an acronym that stands for Atomicity, Consistency, Isolation, and Durability, four key properties that ensure database transactions are processed reliably.

**1. Atomicity:**

- A transaction is treated as a single unit of work, meaning all operations must succeed or fail as a whole.
- If any part of the transaction fails, the entire transaction is rolled back.
- Example: In banking, transferring money must debit one account and credit another; if one fails, both roll back.

**2. Consistency:**

- A transaction must take the database from one valid state to another, maintaining all defined rules and constraints.
- This ensures data integrity is preserved throughout the transaction process.
- Example: Inventory count cannot drop below zero.

**3. Isolation:**

- Transactions should not interfere with each other.
- Even if multiple transactions occur simultaneously, each must operate as if it were the only one in the system until it is complete.
- Example: Two people booking the same seat won’t overwrite each other’s data.

**4. Durability:**

- Once a transaction is committed, its changes must persist, even in the event of a system failure.
- This ensures the data remains stable after the transaction is successfully completed.
- Example: A confirmed order stays in the system despite a server restart.

## Q. What are the differences between isolation levels in SQL?
Isolation levels define the extent to which the operations in one transaction are isolated from those in other transactions. They are critical for managing concurrency and ensuring data integrity. Common isolation levels include:

**1. Read Uncommitted:**

- Allows reading uncommitted changes from other transactions.
- Can result in dirty reads, where a transaction reads data that might later be rolled back.

**2. Read Committed:**

- Ensures a transaction can only read committed data.
- Prevents dirty reads but does not protect against non-repeatable reads or phantom reads.

**3. Repeatable Read:**

- Ensures that if a transaction reads a row, that row cannot change until the transaction is complete.
- Prevents dirty reads and non-repeatable reads but not phantom reads.

**4. Serializable:**

- The highest level of isolation.
- Ensures full isolation by effectively serializing transactions, meaning no other transaction can read or modify data that another transaction is using.
- Prevents dirty reads, non-repeatable reads, and phantom reads, but may introduce performance overhead due to locking and reduced concurrency.

## Q. What is the purpose of the WITH (NOLOCK) hint in SQL Server?
- The WITH (NOLOCK) hint allows a query to read data without acquiring shared locks, effectively reading uncommitted data.
- It can improve performance by reducing contention for locks, especially on large tables that are frequently updated.
- Results may be inconsistent or unreliable, as the data read might change or be rolled back.

## Q. What is the purpose of the SQL EXCEPT operator?
The EXCEPT operator is used to return rows from one query’s result set that are not present in another query’s result set. It effectively performs a set difference, showing only the data that is unique to the first query.

```
SELECT ProductID FROM ProductsSold
EXCEPT
SELECT ProductID FROM ProductsReturned;
```

**Use Case:**

- To find discrepancies between datasets.
- To verify that certain data exists in one dataset but not in another.

**Performance Considerations:**

- EXCEPT works best when the datasets involved have appropriate indexing and when the result sets are relatively small.
- Large datasets without indexes may cause slower performance because the database has to compare each row.

## Q. How can you ensure data consistency across distributed databases?
**1. Use Distributed Transactions:** Implement two-phase commit (2PC) to ensure all participating databases commit changes simultaneously or roll back if any part fails.

**2. Implement Eventual Consistency:** If strong consistency isn’t required, allow data to become consistent over time. This approach is common in distributed systems where high availability is a priority.

**3. Conflict Resolution Mechanisms:** Use versioning, timestamps, or conflict detection rules to resolve inconsistencies.

**4. Data Replication and Synchronization:** Use reliable replication strategies to ensure that changes made in one database are propagated to others.

**5. Regular Audits and Validation:** Periodically verify that data remains consistent across databases and fix discrepancies as needed.

