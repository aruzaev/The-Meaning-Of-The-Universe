## Introduction
---

Querying the database enables you to verify existing database tables, the structure of the tables, and the data values that are stored in the database

This chapter focuses on retrieving data from a database by using SELECT statements

## DESCRIBE (DESC)

The DESC command is used most often to view the structure of database objects

It returns the following values:
- table name
- data types
- primary and foreign keys
- nullable columns
- etc.

![[Pasted image 20240509082723.png]]

## SELECT Statement Syntax

Most of the operations that organizations perform in SQL are the SELECT statements

These statements enable the user to retrieve data from tables given a set of parameters

The user can either view all of the values of a given table or specific records (**rows**) and fields (**columns**)

The SELECT statement is called a ***query*** because it asks the database a question about the values inside of the database

What gets displayed on the screen after the query are the **results** or the answer to the question

This is the specific syntax for the SELECT statement:
![[Pasted image 20240509083509.png]]

The words that are capitalized are the keywords that are used in conjuncture with the SELECT statement to give the query more customization 

Each section inside of the figure that begins with a keyword is called a **clause** (same thing as a sentence)

- The only clauses that are **required** for the SELECT statement is **SELECT** and **FROM** because our query requires a table to probe
- Square brackets are optional
- SQL statements can either be all in one line or split up into multiple. 
	- The best practice is to enter each clause on a separate line for bet readability
- An SQL statement must end in a semicolon

### Selecting aa


