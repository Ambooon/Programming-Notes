
# Foreign Key

```python
import sqlite3

conn = sqlite3.connect('hospital.db')
query = (""" CREATE TALBE IF NOT EXISTS doctor (
		name TEXT NOT NULL,
		phone_number CHAR(20) NOT NULL,
		type TEXT);		 
	""")
conn.execute(query)

query = (""" CREATE TALBE IF NOT EXISTS patient (
		name TEXT NOT NULL,
		email TEXT NOT NULL,
		phone_number CHAR(20) NOT NULL,
		problem TEXT
		doctor_id INTEGER NOT NULL,
		FOREIGN KEY(doctor_id) REFERENCES doctor(rowid));		 
	""")
conn.execute(query)
conn.close()
```


# PRAGMA
Foreign key is not available in sqlite3 by default. So we need to tell it to activate.
In creating a table you don't need to activate it. But it is required if you want to do something in the table like inserting, updating.
```python
conn = sqlite3.connect('hospital.db')

# Activate the foreign keys 
conn.execute("PRAGMA foreign_keys = ON")

cursor = conn.execute("SELECT * FROM patient WHERE doctor_id=2")
```