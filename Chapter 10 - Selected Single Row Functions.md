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

This is also called a **substring**

The syntax of this function is `SUBSTR(c, p, 1)` where c is the character string, p is the beginning position in the string that we want to extract, and 1 is the length of the string that we want to get in the results

```
SELECT DISTINT SUBSTR(zip, 1, 3)
FROM customers;
```

This means that we are getting unique zip codes starting from the first character, and extracting three characters from the string

Since we have this function in the `SELECT` clause, the substring is simply displayed in the results, nothing is modified

You can also use negative numbers in the substring arguments, which means extracting substrings from the end of the data

If you enter -3 for the beginning position, then the system counts backward three positions from the end of the field 

12345
Entering (zip, -3, 2) will give the third and fourth digits of the zip code (3 and 4)

### The INSTR Function

The `INSTR` function returns the position of a substring within a string, it returns a numeric value of the first occurrence of the substring

If it doesn't find anything it simply returns 0

The `INSTR` function has two mandatory arguments, the string value to be used in the search and the characters that need to be located

There are two other **optional arguments**:
- the starting position where the search should be started (negative values can be used)
- occurrence (which occurrence should be returned, first, second, or so on)
\
By default the search begins at the beginning of the string, and the first occurrence is located

```
SELECT name, INSTR(name, ',') "First comma",
	         INSTR(name, ',', 10) "Start read position 10",
	         INSTR(name, ',', 1, 2) "Second comma"
```

![[Pasted image 20240715173316.png]]

The image above gets the position of the first position (which is located by finding the position of the first comma and then adding it by 1, so the starting SUBSTR position is just after the first comma)

We then find the second occurrence of the comma and subtract the position of the first comma from that and subtract 1 so that we don't include the second comma in the substring

### The LENGTH Function

Used to determined the number of characters in a string

```
SELECT DISTINCT LENGTH(address)
FROM customers
ORDER BY LENGTH(address) DESC;
```

We order by the length of the unique addresses

### The LPAD and RPAD Functions

The `LPAD` function is used to pad or fill in the area to the left of a character string with a specific character or a blank space

The syntax is this:
LPAD(c, 1, s) where c is the character string that we want to pad, 1 is the length of the character string AFTER padding, and s is the symbol to use as padding

```
SELECT firstname, LPAD(firstname, 12, '*')
FROM customers
WHERE firstname LIKE 'J%';
```

The first argument specifies the padding in the firstname field,
the second argument means that the column should be padded to a total length of 12 characters with the padded symbols included
the third argument is the symbol to be padded with

the `RPAD` functions is the same, just on the right side

### The LTRIM and RTRIM Functions

You can use the LTRIM function to remove a specific number of characters from the left side

They are used to remove unwanted spaced from strings

The syntax is this:
LTRIM(c, s)

c is the field to modify, and s is an optional parameter and is the string to remove from the data

Example:
If we want to get the P.O. BOX address but some people have "P.O. BOX" inside of the address string:

```
SELECT lastname, LTRIM(address, 'P.O. BOX')
FROM customers
WHERE state = 'FL';
```

### The REPLACE Function

Similar to the "search and replace" function that many programs use

It looks for the occurrence of a specified string of characters and substitutes it with another set of characters if found

The syntax is this:
REPLACE(C, S, R) where c is the field to look for, s is the string of characters to find, and r is the string of characters to substitute for s

```
SELECT address, REPLACE(address, 'P.O.', 'POST OFFICE')
FROM customers
WHERE state = 'FL';
```

### The TRANSLATE Function

Used to replace a character in a string with a new value

Different 