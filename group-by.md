## SELECT and GROUP BY command.

### Group the Records using ```GROUP BY``` command.
```sql
  SELECT country from person GROUP BY country;
  SELECT DISTINCT country from person; /* Bothe output will be same */
  -- To count the countries by grouping, using COUNT
  SELECT country, COUNT(*) from person GROUP BY country;  -- Note field should be the same in SELECT and GROUP BY command.
  SELECT country, COUNT(*) from person GROUP BY country ORDER BY country ASC;  /* Sorting by country */
  SELECT country, COUNT(*) from person GROUP BY country ORDER BY country DESC;
```

### Filter with ```GROUP BY``` using ```HAVING``` command.
```sql
  SELECT country, COUNT(*) from person GROUP BY country HAVING COUNT(*) > 5 ORDER BY country;  -- Grouping having country country > 5
```

#### Explore [Aggregate Functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)  like COUNT(*) we used

### Creating new table using [Mockaroo](https://www.mockaroo.com/) for aggregate functions, use price range b/w 10K - 100K

```sql
  create table car (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    make VARCHAR(100) NOT NULL,
    model VARCHAR(100) NOT NULL,
    price NUMERIC(19, 2) NOT NULL
  );
  
  \i /pathToFile.sql

```

### Get max and min using ```MAX, MIN``` and ```AVG``` aggregate functions
```sql
  SELECT MIN(price) from car;
  SELECT MAX(price) from car;
  SELECT AVG(price) from car;
  SELECT ROUND(AVG(price)) from car;
  -- max and min price for each car make and model
  SELECT make, model, MIN(price) from car GROUP BY make, model;
  SELECT make, model, MAX(price) from car GROUP BY make, model;
  SELECT make, AVG(price) from car GROUP BY make;
```

### Using ```SUM``` operator to sum values with ```GROUP BY```
```sql
  SELECT SUM(price) from car;
  -- total sum of each car make
  SELECT make, SUM(price) from car GROUP BY make ASC;
```

### Some basic Arithmatic Operators
```sql
  SELECT 10 + 10;
  SELECT 10 + 5;
  SELECT 10 * 5;
  SELECT 10 / 5;
  SELECT 10 ^ 2;
  SELECT FACTORIAL(5);
  SELECT 10 % 2;  -- modulus
  -- x% Discount on each car, AS used for alias name for new column we will generate using the query 
  SELECT id, car, make, price, ROUND(price * .10, 2) AS discount, ROUND(price - price * .10, 2) AS finalPrice from car;
```