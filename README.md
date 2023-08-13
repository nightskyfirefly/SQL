# SQL Terminology and Examples

## Table of Contents
- [Foreign Key](#foreign-key)
- [Primer](#primer)
- [Truncate](#truncate)
- [Union](#union)
- [Union All](#union-all)
- [Inner Join](#inner-join)
- [Left Outer Join](#left-outer-join)
- [Right Outer Join](#right-outer-join)
- [Subquery](#subquery)

---

## Foreign Key

A foreign key establishes a relationship between two tables by linking a column in one table to the primary key column in another table.

### Example
```sql
-- Creating a foreign key relationship
ALTER TABLE coffee_data
ADD CONSTRAINT fk_user_id
FOREIGN KEY (user_id) REFERENCES user_info(user_id);
```

## Primer

A primer is a short SQL code snippet that introduces a specific concept or query.

### Example
```sql
-- Primer for Subquery to Calculate Average Anxiety
SELECT
  AVG(anxiety_level) AS avg_anxiety
FROM
  coffee_data
WHERE
  caffeine_mg > (SELECT AVG(caffeine_mg)
                FROM coffee_data);
```

## Truncate

The TRUNCATE command quickly removes all rows from a table.

### Example
```sql
-- Truncate the coffee_data table
TRUNCATE TABLE coffee_data;
```

## Union

The UNION operator combines result sets of two or more queries into a single set, removing duplicates.

### Example
```sql
-- Retrieve distinct genders and coffee consumption data
SELECT
  gender, cups_of_coffee
FROM
  coffee_data
WHERE
  anxiety_level > 3
UNION
SELECT
  gender, cups_of_coffee
FROM
  coffee_data
WHERE
  caffeine_mg > 200;
```

## Union All

The UNION ALL operator combines result sets, including duplicates.

### Example
```sql
-- Retrieve genders and coffee consumption data, including duplicates
SELECT
  gender, cups_of_coffee
FROM
  coffee_data
WHERE
  anxiety_level > 3
UNION ALL
SELECT
  gender, cups_of_coffee
FROM
  coffee_data
WHERE
  caffeine_mg > 200;
```

## Inner Join

An INNER JOIN retrieves rows with matching values in both tables.

### Example
```sql
-- Retrieve correlated data using INNER JOIN
SELECT
  a.gender, a.anxiety_level, b.cups_of_coffee
FROM
  coffee_data a
INNER JOIN
  user_info b ON a.user_id = b.user_id;
```

## Left Outer Join

A LEFT OUTER JOIN returns all rows from the left table and matching rows from the right table.

### Example
```sql
-- Retrieve all genders and associated data using LEFT OUTER JOIN
SELECT
  a.gender, a.anxiety_level, b.cups_of_coffee
FROM
  coffee_data a
LEFT JOIN
  user_info b ON a.user_id = b.user_id;
```

## Right Outer Join

A RIGHT OUTER JOIN returns all rows from the right table and matching rows from the left table.

### Example
```sql
-- Retrieve data from user_info with associated coffee consumption data
SELECT
  a.gender, a.anxiety_level, b.cups_of_coffee
FROM
  coffee_data a
RIGHT JOIN
  user_info b ON a.user_id = b.user_id;
```

## Subquery

A subquery is a query nested within another query.

### Example
```sql
-- Retrieve genders and coffee consumption data based on subquery result
SELECT
  gender, cups_of_coffee
FROM
  coffee_data
WHERE
  caffeine_mg > (SELECT AVG(caffeine_mg)
                FROM coffee_data);
```
