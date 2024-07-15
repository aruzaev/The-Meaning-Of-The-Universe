# [[Chapter 10 - Selected Single Row Functions]]

A function is a prewritten block of code that allows for **one or more arguments**, the function processes those arguments and then outputs a single value as output

**Single row functions** return only one row of results for each record that has been processed
In other words, it operates on each row of the table individually and returns one result per row

**Multiple row functions** operate on multiple rows of the table and returns a single result based on those multiple rows

There are different types of functions:
```
Case Conversion Functions                -- UPPER, LOWER, INTCAP
Character Manipulation Functions         -- SUBSTR, INSTR, LENGTH, LPAD/RPAD,                                             LTRIM/RTRIM, REPLACE, TRANSLATE,                                              CONCAT
Numeric Functions                        -- ROUND, TRUNC, MOD, ABS, POWER
Date Functions                           -- MONTHS_BETWEEN, ADD_MONTHS,                                                   NEXT_DAY, LAST_DAY, TO_DATE,                                                  ROUND, TRUNC, CURRENT_DATE
Regular Expressions                      -- REGEXP_LIKE, REGEXP_SUBSTR
Other Functions                          -- NVL, NVL2, NULLIF, TO_CHAR,                                                   DECODE, CASE expression, SOUNDEX,                                             TO_NUMBER
```

## Case Conversion Functions

Character functions allow you to convert the cases of the characters within a string

For example converting lower case letters to all uppercase using `UPPER`

This is mostly used for when application developers want to make user friendly apps that utilize an sql database

**Case conversion functions** alter the case of a character string

When these functions are used in a **query**, the output that is being shown on the bottom is temporary and **doesn't affect how the data is stored**

However, when used inside of an INSERT statement, the functions can change how the information is stored in the table

### The LOWER function

If data is being stored in uppercase, a new user might try to query the data using lowercase because they didn't know

Since SQL queries are **case sensitive**, this query won't work since there aren't any results that match directly to that

You can solve this by using the `LOWER` function which converts the character strings in the row to lowercase:
```
SELECT firstname, lastname
FROM customers
WHERE LOWER(lastname) = 'nelson';
```

The result of this query will still be in uppercase, this is because we haven't used the `LOWER` function inside of the `SELECT` clause:

```
SELECT LOWER(firstname), LOWER(lastname)
FROM customers
WHERE LOWER(lastname) = 'nelson';
```

You must still include the `LOWER` function inside of the `WHERE` clause because the data in the table is still in uppercase and needs to be converted

#### When a function is used in a `SELECT` clause, it only affects *how the data is displayed in the results*. When a function is used in a `WHERE` clause, it *transforms the data* as needed to evaluate the comparison condition

### The UPPER function

Converts characters into uppercase letters, used in the same way as the `LOWER` function

You can use the substitution variable in conjuncture with the `UPPER` function to make sure that the information that is stored in the table is always uppercase

```
SELECT firstname, lastname
FROM customers
WHERE lastname = UPPER('&Custval');
```

### The INITCAP Function

This is a way to convert single case strings (strings that are either lowercase or all uppercase) into mixed case strings in order to be more readable

**Mixed case** - the first letter is capitalized and the rest are lowercase:
```
SELECT INITCAP(firstname) "First Name", INITCAP(lastname) "Last name"
FROM customers
WHERE lastname = 'NELSON';
---
Becca Nelson
```

```
SELECT INITCAP('the soap') "Capitals"
FROM dual;

Capitals
---
The Soap
```

## Character Manipulation Functions

Character manipulation functions are used to perform various operations on data strings

These operations include modifying, searching, and formatting text

For example you might want to identify the first three digits from zip codes in a certain state

### The SUBSTR Function

You can use the `SUBSTR` function to return an exact portion of a string, starting from a specified position and to an optional length

This is also called a **substring**, 