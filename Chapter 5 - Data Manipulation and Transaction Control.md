# [[Chapter 5 - Data Manipulation and Transaction Control]]

This chapter talks further about methods for adding new data rows and modifying or deleting existing data rows

These commands are different from DDL statements because they ***affect the information stored in the tables*** NOT the structure of the table

Commands that modify data are called:
**DML - data manipulation language** commands

Commands that permanently save the data or undo data changes are called **transaction control commands**

These are all the commands that we will use in this chapter:

```
INSERT -- Adds new rows to a table, can have subqueries to copy existing rows from an existing table

UPDATE -- Adds data to, or modifies data in, existing rows

DELETE -- Removes rows from a table

COMMIT -- Saves the changes made to the data in the table permanently

ROLLBACK -- "Undoes" uncommited changed to the data 

SAVEPOINT -- Enables setting markers in a transaction in order to rollback

LOCK TABLE -- Prevents other users from making changes to a table

SELECT ...
FOR UPDATE -- Creates a shared lock on a table to prevent another user from making changes to the data in the specified columns of the table
```

## Inserting New Rows

When a table is created and all the constraints have been added (note. constraints and settings for the table are always added BEFORE data is added)

we can add data to the table

### Using the `INSERT` Command

To add new rows of data to a table, we use the following command:

```
INSERT INTO tablename [(column name, ...)]
VALUES (datavalue, ...)
```

The square brackets are optional

Inside of the `VALUES` clause is where the list of data values that will be inserted into the table are identified

If the data that is being entered into the `VALUES` clause has a value for every column in the table and is in the same order as columns in the table, you don't need to add the column name in the  `INSERT INTO` clause

If there are missing values in the `VALUES` clause, or they're in a different order than what they're listed in the table view, the column names MUST be listed in the `INSERT INTO` clause in the same order that the `VALUES` list is presented

You must use single quotes to enclose nonnumeric data inserted in a column

It is best practice to always enter the data list in all uppercase because `INSERT INTO` retains the cases that are used, and if they are mixed cases then it can be impossible to search through

**No formatting symbols (e.x. $ or ',') are allowed because they will cause an error**

#### NULL VALUES

You can take one of the following approaches to make a certain column contain a NULL value

- List all columns *except* for the NULL column in the `INSERT INTO` clause, provide data for all the other listed columns inside of `VALUES`
- Substitute the value in the `VALUES` clause with a ('') to indicate that it is a NULL value, don't add a space
- Include the explicit keyword NULL in the appropriate column 

![[Pasted image 20240611074415.png]]

#### DEFAULT VALUES

You can instruct Oracle to use DEFAULT values using the following methods:

- Insert a column list inside of the `INSERT INTO` clause that omits the column in the table that you want to make default
- Use the explicit keyword DEFAULT in the appropriate column

![[Pasted image 20240611074734.png]]

It isn't a requirement to have the `INSERT INTO` values be in the same sequence as the table, what **is a requirement is to have the values in** `VALUES` **clause be the same sequence as the** `INSERT INTO` **values**

The order of the list dictates which data value is assigned to which column.