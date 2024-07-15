# [[Chapter 9 - Joining Data From Multiple Tables]]

In order to combine data across multiple tables, you need to use joins and **join conditions**


***IMPORTANT: NEVER USE NATURAL JOIN***

There are multiple kinds of joins that can be used:

### Cartesian Join 

Replicates each row from the first table with every row from the second table

Creates a join between two or more tables with every possible record combination

Can be created using **two methods**:
1. not including a joining condition inside of the `WHERE` clause
2. Using the `JOIN` method with the `CROSS JOIN` keywords

### Equality Join (aka equijoin, inner join, or simple join)

Creates a join using commonly named and defined columns (finding common columns and connection using that)

Can be created using **two methods**:
1. Using the `WHERE` clause
2. Using the `JOIN` method with the `NATURAL JOIN (never use), JOIN ... ON, or JOIN ... USING` keywords

### Non-equality Join

Joins tables that have no equivalent or common rows that can be joined

Example: matching values in one column of a table with a range of values in another table

Can be created using **two methods**:
1. Using the `WHERE` clause
2. Using the `JOIN` method with the `JOIN ... ON` keyword

### Self-join

Joins a table to itself. Used for recursive table

Can be created using **two methods**:
1. Using the `WHERE` clause
2. Using the `JOIN` method with the `JOIN ... ON` keyword

### Outer Join

Includes records of a table in the output when there's no matching record in the other table

## Cartesian Join

Each record in the first table is matched with each record in the second table

If you have three records in one table and four records in anohter, the first record in the first table will be matched with each of the four records, and so on for the second and third one

![[Pasted image 20240618112120.png]]

#### Traditional Method

Excluding `JOIN` clause

```
SELECT isbn, title, location, '   ' Count
FROM books, warehouses -- this is where we join
ORDER BY location, title;
 ```

####  Using Join Method

```
SELECT isbn, title, location, '   ' Count
FROM books CROSS JOIN warehouses -- this is where we join
ORDER BY location, title;
```
Cartesian or CROSS JOIN combines each row from one table with each row from another table

## Equality Join

When two or more tables have equivalent data in a common column

A **common column** is a column that has the same data in two or more tables

Reviewing the FK constraints can help you identify the common columns between the tables

**it isn't a requirement for the columns to have the same name, they just need to have the same data**

#### Traditional Method

Using the WHERE clause to instruct the database how to join the tables without it being a cartesian join

The WHERE clause can perform two different activities:
- joining the tables
- providing conditions to limit the rows that are affected

```
SELECT title, name
FROM books, publisher
WHERE books.pubid = publisher.pubid;
```

The HWERE tells which columns from which tables are common

A **column qualifier** indicates the table that is being referenced, it is the word before the dot and removes any ambiguity

Search conditions can also be added to the where

Use aliases:
- they are assigned in the FROM clause
- the improve processing efficiency (system no longer needs to identify which column a table is in), coding is also simplified
- when an alias is used, it MUST be used every time the table is referenced in that statement

#### JOIN Method

There are three different approaches

- Natural Join - creates a join automatically if the columns have matching names
- USING - allows you to create a join based on a column that has the same name and definition in both tables
- ON - when the tables to be joined dont have a commonly named and defined column

```
SELECT title, pubid, name
FROM published NATURAL JOIN books;
```

You aren't required to specify the common columns because it checks automatically and assumes the tables have at least one column in common with the same name and datatype

Never use this

```
SELECT b.title, pubid, p.name
FROM publisher p JOIN books b
	USING (pubid);
```

This requires both tables to have the same column name and datatype

If they don't then we use ON

```
SELECT b.title, b.pubid, p.name
FROM publisher2 p JOIN books b
	ON p.id = b.pubid;
```

The main difference between the two are this:

The USING clause can only be used if the tables being joined have a common column with the same name. This isn't needed in the ON clause

A condition is specified in the ON clause, this isn't allowed in the USING clause as it can only contain the name of the common column

## Non-Equality Joins

This type of join is used when there is no equivalent rows in the tables to be joined; can't use an equal sign

Similar to the above join, non equality joins can be performed with the WHERE clause and the JOIN ON

A non-equality join enables you to store a range's minimum in one column and the maximum in another column

#### Traditional Method

Since BOOKS and PROMOTION doessnt have an equivalent column you can do this

```
SELECT b.title, p.gift
FROM books b, promotion p
WHERE b.retail BETWEEN p.minretail AND p.maxretail
```

#### Join Method

```
SELECT b.title, p.gift
FROM books b JOIN promotion p
	ON b.retail BETWEEN p.minretail AND p.maxretail;
```

## Self-Joins

Data in one column of the table can have a relationship with another column in the same table

The main goal is to make it appear that we're joining two different tables, so the method doesn't matter
#### Traditional Method

```
SELECT r.firstname, r.lastname, c.lastname "Referred"
FROM customers c, customers r
WHERE c.referred = r.customer#;
```

#### Join Method

```
SELECT r.firstname, r.lastname, c.lastname "Referred"
FROM customers c JOIN customers r
	ON c.referred = r.customer#;
```

## Outer Joins

All of the other joins can be referred to as INNER joins because the records are listed only if a match is found in each table

If you want to include records in the join results that exist in one table but don''t have a matching row in the other table, you use an **outer join**

The database joins the mismatched record to a NULL record in the other table

#### Traditional Method

To create records that don't have a matching row, we use an **outer join operator** (+)

It's placed in the WHERE clause after the column name thats missing the matching row and it tells the database to create a NULL row in that table in order to join with the row in the other table

```
SELECT c.lastname, c.firstname, o.order#
	FROM customers c, orders o
	WHERE c.customer# = o.customer#(+)
	ORDER BY c.lastname, c.firstname;
```

The orders table is the "deficient table" because it has missing data "customers that haven't placed orders"

The operator is places on the side of the deficient table

Some limitations
- The operator can only be used for one table in the joining condition. You can't create NULL rows in both tables are the same time
- A condition that has the outer join operator can't use the IN or OR operators

#### Join Method

With this method, you can specify which table should be applied by using a left, right, or full outer join

Left and right outer joins specify which table the outer join should be applied to, or the deficient table, based on the positions of the table

A full outer join keeps all rows from both tables in the results, no matter which table is deficient (it performs a combination of left and right outer joins)

With a left outer join, if the table listed on the left side of the join has an unmatched recored, its matched with a NULL record

```
SELECT c.lastname, c.firstname, o.order#
FROM customerss c LEFT OUTER JOIN orders o
	USING (customer#)
ORDER BY c.lastname, c.firstname;
```

## Set Operators

Set operators are used to combine the results of two or more SELECT statements

UNION - returns the results of both queries and removes duplicates
UNION ALL - returns the results of both queries but includes duplicates
INTERSECT - returns only the rows included in BOTH the results of the queries
MINUS - subtracts the second query's results if they are also returned in the results of the first query

Some guidelines for set operations:
- all columns are included to perform thee set operation
- each query must contain the same number of columns, which are compared posititionally
- columnn naames can be different in the queries
