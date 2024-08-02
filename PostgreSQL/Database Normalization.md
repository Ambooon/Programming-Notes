# 1NF (First Normal Form)
- Row number must not convey meaning.
- No mixing data types in same column.
- Must have a primary key.
- No repeating group of data in single row.

# 2NF
Each non-key attribute in the table must be dependent on the entire primary key.

BAD! - Column does not belong in this table
![[Pasted image 20240719154218.png]] 

GOOD!
![[Pasted image 20240719154248.png]]

# 3NF
Each non-key attribute in the table must depend on the key, the whole key, and nothing but the key.

BAD! 
![[Pasted image 20240719154639.png]]

GOOD!
![[Pasted image 20240719154618.png]]

# 4NF
The only kinds of multivalued dependency allowed in a table are multivalued dependencies on the key.

BAD!
![[Pasted image 20240719154954.png]]

GOOD!
![[Pasted image 20240719155015.png]]

# 5NF
It must not be possible to describe a table as being a logical result of joining some other tables together.

BAD!
![[Pasted image 20240719155325.png]]

GOOD!
![[Pasted image 20240719155258.png]]