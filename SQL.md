## SELECT query structure

```SQL
SELECT DISTINCT 
  column, AGGREGATE_FUNCTION(column or expression),...
FROM 
  table_name
JOIN 
  another_table
ON 
  table.column = another_table.column
WHERE 
  constraint_expression
GROUP BY 
  column  
HAVING 
  constraint_expression
ORDER BY 
  column ASC/DESC
LIMIT 
  num_limit OFFSET num_offset;
```
 
#### Actual Order Performed
`FROM`, `JOIN`, `ON`, `WHERE`, `GROUP BY`, `HAVING`, `SELECT`, `ORDER BY`, `LIMIT`

#### Aggregates
- Applies to groups. If no groups, then entire table.
- Not allowed in `WHERE`
- `COUNT(col)` - Number of rows in col with **non-null** values
- `MIN`
- `MAX`
- `AVG`
- `SUM`

#### String Comparision
- `LIKE` - simple pattern matching
   - `%` - wildcard that matches any number of characters, even zero characters
   - `_` - matches exactly one character
   - MySQL lets you compare numeric expressions
     - `SELECT 10 LIKE '1%';`
- `NOT LIKE`
- `STRCMP(expr1,expr2)`
   - returns `0` if strings are the same
   - returns `-1` if the first argument is smaller than the second according to the current sort order
   - returns `1` otherwise
- `REGEX`  - pattern matching with regular expressions (`RLIKE` is the same thing)
  - `WHERE city REGEXP '^[aeiou]';` (where city name starts with a vowel)
- `NOT REGEX`

#### `COALESCE` (PostgreSQL, MySQL)
- Returns first non-null argument
- `SELECT COALESCE(NULL, 1, 2);`

#### Even or Odd
- `MOD(col_name, 2) = 0`

#### `COUNT`
- Find difference between total number of fields and unique fields
- `SELECT COUNT(city) - COUNT(DISTINCT city) FROM states;`

#### `LENGTH`
- Returns the length of the specified string (in bytes).
- `SELECT LENGTH(title) AS TitleLength;`

#### `RIGHT`
- Extract substring from right
- `SELECT RIGHT(name, 3)`
- `ORDER BY RIGHT(name, 3)`

## Update
```sql
UPDATE
  table_name
SET
  column1 = val1,
  column2 = val2
WHERE
  conditions;
```

## Insert
```sql
INSERT INTO
  table_name (column_names)
VALUES
  (values);
```

## Delete
```sql
DELETE FROM
  table_name
WHERE
  conditions
```

