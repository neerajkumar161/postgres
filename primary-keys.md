### Primary keys use to uniquely identify the record in a table

### Creating Table with Primary Key Constaints
```sql
  CREATE TABLE person(
    id BIGSERIAL NOT NULL PRIMARY KEY,  /* BIGSERIAL will increment value itself */
    firstName VARCHAR(40) NOT NULL,
    lastName VARCHAR(40) NOT NULL,
    gender VARCHAR(6) NOT NULL,
    dateOfBirth DATE NOT NULL
  );
```

### Remove Primary key constraint from table
#### By doing so, we can add as many records with same id.
```sql
  \d person;
  ALTER TABLE person DROP CONSTRAINT person_pkey;
```

### Adding Primary key constaint in a table
```sql
  ALTER TABLE person ADD PRIMARY KEY (id); -- PRIMARY KEY is constraint
  -- it will not work, if there are any duplicated primary key value in a table, to fix this we've to remove duplicate values from table
```

### Unique Constraint, unique value for a give column
```sql
  -- Suppose we want to add unique constraint on email, so new user cannot use the same email twice in a database
  SELECT email, COUNT(*) from person GROUP BY email;
  SELECT email, COUNT(*) from person GROUP BY email HAVING COUNT(*) > 1;  -- get email count which are not unique.
  -- Add email constraint
  ALTER TABLE person ADD CONSTRAINT unique_email_address UNIQUE (email);
  -- Now if we try to add record with existed email, will throws error
  ALTER TABLE person DROP CONSTRAINT unique_email_address;
```

### Another way to add a Unique Constraint
```sql
  ALTER TABLE person add UNIQUE(email); -- only difference, Postgres will create contraint name by itself
```

### ```Check``` constraint, suppose you want to add constraint on a column for specific values, for eg. gender i.e Male and Female
```sql
  -- list distinct genders
  SELECT DISTINCT gender FROM person;
  ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK (gender IN ('Genderqueer','Bigender','Genderfluid','Male','Non-binary','Polygender','Female','Agender'));
  ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK (gender IN ('Male','Female'));
  ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK (gender = 'Male' OR gender = 'Female');
  -- drop constraint
  ALTER TABLE person DROP CONSTRAINT gender_constraint;
```