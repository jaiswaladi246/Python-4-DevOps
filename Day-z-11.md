
# Databases

A **database** is a structured collection of data organized in a way that it can be easily accessed, managed, and updated. Databases are used to store and retrieve information for various purposes such as managing business operations, storing user information in web applications, and more.

### Relational Models:

The **relational model** is a way of organizing data in tables (relations) with rows (tuples) and columns (attributes). It was introduced by Edgar Codd in the early 1970s. In a relational database, data is organized into one or more tables, and relationships between the tables are established using keys.

### Tables, Rows, and Columns:

- **Table**: A table is a collection of related data organized in rows and columns. Each table in a database has a unique name.

- **Row (Tuple)**: A row represents a single record or entry in a table. It contains a set of values corresponding to the attributes (columns) defined for that table.

- **Column (Attribute)**: A column represents a specific type of data in a table. It defines the kind of information that will be stored in that column.

### Keys:

- **Primary Key**: A primary key is a unique identifier for each record in a table. It ensures that each row can be uniquely identified. Primary keys are used to enforce entity integrity.

- **Foreign Key**: A foreign key is a field in a table that refers to the primary key in another table. It establishes relationships between tables.

#### Examples for primary keys and foreign keys with accompanying table diagrams.

##### Example with Primary Key:

**Scenario: Customers and Orders**

In this example, we have two tables, one for customers and one for orders. Each customer has a unique identifier, and each order is associated with a specific customer.

**Tables:**

1. Customers Table:
   - Columns: customer_id (Primary Key), customer_name, email

2. Orders Table:
   - Columns: order_id (Primary Key), customer_id (Foreign Key), order_date, total_amount

**Table Diagram:**

```
Customers Table
+-------------+-------------------+----------------------+
| customer_id | customer_name     | email                |
+-------------+-------------------+----------------------+
|     1       |   John Doe        | john@example.com     |
|     2       |   Jane Smith      | jane@example.com     |
|     3       |   Bob Johnson     | bob@example.com      |
+-------------+-------------------+----------------------+

Orders Table
+------------+--------------+---------------------+---------------+
| order_id   | customer_id  | order_date          | total_amount  |
+------------+--------------+---------------------+---------------+
|    101     |      1       |  2023-11-01         |     100       |
|    102     |      2       |  2023-11-02         |     150       |
|    103     |      1       |  2023-11-02         |     200       |
+------------+--------------+---------------------+---------------+
```

In this example, `customer_id` is the primary key in the Customers table, ensuring each customer has a unique identifier. The Orders table has a `customer_id` column, which is a foreign key referencing the primary key in the Customers table, establishing a relationship between the two tables.

##### Example with Foreign Key:

**Scenario: Employees and Departments**

In this example, we have two tables, one for employees and one for departments. Each employee belongs to a specific department, which is represented by a foreign key in the Employees table.

**Tables:**

1. Employees Table:
   - Columns: employee_id (Primary Key), employee_name, department_id (Foreign Key), position

2. Departments Table:
   - Columns: department_id (Primary Key), department_name

**Table Diagram:**

```
Employees Table
+-----------------+------------------+------------------+----------------+
| employee_id     | employee_name    | department_id    | position       |
+-----------------+------------------+------------------+----------------+
|       1         |   John Doe       |        101       |  Manager       |
|       2         |   Jane Smith     |        102       |  Sales Rep     |
|       3         |   Bob Johnson    |        101       |  Analyst       |
+-----------------+------------------+------------------+----------------+

Departments Table
+------------------+----------------------+
| department_id   | department_name     |
+------------------+----------------------+
|       101        |   Sales             |
|       102        |   Marketing         |
+------------------+----------------------+
```

In this example, `employee_id` is the primary key in the Employees table. The `department_id` column in the Employees table is a foreign key referencing the primary key in the Departments table. This establishes a relationship between employees and their respective departments.

These examples demonstrate the use of primary keys and foreign keys to establish relationships between tables in a relational database.

### Relationships:

- **One-to-One**: A relationship where one record in a table is associated with exactly one record in another table.

- **One-to-Many**: A relationship where one record in a table can be associated with multiple records in another table.

- **Many-to-Many**: A relationship where multiple records in a table can be associated with multiple records in another table.

## Examples for each type of relationship along with a simple table diagram.

### One-to-One Relationship:

**Example: Users and User Profiles**

In a one-to-one relationship, one record in a table is associated with exactly one record in another table.

