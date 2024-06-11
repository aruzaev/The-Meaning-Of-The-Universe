# [[Chapter 4 - Constraints]]

## Introduction
---

**Constraints** are rules used to enforce business rules, practices, and policies to ensure the accuracy and integrity of data

They help by not allowing data to be added to tables if they don't meet a certain set of rules

Here are all the main five constraints for Oracle:

```
PRIMARY KEY -- determines which columns uniquely identifies each record. The primary key can't be NULL, and the data values must be unique

FOREIGN KEY -- In a one-to-many or parent-child relationship, this constraint is added to the MANY table (think of foreign minister in the UN with many other people). 

The contraint ensures that if a value is entered in a specific column, it must already exist in the "one" (home country) table, or the record isn't added (he's just a random person)

UNIQUE -- Ensures that all of the data values stored in a specifiec column are unique. The difference between UNIQUE and PRIMARY KEY is that UNIQUE allows for NULL values.

CHECK -- Ensures that a specific condition is true before the data can be added to the table.

e.x. an order's ship date can't be earlier than its order date

NOT NULL -- Checks that a specified column can't contain a NULL value. This constraint can only be set with the column level approach
```


When making a table, there are two ways to create a constraint:

1. column level
2. table level

Creating a constraint at the table level means that the definition of the constraint is separate from the column definition 

The only **difference** between the two methods is that the constraint code is in different parts of the `CREATE TABLE` statement

### Column level

```
columnname [CONSTRAINT constraintname] constrainttype;
```

`NOT NULL` can only be created at the **column level**

### Table level

```
[CONSTRAINT constraintname] constrainttype
(columnname, ...);
```

When making a table and a constraint at the same time, you do the constraint code only after all the columns are defined

The only difference between column and table level syntax is that with table you provide the column name at the end in parenthesis, ***more fancy***

all constraints are enforced at the table level
if a data value violates a constraint, the entire row is rejected

to existing tables:
using ALTER TABLE:
	NOT NULL = MODIFY (lmnop but reversed)
	 everything else uses ADD clause

PRIMARY KEY constraint

ensures that columns do not contain duplicate or NULL values
only one per table is allowed

composite primary key is separated by commas inside of the parenthesis

FOREIGN KEY constraint

requires that a value exists in the referenced column of another table
NULL values allows
keeps reference integrity 
maps to the PRIMARY KEY in parent table