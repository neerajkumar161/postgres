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
  SELECT * from person OFFSET 5 LIMIT 5;  /* Will limit 5, but skip first 5,*/
```
```js
  // MongoDB Equivalent 
  [ { $skip: 5 }, { $limit: 5 } ]
```

### ```IN``` operator instead of OR on same column or field again and again
```sql
  SELECT * from person WHERE country = 'India' OR country = 'France' OR country = 'Poland';
  -- Instead we can use IN operator to acheive same result
  SELECT * from person WHERE country IN ('India', 'France', 'Poland');  /* 
```
```js
  // MongoDB Equivalent
  [ { $match: { country: { $in: ['India', 'France', 'Poland'] } } } ]
```

### Using ```BETWEEN``` operator
```sql
  SELECT * FROM person where dateofbirth BETWEEN DATE '1996-01-01' AND '1998-01-01'
```
```js
  // MongoDB Equivalent
  [ { $match: { dateofbirth: { $gte: new Date('1996-01-01'), $lte: new Date('1998-01-01') } } } ]
```

### Using ```LIKE``` and ```ILIKE``` operators to match the substring
```sql
  SELECT * FROM person WHERE email LIKE '%.com';
  SELECT * FROM person WHERE email LIKE '%@google.com';  /* any chars before @google.com */
  SELECT * FROM person WHERE email LIKE '%@google%';  /* any chars before and after @google */
  -- _ use for single character
  SELECT * FROM person WHERE email LIKE '_____@%.com'; /* Five chars before @%.com */
  SELECT * FROm person WHERE country LIKE 'P%'; /* Case Sensitive */
  -- ILIKE is case insentive
  SELECT * FROm person WHERE country ILIKE 'p%';
```

```js
  // MongoDB Equivalent, it uses regex heavily to match the expression
  [ { $match: { email: { $regex: /\.com$/ } } } ]
  [ { $match: { email: { $regex: /\@google.com$/ } } } ]
  [ { $match: { email: { $regex: /google.com/ } } } ]
  [ { $match: { email: { $regex: /^.{5}@.*\.com$/ } } } ]
  [ { $match: { email: { $regex: /^P/ } } } ]
  [ { $match: { email: { $regex: /^P/i } } } ]  /* Case Insensitive */
```