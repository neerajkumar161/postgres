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