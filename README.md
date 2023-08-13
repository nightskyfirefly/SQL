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
