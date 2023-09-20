### Dates in Postgres
```sql
  SELECT NOW();  --2023-09-20 12:28:40.788548+05:30
  SELECT NOW()::DATE; -- 2023-09-20
  SELECT NOW()::TIME; -- 12:28:40.788548
```
### Adding and Substracting Dates
```sql
  SELECT NOW() - INTERVAL '1 YEAR';
  SELECT NOW() - INTERVAL '10 YEARS';
  SELECT NOW() - INTERVAL '10 DAYS';
  SELECT NOW() + INTERVAL '1 YEAR';
  SELECT NOW() + INTERVAL '10 YEARS';
  SELECT NOW()::DATE + INTERVAL '10 YEARS'; -- 2033-09-20 00:00:00
  -- or
  SELECT (NOW()+ INTERVAL '10 YEARS')::DATE;  -- 2033-09-20
```

### Extract specific fields from Date
```sql
  SELECT EXTRACT(YEAR FROM NOW());
  SELECT EXTRACT(MONTH FROM NOW());
  SELECT EXTRACT(DAY FROM NOW());
  SELECT EXTRACT(DOW FROM NOW()); -- Date of the Week
  SELECT EXTRACT(CENTURY FROM NOW());
```

### Calculate the age using ```AGE``` function
```sql
  SELECT firstname, lastname, email, gender, dateofbirth, AGE(NOW(), dateofbirth) from person;
  SELECT firstname, lastname, email, gender, dateofbirth, AGE(NOW()::DATE, dateofbirth) from person;
```