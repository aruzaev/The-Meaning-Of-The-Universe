# [[Chapter 3 - Table Creation and Management]]

This chapter focuses on addressing methods for creating tables and modifying existing tables

The following commands will be focused on:

CREATING TABLES
```
CREATE TABLE     - creates a new table in the database and identifies the type of data to be stored
CREATE TABLE ... AS -- creates a table from an existing database, using the AS clause and subqueries
```

MODIFYING TABLE
```
ALTER TABLE ... ADD -- adds a column to a table
ALTER TABLE ... MODIFY -- changes a column size, datatype, or default value
ALTER TABLE ... DROP COLUMN -- deletes one column from a table
ALTER TABLE ... SET UNUSED
or
SET UNUSED COLUMN -- marks a column for deletion at a later time

DROP UNUSED COLUMNS -- completes the deletion of a column previously marked with SET UNUSED
RENAME ... TO -- changes a table name
TRUNCATE TABLE -- deletes all table rows, but the table name and column structure remain
```

DELETING TABLES
```
DROP TABLE -- removes an entire table from the Oracle 12c database
PURGE TABLE -- permanently deletes a table in the recycling bin
```

RECOVERING TABLES
```
FLASHBACK TABLE ... TO BEFORE DROP -- recovers a tabe if the PURGE option hasn't yet been used when the table is dropped
```

## Table Design

Before creating a table using the SQL commands, its important to make the complete entity design for the table name and structure

Here are some requirements:
- the names of tables and columns can be up to 30 characters in length and must begin with a letter, **these limitations are only for a table or column name, NOT the data within a column**
- the names of tables and columns can't contain any blank spaces
- numbers, the underscore system, and the number sign are allowed in table and column names
- each table owned by a user should have a unique table name and the column names of each table should be unique
- you cannot use *distinct* words such as SELECT, DISTINCT, CHAR, and NUMBER for table or column names

Another thing that's important is figuring out what data needs to be in the table

e.x. if we want to make a new table about account managers we would have their
- name
- employment date
- assigned region
- their id (primary key)

Now that we know what will be in the table, we need to design the columns, we do this by:
1. choosing a name for each column
2. determining the type of data that each column stores
3. determining the column's maximum width

Here are the different types of data that can be stored in each column:

- VARCGHAR2(n) - Variable length character data, the `n` represents the column's maximum length. The maximum size is 4000 bytes. There's not default size for this datatype which means that **a minimum value must be specified**.
  
  Example: VARCGHAR2(9) can contain up to nine letters, numbers, or symbols
  
- CHAR(N) - Fixed length character column, the `n` represents the column's length. The default size is 1 and the maximum size is 2000
  
  Example: CHAR(9) can contain nine letters, numbers, or symbols. However, if fewer than nine characters are entered, spaces will be added to the right of the data to force the number of characters to 9

- NUMBER(p, s) - A column used for numeric option. The `p` means **precision** and represents the total amount of digits to the left and right of the decimal position **the amount of digits in total**, up to a maximum of 38 digits
  
  The `s` means **scale** and represents the number of digits to the right of the decimal
  
  Example: NUMBER(7, 2) can store a numeric value up to 99999.99. If the precision or scale isn't specified, the column defaults to a precision of 38 digits
  
  Precision 4, scale 2: 99.99

  Precision 10, scale 0: 9999999999

  Precision 8, scale 3: 99999.999

  Precision 5, scale -3: 99999000


Truncated = permanently deleted
Tables can be modified even if they have existing rows of data
you cant use reserved keywords such as date when making a new table or column
changing the default value of existing columns does not affect existing rows, it only affects future insertions where the value in the column isn't specified

A virtual column is a column that is derived from an expression that involves other columns in the table
The value of the column isn't stored in the database but it gets calculated when queried:
```
CREATE TABLE newtable (cola NUMBER(3), colb NUMBER(3), cole AS (cola+colb));
```

Truncate table removes all data from a table but leaves the table's structure intact
VARCHAR2 requires a length specification

Table names cant have special characters or start with a number
Which of the following is a valid table name? a. 9NEWTABLE b. DATE9 c. NEW”TABLE d. None of the above are valid table names would be b.

The `USER_TAB_COLUMNS` view contains information about the columns of the user's tables, including the default values for the columns.

Rules when modifying existing columns:
- a column must be as wide as the data fields that it already contains
- if a NUMBER column already has data inside of it, you can't decrease the columns `p` or `s` values
- changing the default value of the column doesn't change the values of data already within the table, only new values

Unlike ALTER TABLE with ADD and MODIFY, a DROP COLUMN clause can only reference ***one*** column

When you drop a column from a table, deletion is permanent. It's impossible to undo the damage if you delete the wrong column accidentally

You can't delete **the last remaining column**, it will give you an error message

The primary key column can't be dropped from a table

ALTER TABLE ... SET UNUSED makes the column no longer visible from the table, but it still occupies space and exists in the database

ALTER TABLE ... DROP COLUMN directly and  permanently removes the column from memory and the database

at least one column both ways

2landing pages for grotrop and an ai based product

rfp proposal phase
engineering constructions
rfp to response
gen ai project
reads rfp and analyzes rfp
autodrafting responses to rfps
vertical product
robust product in the 

very minimal aand contemporary
saas
hello
what we do
who is our customers 
about company about team

about team on different page
contact page

do some research 
first page has to immediately say what we stand for and what our solution is

AEC

RFP to Response

Automating

Gen AI

pick up some ai templates and make a rough draft for next week
very sleek modern 
put standard message

benefit: cut down on manpower, cut on manual work
bidding - bid for more projects
build

the system should be able to r

read rfp, read history, come project project