# AMA Answers
1: **Diff TEXT and VARCHAR:** `TEXT` stores virtually unlimited length strings, while `VARCHAR` defines a specific character limit.

2: **RIGHT JOIN:** A `RIGHT JOIN` returns all records from the right table (the second table mentioned in the query) and the matched records from the left table. If there is no match, the result from the left side will contain `NULL`.

3: **Common Table Expressions (CTE):** A CTE is a temporary, named result set that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. It is created using the `WITH` keyword and helps break down complex, nested queries into more readable, logical building blocks.

4: **Normalization:** It is the process of organizing data in a database to reduce data redundancy and improve data integrity. It involves dividing large tables into smaller, related tables and linking them using relationships (like primary and foreign keys) according to normal forms (1NF, 2NF, 3NF).

5: **Python Exceptions:** Exceptions are used to handle runtime errors so the program doesn't abruptly crash. You place risky code inside a `try` block and handle specific errors in `except` blocks. You can also use `finally` to execute cleanup code regardless of whether an error occurred.

6: **The `href` attribute:** In HTML, `href` stands for "Hypertext REFerence". It is used inside an anchor tag (`<a>`) to specify the destination URL of a link (e.g., `<a href="[https://example.com](https://example.com)">Link</a>`).

7: **CASE Expression:** The `CASE` expression is SQL's way of handling IF-THEN-ELSE logic. It evaluates conditions sequentially and returns a specific value when the first condition is met. If no conditions are met, it returns the value in the `ELSE` clause.

8: **Git Hooks:** Git hooks are custom scripts that Git automatically executes before or after specific actions occur (like committing, pushing, or merging). They are often used to enforce formatting rules, run tests, or prevent bad commits (e.g., a `pre-commit` hook).

9: **Views vs. Materialized Views:**

* **View:** A saved SQL query that acts as a virtual table. The database runs the underlying query every time you access the view.
* **Materialized View:** Stores the actual data result of the query physically on disk. It provides much faster read performance but requires periodic refreshing to stay updated with the base tables.

10: **Recovering a deleted local branch:** You can recover it using `git reflog`.

1. Run `git reflog` to see a history of your HEAD movements.
2. Find the SHA hash of the commit where the branch existed.
3. Recreate the branch from that hash using: `git checkout -b <branch_name> <SHA_hash>`.

11: **Foreign Key and its Limitations:** A foreign key is a column (or group of columns) in one table that references the primary key of another table, ensuring referential integrity.

* **Limitations:** They can slow down `INSERT`, `UPDATE`, and `DELETE` operations because the database must check the constraints. They also complicate database migrations, table truncations, and bulk data loads.

12: **HTML Elements:** An HTML element is an individual component of an HTML document, usually consisting of a start tag, the content, and an end tag. For example, `<p>This is a paragraph.</p>` is an entire element.

13: **Data Redundancy:** In SQL and databases, data redundancy occurs when the exact same piece of data is stored in two or more separate places. This wastes storage space and creates data anomaly risks (if you update it in one place but forget to update it in another, your data becomes inconsistent).

14: **The `NTILE()` Window Function:** `NTILE(n)` divides an ordered result set into a specific number of roughly equal groups (or "buckets"), assigning a bucket number to each row. For example, `NTILE(4)` divides the data into quartiles, assigning a number from 1 to 4 to every row based on its rank.

15: **CROSS JOIN:** A `CROSS JOIN` produces a Cartesian product of two tables. It takes every single row from the first table and pairs it with every single row from the second table. If Table A has 10 rows and Table B has 5 rows, a cross join results in 50 rows.
