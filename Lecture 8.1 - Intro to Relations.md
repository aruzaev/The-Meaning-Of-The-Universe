# [[Lecture 8.1 - Intro to Relations]]

Relational databases stem from an abstract mathematical concept called relations

They have the same properties and behaviours as a table in a database

This is about the transformation of a conceptual data model (ERD) to a objects in a physical database

An entity is not a table and an attribute is not a column

---

**Relational database** - A collection of objects, the operations, and their data

Each relational database has a row and a column

![[Pasted image 20240319135117.png]]

If we wanted to find a certain piece of info in the table, instead of looking at it manually we can use a query language such as SQL

![[Pasted image 20240319135328.png]]

**Primary key** - a column or set of columns that uniquely identifies each row in a table (contains no null values)

![[Pasted image 20240319135624.png]]
Bank number and account number aren't unique separately but together they make a primary key

Each table should have a primary key, even though you can make one without it it is not recommended

**Candidate key** - A column or combination of columns that could serve as the table's primary key

To be a good candidate for a primary key, the values have to be not null and unique

**Unique key** - also called alternate keys; a set of columns that are unique which creates another way to look up a record because they're unique

**Foreign key** - A column or set of columns that refers to the primary key; either in the same table or another table

![[Pasted image 20240319140643.png]]

If a primary key is composed of one or more FKs, the FK value cannot be NULL

**Column integrity** - A column must have values that are only consistent with the data that is defined in the column