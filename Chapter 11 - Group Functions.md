# [[Chapter 11 - Group Functions]]

Group functions, also called multiple row functions, return one result per group of rows processed

These are the most common group functions:

```
SUM([DISTINCT | ALL] n) -- Returns the sum or total value of the selected numeric field. Ignores NULL values

AVG([DISTINCT] | ALL] n) -- Returns the average value of the selected numeric field. Ignores NULL values

COUNT(*[DISTINCT | ALL] c) -- Returns the number of rows containing a value in the identified field. Ignores NULL values unless (*) is used instead of a field name
SELECT COUNT(*) FROM books; OR SELECT COUNT(shipdate) FROM orders;

MAX([DISTINCT | ALL] c) -- Returns the largest value from the selected field. Ignores NULL values 

MIN([DISTINCT | ALL] c) -- Returns the smallest value from the selected field. Ignores NULL values

STDDEV([DISTINCT | ALL] n) -- Returns the standard deviation of the selected numeric field. Ignores NULL values

VARIANCE([DISTINCT | ALL] n) -- Returns the variance of the selected numeric field. Ignores NULL values

GROUP BY Extensions

GROUPING SETS -- Enables performing multiple 
```

## Group Functions 

They process groups of rows, also called **aggregate functions**

Things to know:
- use the DISTINCT keyword to include only unique values. The ALL keyword is used by default
- All group functions (except for the COUNT(\*) function), ignore NULL values. To include them, nest the NVL inside of the group function  

### The SUM Function

Used to calculate the total amount stored in a column filled with numeric data

**DISTINCT** means to include only the unique numeric values in the calculation
**ALL** means to include multiple occurrences of numeric values

Assumes ALL by default

### The AVG Function

Finds the average of numeric values in a specified column

To specify the result to two decimal places, we use TO_CHAR to round the decimals

## Grouping Data

78