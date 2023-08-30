### [Data Types](https://www.postgresql.org/docs/10/datatype.html) in Postgres 

### Create table in Postgres

```sql
  CREATE TABLE table_name(
    Column_name + data_type + constraints if any
  )
```

### Example
```sql
  CREATE TABLE person(
    id int,
    firstName VARCHAR(40),
    lastName VARCHAR(40),
    gender VARCHAR(6),
    dateOfBirth DATE
  );

  \d /* Describe the all relations */
  \d person  /* Desribe table */
```

### Before creating the table you need to grant permissions to the user.
```sql
  GRANT CONNECT ON DATABASE testdatabase TO neerajkumar; /* Connect permission */
  GRANT pg_read_all_data TO neerajkumar;  /* Read Permission */
  GRANT pg_write_all_data TO neerajkumar; /* Write permission */
  GRANT USAGE ON SCHEMA public TO neerajkumar; /* Schema usage permission */
  GRANT postgres TO neerajkumar; /* You can grant specfic role from other user as well */
```


### Creating Table with Constaints
```sql
  CREATE TABLE person(
    id BIGSERIAL NOT NULL PRIMARY KEY,  /* BIGSERIAL will increment value itself */
    firstName VARCHAR(40) NOT NULL,
    lastName VARCHAR(40) NOT NULL,
    gender VARCHAR(6) NOT NULL,
    dateOfBirth DATE NOT NULL
  );

  /* Alter table, if you want to add anther column in schema */
  ALTER TABLE person
    ADD COLUMN email VARCHAR(30);
```

### Insert values in the table
```sql
  INSERT INTO person(firstName, lastName, gender, dateOfBirth) VALUES ('Neeraj', 'Kumar', 'Male', DATE '21-01-1992');
  INSERT INTO person(firstName, lastName, gender, dateOfBirth) VALUES ('Rohit', 'Kumar', 'Male', DATE '13-11-1996');
  INSERT INTO person(firstName, lastName, gender, dateOfBirth, email) VALUES ('Amy', 'Smith', 'Female', DATE '23-04-1995', 'amy.smith@gmail.com');
```

### Insert 1000+ rows using [Mockaroo](https://www.mockaroo.com/)
```sql
  \i /pathToFile.sql
```

### Create Table [READ HERE](./create-table.md)