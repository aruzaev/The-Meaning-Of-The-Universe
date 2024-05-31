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
```


