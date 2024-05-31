## Introduction
---

Generally, unless you use DISTINCT and the UNIQUE keywords, whenever you query the table you get the entire table, this is called **projection**

However there is another form of querying a table called **selection**, which is when you receive records only when they meet certain condition

Since there can be thousands or millions of records inside of a table, using selection can help drastically reduce the amount of records that will be outputted

This chapter will focus on the following keywords and operators:

- WHERE clause - used to specify conditions that must be true for a record to be included in the query results
- ORDER BY clause - used to specify the sorted order for displaying query results
- Mathematical comparison operators (=, <, >, <=, >=, <>, !=, ^=) - used to indicate how a record should relate to a specific search value
- other comparison operators (BETWEEN ... AND, IN, LIKE, IS NULL) - Used in conditions with search values that include patterns, ranges, or NULL values
- logical operators (AND, OR, NOT) - used to join multiple search conditions (AND, OR) or reverse the meaning of a search condition (NOT)

## WHERE clause syntax

In order to retrieve records from the database based on a given condition, we need to use the WHERE clause in the SELECT statement

![[Pasted image 20240515182146.png]]

According to the syntax, it needs to appear after the FROM clause and the square brackets denote that it is **optional**

A **condition** identifies what must exist or a requirement that must be met in order for a record to be included in the results

The database will then search through all of the records according to the specified condition of the query

If a condition is TRUE, then the query gets returned properly in the query 

In order to display a list containing the last name of every customer living in Florida, you need to use the following SQL statement:

```
SELECT lastname, state
	FROM customers
	WHERE state = 'FL';
```

This query specifies the lastname and state columns that are stored in the CUSTOMERS table

By itself, this would be called projection since we are **limiting the output to specific columns***, however we also have the WHERE clause to see the customers who have FL stored in the State field

in the WHERE clause, WHERE is the keyword, State is the name of the column to be searched, and the comparison operator (= or "equals to") means that the record MUST contain the exact value that has been specified (in this case it's 'FL')

The single quotations around 'FL' mean that it is a **string literal**, which makes SQL interpret FL literally

FL is also in all uppercase to match how it's like in the database

The process of limiting output to specific rows is called **selection**

### Rules for Character Strings

Since FL is enclosed in single quotes, it means that it is a string literal, which results in anything between the quotes being interpreted **exactly as listed**

However, if the field that is used in the WHERE clause uses only *numbers*, then the single quotes aren't needed:

```
SELECT *
FROM customers
WHERE customer# = 1010;
```

The same can be done for the book table with ISBNs:

```
SELECT *
FROM books
WHERE isbn = 9238923892;
```

Since there are no values in ISBN that contain letters, we can search the field with a numeric input without using any quotation marks

However, if the table has even **one letter** inside of the ISBN field, then not using a quotation would cause an **error message**

Ultimately, using single quotation marks depends on if the field is meant to hold numeric of text data, because of this we should ***always use single quotes*** if the column is defined with anything other than a numeric data type

### Rules for Dates

Usually dates are displayed with the format of ``DD-MON-YY`` with MON being the three letter abbreviation for the month

Since the month format has **hyphens (symbols)** and **letters**, it needs to use single quotes

```
SELECT *
FROM books
WHERE pubdate = '21-JAN-05';
```

## Comparison Operators

So far, we've only used an equal sign, which is called an **equality operator**, to evaluate search conditions

This essentially means that we instruct SQL to only return the results that contain the *exact* value that is provided after the equals sign

However there are different types of searches that aren't based on the "equal to" operaton

***Example***

Management wants to include a gift with the purchase of any book that retails for more than $55.00

The equality operator won't be suitable in this situation so we need to use a different operator called the **comparison operator**

This comparison operator allows us to search for things that are less than or greater than a certain target:

```
SELECT title, retail
FROM books
WHERE retail > 55;
```

This results in four books being printed where the retail price is greater than 55

Even though we entered 55, SQL will also accept partial decimal points such as 55.00

However entering a dollar sign or a comma within the number would give an error message because they are **symbols** (this means than 55.00 != $55.00)

Oracle doesn't have a datatype, so it views commas and dollar signs as characters which need to be part of a string

The (>) operator can also be used with **text and date fields**, which will appear alphabetically

In order to create a query that shows a list of books with a title occurring alphabetically after the letters HO, all of the titles with characters following HO will be listed

```
SELECT title
FROM books
WHERE title > 'HO';
```

![[Pasted image 20240521084343.png]]
 
There are other comparison operators that can also be used in conjuncture with math statements such as

```
SELECT title, retail-const profit
FROM books
WHERE retail-cost < cost*.2;
```

This searches for all of the books that have a profit of less than 20% of the books cost

Since profit is determined by subtracting the cost from the retail price, the calculated value can be compared against the book's cost multiplied by .20

The less than and greater than operator don't include values that directly math the condition

In order to do that we need to use the greater/less than or equal to operators (>=, <=)

