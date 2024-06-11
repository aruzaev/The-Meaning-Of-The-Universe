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

### Inserting Data from an Existing Table

If a table already exists, and you need to add a couple records from that table into another table you would do this:

```
INSERT INTO tablename [(columname, ...)]
subquery;
```

The main difference between this and the previous `INSERT INTO` clause is that the `VALUES` clause isn't present

> the data is derived from the subquery's results

The subquery is also allowed to not be enclosed in parenthesis

example:
```
INSERT INTO acctbonus (amid, amsal, region)
	SELECT amid, amsal, region
		FROM acctmanagerl
```

## Modifying Existing Rows

To alter existing table data, you need to use the `UPDATE` command

### Using the UPDATE command

```
UPDATE tablename
SET columnname = new_datavalue, ...
[WHERE condition];
```

The `SET` clause identifies which columns need to be changed and their new values

The optional `WHERE` details the *exact records to be changed* using a condition statement, if it's removed, then the update in the `SET` clause is updates for *all records* in the table

example:

```
UPDATE acctmanager
	SET amedate = '01-AUG-09'
	WHERE amid = 'J500';
```

You can also use `IN` instead of =:

```
UPDATE acctmanager
	SET region = 'W'
	WHERE region IN('NE', 'NW');
```

If you need to modify more than one column of a row, you can do this using commas:

```
UPDATE acctmanager
	SET amedate = '10-OCT-09'
		region = 'S'
	WHERE amid = 'L500';
```

### Using Substitution Variables

When adding or modifying a record that takes a lot of effort, such as when there's a lot of them, you can use a substitution variable instead of typing the same command over and over

A **substitution variable** instructs ORACLE to create a value in place of a variable when the command is actually executed

To create a substitution variable you just need to type a (&) symbol followed by the name of the variable:
```
UPDATE customers
	SET region = '&Region'
	WHERE state = '&State';
```

Executing this command will open up a prompt where you can type in the data for the variable, when OK is hit, then the next prompt for STATE will appear which will allow you to specify which rows to modify

## Deleting Rows

To delete a row the syntax is this:

```
DELETE FROM tablename
[WHERE condition];
```

The `DELETE` doesn't specify any column names because it deletes an entire row of data

The `WHERE` clause is optional and specifies what rows to be deleted specifically

## Using Transaction Control Statements

When you execute an SQL statement, DML commands aren't saved to the table permanently

After doing the DML commands, you need to do **transaction control** statements in order to permanently save the data changes in the table

A transaction is a term that describes data actions caused by DML statements that should logically be performed together

**Transaction control** determines at which points DML statements are saved permanently to the database

### COMMIT and ROLLBACK Commands

The `COMMIT` command is used either **implicitly** or **explicitly** and saves the DML statements that have been executed previously

**Explicit `COMMIT`** - occurs when you enter a `COMMIT` statement
**Implicit `COMMIT`** - occurs when you exit various tools, such as the SQL Developer.
> It can also occur when a DDL (data definition language) commands are executed (`CREATE or ALTER TABLE`)
> 
> this means that if a user adds several data entries into a table and then makes a new table, the data entries will be saved

**A transaction is a series of statements that have been executed but not committed**

Unless the DML operation is committed, they can be undone by using the `ROLLBACK` command

`ROLLBACK` will reverse every change made that hasn't been committed or saved and will reverse **until the last commit**

However **DDL commands such as `CREATE TABLE, TRUNCATE TABLE, ALTER TABLE` CANNOT be rolled back** because they are commands that impact the structure of the table, NOT the data within the table

### SAVEPOINT Command

The `SAVEPOINT` command is sometimes used as a kind of bookmark for a transaction

`SAVEPOINT` creates various `ROLLBACK` points to rollback to a certain point in the transaction

The syntax for creating a `SAVEPOINT` is as follows:
```
SAVEPOINT name;
```

To rollback:

```
ROLLBACK TO SAVEPOINT name;
```

Commits still need to be made