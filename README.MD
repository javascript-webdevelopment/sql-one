# SQL One

In this lecture we introduce SQL, specfically the PostgreSQL flavor of SQL.

PostgreSQL is the language that we will be using to interact with our database to store, retrieve, delete, and update data.

## Database

A database is an organized way that we can create and store data for our applications. 

We will be working with a `relational` database. A relational data base is built upon the table layout. It's easy to think about this like Microsoft Excel, how there are columns and rows working together to organize data.

An example of a relational databse table looks like this

![Table](images/table.png)

Tables in a relational database all have a `schema`.

## Schema

The `schema` is the bluepring for how our tableis structured. This is what sets the guidelines for how the data is stored inside of our database.

A schema for our table above would look similar to this

```sql
CREATE TABLE racers (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER,
    country TEXT
)
```

Above, we are determining exactly what datatypes are allowed to be inserted into each coloumn for the row that is being added to our racers table in our database.

## DataTypes

When setting up our schema we will determine what `data type` is allowed in our columns. There are many types out there, but we will cover the main ones.

### Empty Values

`Null` - This data type means an empty value.

### Numeric Values

`Integer` - This data type will define a round number.

`Decimal` - This data type can have unlimited decimal values.

`Float` - This data type can have values up to 15 decimal places.

`Serial` - This data type is an incrementing integer, usally used with primary keys to establish uniqueness.

### Character Values

`Text` - This data type declares unlimited characters in a string.

`Varchar(n)` - This data type will allow you to determine how many characters are allowed.

## Statements

SQL statements are queries that we make to our database.

A few things to note about SQL Statements:

1. We use a semicolon to delcare the end of a statement.

2. We can not have a trailing comma on our scripts. 

3. We need to use single quotes, not double.

4. It's common to use all caps, but it's not needed. It's best to stick with one way and be consistant and not use lowercase and capital characters.

### Insert Statement

We can use `insert statements` to add data into our tables. The syntax for an insert statement looks like the following.

```sql
INSERT INTO racers
(name, age, country)
VALUES
('Tayte', 22, 'US')
```

Above, we are adding myself into the database. We first delcare a insert statement with the `INSERT INTO` keyword followed by the name of the table we are inserting data into. Then in parenthesis, we select the columns to add to. We then use the `VALUES` keyword followed by another pair of parenthesis to include the data to insert into the columns.

> Note: It's import that the data lines up with the column we want to insert that data into

### Select Statement

`Select` statements are used to query our database for information. The structure for a `select` statement looks like the following.

```sql
SELECT *
FROM racers
```

Above, we delcare it's a select statement using the `SELECT` keyword. It is followed by the column name that we want to selectv data from. In this case, we used an asterik to say 'all' the data from every column. Then we declare what table to select from using the `FROM` keyword.

#### WHERE

We can use a `where clause` to add a filter to our select statements. The different types of ways to filter data with a where clause.

##### Comparison Operators

`>` - Greater than.

`<` - Less than.

`>=` - Greater than or equal to.

`<=` - Less than or equal to.

`!=` - Does not equate.

##### Logical Operators

`AND` - Check for multiple conditions to be true.

`OR` - Check for only one of multiple conditions to be true.

##### Null and Not Null

`IS NULL` - Checks for a value to be null.

`IS NOT NULL` - Checks for a value NOT to be null.

##### IN Condition

`IN` - This is used as shorthand syntax to act as multiple `OR` conditions.

```sql
SELECT *
FROM racers
WHERE ame IN ('Tayte', 'Samual', 'Kevin');
```

If we didn't use the `IN` key word, our statement would look like this

```sql
SELECT *
FROM racers
WHERE name = 'Tayte'
OR name = 'Samual'
OR name = 'Kevin';
```

##### BETWEEN Condition

`BETWEEN` - This is used to retrieve values in between a range.

```sql
SELECT *
FROM racers
WHERE id BETWEEN 1 AND 3;
```

#### LIMIT

The `LIMIT` clause will allow you to return a certain amount of rows from a select statement.

```sql
SELECT *
FROM racers
LIMIT 2
```

This would return the first two rows of data from the racers table.

