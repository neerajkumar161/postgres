### Handling ```null``` values in Postgres using ```COALESCE``` function
```sql
  SELECT COALESCE(null);  -- null
  SELECT COALESCE(null, 1);  -- 1, will pick the next parameter which is not null
  SELECT COALESCE(null, null, 1);  -- 1, will pick the next parameter which is not null
  SELECT COALESCE(null, 1, 10);  -- 1, 
  -- handle the empty emails in the table
  SELECT id,firstname, lastname, gender, COALESCE(email, 'NULL') from person;
  SELECT id,firstname, lastname, gender, COALESCE(email, 'NULL') from person;
  SELECT id,firstname, lastname, gender, COALESCE(email, 'NULL') AS email from person;  
```
### Handling Division by zero exception ```NULLIF```
```sql
  /* NullIf always returns first paramter if both are different */
  SELECT 10 / 0;  -- throws error
  SELECT NULLIF(10, 10); -- will be null
  SELECT NULLIF(19, 10);  -- 19
  SELECT 10 / NULLIF(12, 90);  -- not throws error, but wait what if 
  SELECT 10 / NULLIF(0, 10)  -- YES, It will throw error
  SELECT COALESCE(10 / NULLIF(0, 0), 0)  -- Displays default value
```