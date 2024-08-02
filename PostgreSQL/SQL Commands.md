
# Create Table
```SQL
CREATE TABLE person (
id BIGSERIAL NOT NULL PRIMARY KEY,
name VARCHAR(50) NOT NULL,
sex VARCHAR(6) NOT NULL,
email VARCHAR(100) UNIQUE,
CONSTRAINT sex CHECK (sex = "Male" or sex = "Female")
);
```

## With foreign keys
```sql
CREATE TABLE car (
id BIGSERIAL NOT NULL PRIMARY KEY,
brand VARCHAR(50) NOT NULL,
price BIGINT NOT NULL,
);

CREATE TABLE person (
id BIGSERIAL NOT NULL PRIMARY KEY,
name VARCHAR(50) NOT NULL,
sex VARCHAR(6) NOT NULL,
email VARCHAR(100) UNIQUE,
CONSTRAINT sex CHECK (sex = "Male" or sex = "Female"),
car_id BIGINT REFERENCES car (id),
UNIQUE car_id
);
```

BIGSERIAL is an auto incrementing unsigned int.
## Constraints
- NOT NULL
- PRIMARY KEY
- UNIQUE
- CHECK

# Insert Values
```SQL
INSERT INTO person(name, sex, email) VALUES ('Francis', 'Male', 'franci@email.com');
```

# Delete values
```sql
DELETE FROM person WHERE id=1;
```

# Update values
```sql
UPDATE person SET email = 'test@email.com' WHERE id = 2;
```

# Other commands
- order by
- select distinct
- where clause and AND
- comparison operators
- limit, offset & fetch
- IN
- Between
- Like and iLike
- Group by
- group by having
- min, max, average
- sum
- alias
- coalesce - value if the value is null
- nullif
- timestamps and dates
- age function
- on conflict do nothing
- on conflict do update

# Joins
## Inner Join
```sql
SELECT * FROM person JOIN car ON person.car_id == car.id;
```

## Left Join
```sql
SELECT * FROM person LEFT JOIN car ON person.car_id == car.id;
```

# UUID

First install the extension
```sql
CREATE EXTENSTION IF NOT EXISTS "uuid-ossp";
```

```sql
CREATE TABLE car (
id UUID NOT NULL PRIMARY KEY,
brand VARCHAR(50) NOT NULL,
price BIGINT NOT NULL,
);

CREATE TABLE person (
id UUID NOT NULL PRIMARY KEY,
name VARCHAR(50) NOT NULL,
sex VARCHAR(6) NOT NULL,
email VARCHAR(100) UNIQUE,
CONSTRAINT sex CHECK (sex = "Male" or sex = "Female"),
car_id UUID REFERENCES car (id),
UNIQUE car_id
);

INSERT INTO car (id, brand, price) VALUES (uuid_generate_v4(), 'Ford', 'Ranger');
```