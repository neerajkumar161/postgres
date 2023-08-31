### Get the Documents using ```SELECT``` operation

```sql
  SELECT * from person; /* To get all records */
  SELECT firstName, lastName from person;
  SELECT id from person WHERE id <= 10; /* Fetch records where id <= 10 > */
```

### Order/Sort the documents using ```ORDER BY``` operation
```sql
  SELECT * from person ORDER BY country ASC; /* Default no need ASC */
  SELECT * from person ORDER BY country DESC; /* Descending */
  SELECT * from person ORDER BY id, email ASC;
```

### Sort and remove duplicates or get unique documents/records using ```DISTINCT```
```sql
  SELECT country from person ORDER BY country;/* Will get the all records country name sort */
  /* Now to remove duplicate elements */
  SELECT DISTINCT country from person ORDER BY country;  /* All Unique countries */
  SELECT DISTINCT country from person ORDER BY country DESC; 
```

### Add conditions using clauses ```WHERE``` and ```AND```, ```OR``` operators
```sql
  SELECT * from person WHERE gender = 'Female';
  SELECT * from person WHERE gender = 'Male' AND country = 'India';  /* Male and country India */
  SELECT * from person WHERE gender = 'Female'
    AND (country = 'India' OR country = 'Poland');
  SELECT * from person WHERE gender = 'Female'
    AND (country = 'India' OR country = 'Poland') 
    AND dateOfBirth <= '1995-01-01';
```

### Using comparison operators
```sql
  SELECT 1 = 1; /* t (true) */
  SELECT 1 = 0; /* f (false) */
  SELECT 1 <= 0;
  SELECT 1 <> 0; /* != Operator */
  SELECT 'NEERAJ' <> 'neeraj'  /* true */
```

### Limiting for Pagination and stuffs using  ```LIMIT```, ```OFFSET``` and ```FETCH```
```sql
  SELECT * from  person LIMIT 10;
  SELECT * from  person FETCH FIRST 5 ROW ONLY;  /* Alternative to LIMIT */
  -- offset basically skip option in MongoDB
  SELECT * from person OFFSET 5 LIMIT 5;  /* Will limit 5, but skip first 5,MongoDB Equivalent [ { $skip: 5 }, { $limit: 5 } ]*/
```