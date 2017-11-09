### General SELECT query structure

```SQL
SELECT DISTINCT column, AGGREGATE_FUNCTION(column or expression),...
FROM table_name
  JOIN another_table
  ON table.column = another_table.column
  WHERE constraint_expression
  GROUP BY column  
  HAVING constraint_expression
  ORDER BY column ASC/DESC
  LIMIT num_limit OFFSET num_offset;
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

#### `COALESCE` (PostgreSQL, MySQL)
- Returns first non-null argument
- ` SELECT COALESCE(NULL, 1, 2) `

#### Even or Odd
- `MOD(col_name, 2) = 0`

#### `COUNT`
- Find difference between total number of fields and unique fields
- `SELECT COUNT(city) - COUNT(DISTINCT city) FROM states;`

#### `LENGTH`
- Returns the length of the specified string (in bytes).
- `SELECT LENGTH(title) AS TitleLength`