**Tables:**

1. Users Table:
   - Columns: user_id (Primary Key), username, email

2. User Profiles Table:
   - Columns: profile_id (Primary Key), user_id (Foreign Key), first_name, last_name, date_of_birth

**Table Diagram:**

```
Users Table
+---------+-----------+---------------------+
| user_id | username  | email               |
+---------+-----------+---------------------+
|   1     | john_doe  | john@example.com    |
|   2     | jane_doe  | jane@example.com    |
+---------+-----------+---------------------+

User Profiles Table
+------------+---------+------------+-----------+
| profile_id | user_id | first_name | last_name |
+------------+---------+------------+-----------+
|    1       |   1     |   John     |   Doe     |
|    2       |   2     |   Jane     |   Doe     |
+------------+---------+------------+-----------+
```

### One-to-Many Relationship:

**Example: Departments and Employees**

In a one-to-many relationship, one record in a table can be associated with multiple records in another table.

**Tables:**

1. Departments Table:
   - Columns: department_id (Primary Key), department_name

2. Employees Table:
   - Columns: employee_id (Primary Key), department_id (Foreign Key), employee_name, position

**Table Diagram:**

```
Departments Table
+------------------+----------------------+
| department_id   | department_name     |
+------------------+----------------------+
|       1          |   Sales             |
|       2          |   Marketing         |
+------------------+----------------------+

Employees Table
+-----------------+------------------+----------------+
| employee_id     | department_id    | employee_name  | position   |
+-----------------+------------------+----------------+
|       1         |   1              |   John Doe     |  Manager   |
|       2         |   1              |   Jane Smith   |  Sales Rep |
|       3         |   2              |   Bob Johnson  |  Analyst   |
+-----------------+------------------+----------------+
```

### Many-to-Many Relationship:

**Example: Students and Courses**

In a many-to-many relationship, multiple records in a table can be associated with multiple records in another table.

**Tables:**

1. Students Table:
   - Columns: student_id (Primary Key), student_name

2. Courses Table:
   - Columns: course_id (Primary Key), course_name

3. Enrollment Table (Join Table):
   - Columns: enrollment_id (Primary Key), student_id (Foreign Key), course_id (Foreign Key)

**Table Diagram:**

```
Students Table
+-------------+-------------------+
| student_id  | student_name      |
+-------------+-------------------+
|     1       |   John Doe        |
|     2       |   Jane Smith      |
|     3       |   Bob Johnson     |
+-------------+-------------------+

Courses Table
+------------+---------------------+
| course_id  | course_name         |
+------------+---------------------+
|    101     |   Math 101          |
|    102     |   English 101       |
|    103     |   History 101       |
+------------+---------------------+

Enrollment Table
+----------------+-------------+------------+
| enrollment_id  | student_id  | course_id  |
+----------------+-------------+------------+
|      1         |      1      |     101    |
|      2         |      1      |     102    |
|      3         |      2      |     101    |
|      4         |      3      |     103    |
+----------------+-------------+------------+
```

These examples illustrate different types of relationships in a relational database. Understanding these concepts is crucial for designing and working with databases effectively.

### Normalization:

**Normalization** is a process used in database design to organize a database into tables in such a way that redundancy is minimized. This is achieved by dividing a large table into smaller tables and defining relationships between them.

### SQL (Structured Query Language):

SQL is a domain-specific language used for managing and querying relational databases. It provides commands for creating, retrieving, updating, and deleting data from databases. Some common SQL commands include `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `CREATE`, `DROP`, and more.

### Examples:

Let's illustrate some of these concepts with a simple example. Consider two tables, `Customers` and `Orders`:

**Customers Table**:

| CustomerID | Name   | Email           |
|------------|--------|-----------------|
| 1          | Alice  | alice@example.com|
| 2          | Bob    | bob@example.com  |
| 3          | Charlie| charlie@example.com|

**Orders Table**:

| OrderID | CustomerID | Product     | Quantity |
|---------|------------|-------------|----------|
| 101     | 1          | Product A   | 2        |
| 102     | 2          | Product B   | 3        |
| 103     | 1          | Product C   | 1        |

In this example, `CustomerID` is the primary key in the `Customers` table, and it is also a foreign key in the `Orders` table, establishing a one-to-many relationship.

These are some of the basic concepts related to databases and the relational model. There are many more advanced topics in database management and design, but understanding these fundamentals is a great starting point.
