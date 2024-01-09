[[Database Concepts & Design]]

## Database Development Process
---

**Step 1**: Data Modelling

Collection and analysis of the date a business or client needs to track, then diagramming how the data will be organized using an Entity Relationship Diagram (ERD)

During this step, questions about the information requirements of a business need to be asked

**Step 2**: Database Development Process

Converts the ERD to a Table Instance Chart which has the following components:
- Table name
- Column names
- Keys 
	- Primary Key (PK) which is the unique identifier for each row of data
	- Foreign Key (FK) which links data from one table to another by referencing the PK column in the second table
- Nulls (indicates if a column has a value or is undefined (null))
- Unique (indicates if a value in a column is unique within the table)
- Data type (Defines the format of the data stored in each column)

SQL (Structured Query Language) is uses to build the physical structure of the database

It is also used to add, access, and manipulate data within a database