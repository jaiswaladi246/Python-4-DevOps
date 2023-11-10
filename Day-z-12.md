# Day-12 | Connecting to Postgres using python

Sure! Here are the steps to download and configure PostgreSQL on Windows:

1. **Download PostgreSQL**:

   - Go to the official PostgreSQL download page: [https://www.postgresql.org/download/windows/](https://www.postgresql.org/download/windows/)
   - Select the version that you want to install (e.g., PostgreSQL 14.0) and click on the download link appropriate for your system (32-bit or 64-bit).

2. **Run the Installer**:

   - Once the installer executable file is downloaded, run it by double-clicking on it.

3. **Installation Wizard**:

   - The PostgreSQL Installation Wizard will open. Click "Next" to proceed.

4. **Select Components**:

   - Choose the components you want to install. The default selections are usually sufficient for most users. Click "Next".

5. **Select Installation Directory**:

   - Choose the directory where you want to install PostgreSQL. The default location is usually fine. Click "Next".

6. **Data Directory**:

   - Choose the data directory where PostgreSQL will store its data. The default location is also fine. Click "Next".

7. **Password**:

   - Set a password for the PostgreSQL superuser (called `postgres` by default). Make sure to remember this password, as you'll need it to access the database later. Click "Next".

8. **Port Configuration**:

   - Choose the port number for PostgreSQL. The default port is 5432. Click "Next".

9. **Locale**:

   - Select the locale that matches your system. The default locale is usually fine. Click "Next".

10. **Ready to Install**:

   - Review the summary of your selections. If everything looks correct, click "Next".

11. **Installation Progress**:

    - The installer will now install PostgreSQL on your system. This may take a few minutes.

12. **Stack Builder** (optional):

    - The Stack Builder is a tool that allows you to download and install additional tools and drivers that work with PostgreSQL. You can skip this for now if you don't need it.

13. **Completing the PostgreSQL Setup**:

    - Once the installation is complete, you'll see a screen indicating the success of the installation. Click "Finish" to close the wizard.

## Connect to Postgres 

To interact with PostgreSQL databases using Python, you'll need to use a library that provides a connection interface. The most commonly used library for this purpose is `psycopg2`. If you haven't already installed it, you can do so using `pip`:

```bash
pip install psycopg2
```

Here are Python programs for the tasks you mentioned:

### 1. Connect to PostgreSQL:

```python
import psycopg2

# Connect to the PostgreSQL database
conn = psycopg2.connect(
    database="your_database_name",
    user="your_username",
    password="your_password",
    host="your_host",
    port="your_port"
)

conn.autocommit = True

# Create a cursor object
cur = conn.cursor()

# Execute SQL queries here

# Close the cursor and connection
cur.close()
conn.close()
```

Replace the placeholders (`your_database_name`, `your_username`, `your_password`, `your_host`, `your_port`) with your actual PostgreSQL database information.

### 2. Create Database:

```python
# Execute SQL to create a database
cur.execute('CREATE DATABASE new_database;')
```

### 3. View Databases:

```python
# Execute SQL to view all databases
cur.execute('SELECT datname FROM pg_database;')
databases = cur.fetchall()
print(databases)
```

### 4. Create Table:

```python
# Execute SQL to create a table
cur.execute('''
    CREATE TABLE my_table (
        id SERIAL PRIMARY KEY,
        name VARCHAR(100),
        age INT
    );
''')
```

### 5. Insert Data:

```python
# Execute SQL to insert data into the table
cur.execute("INSERT INTO my_table (name, age) VALUES (%s, %s);", ('John Doe', 30))
```

### 6. View Tables:

```python
# Execute SQL to view all tables
cur.execute("SELECT table_name FROM information_schema.tables WHERE table_schema='public';")
tables = cur.fetchall()
print(tables)
```

### 7. View Data:

```python
# Execute SQL to view data from a table
cur.execute("SELECT * FROM my_table;")
data = cur.fetchall()
for row in data:
    print(row)
```

Remember to handle exceptions, commit changes, and close connections appropriately in a production environment. Also, be cautious with user inputs to prevent SQL injection attacks.

Make sure to adapt the code to your specific database and table names.
