
# Initial Setup
```python
import sqlite3

# Create or connect into the database.
conn = sqlite3.connect('database.db')

# Create a cursor.
c = conn.cursor()

# Execute a command
c.execute("""
		  CREATE TABLE IF NOT EXISTS customers (
			  first_name text,
			  last_name text
			  age integer
		  )
		  """)

# Commit the command into the database
conn.commit()

# Close the connection to the database
conn.close()
```

**Cursor** - cursors in sqlite3 python are objects that act as a pointer to the results of a query. They enable you to fetch, add, modify or delete data from a database. The cursor can also be used to traverse through the rows of a query result.

**SQLite3 Datatypes:**
- null
- integer
- real - decimal number
- text
- blob - images, mp3


# Insert record
```python
import sqlite3

conn = sqlite3.connect('database.db')
c = conn.cursor()

# Execute commands here
c.execute("INSERT INTO customers VALUES ('Francis', 'Angoring', 21)")
#c.execute("INSERT INTO customers (first_name, last_name, age) VALUES ('Francis', 'Angoring', 21)")

conn.commit()
conn.close()
```


# Insert many record

**Placeholder** - this is done by using (?, ?, ?). This acts as a placeholder for the 2nd argument.
```python
many_customers = [
				  ('David', 'Calumba', 22),
				  ('Jezter', 'Landicho', 24),
				  ('Danica', 'Estrada', 22),
]
c.executemany("INSERT INTO customers VALUES (?,?,?)", many_customers)

#c.executemany("INSERT INTO customers VALUES (?,?,?)", ($first, $second, $age))
```


# Fetch data

Fetch returns a tuple
```python
c.execute("SELECT * FROM customers")

# Fetch the first item
c.fetchone()

# Fetch a number of item
c.fetchmany(3)

# Fetch all item
c.fetchall()
```


# Primary Key

The column name for primary key is **rowid**
```python
c.execute("SELECT rowid, * FROM customers")
```


# WHERE clause
```python
c.execute("SELECT * FROM customers WHERE first_name = 'Francis'")
```

You can use:
- logical operators (<, >, =, <=, >=)
```python
c.execute("SELECT * FROM customers WHERE age > 18")
```
- LIKE operator.
```python
c.execute("SELECT * FROM customers WHERE first_name LIKE 'Da%')
# The return item for this are 
# David, Danica
```


# Update item
```python
c.execute("""
		  UPDATE customers SET age = 22 
		  WHERE rowid = 1
		  """)
```


# Delete item
```python
c.execute("DELETE FROM customers WHERE first_name = 'Danica' ")
```


# Order By
```python
# Two options ASC or DESC
c.execute("SELECT * FROM customers ORDER BY first_name ASC")
```


# AND / OR
```python
c.execute("SELECT * FROM customers WHERE first_name LIKE 'Da%' AND age > 18")
```


# LIMIT
```python
c.execute("SELECT * FROM customers LIMIT 2")
```


# DROP TABLE
```python
c.execute("DROP TABLE customers")
```