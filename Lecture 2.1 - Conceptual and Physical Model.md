[[Database Concepts & Design]]

# [[Lecture 2.1 - Conceptual and Physical Model]]

Its important to recognize and analyze information to understand how things work and how you could make them better

Some examples include:
- how to make the line at the food counter better
- how to successfully exchange an item at a store
- how to organize and keep track of your growing CD collection

Understanding and analyzing information can also prevent mistakes and misunderstanding

**Steps in database design**:

1. **Requirement Analysis:** Understanding the business requirements and rules.
2. **Conceptual Design:** Creating an ERD to represent the high-level structure of the database without delving into details specific to any database management system (DBMS).
3. **Logical Design:** Refining the ERD to include keys, precise data types, and constraints, transitioning from a conceptual model to a logical model.
4. **Physical Design:** Translating the logical model into a physical schema that can be implemented in a specific DBMS. This involves defining tables, columns, data types, constraints, and indexes.

## What is a Conceptual Model?

A conceptual model is a structured business view of the data required to support the daily operations of a business

The characteristics of a conceptual data model are:
- An overall view of the structure of the data in a business context (no specific implementation data)
- Features that are independent of any database or physical storage structure (not tied down by software, just the schema)
- Objects that may not ever be implemented in physical databases (they may be some elements that won't be in the physical model, but they are just drawn to further understand the businesses needs deeper)
- Captures the functional and informational needs of a business
- Is based on current needs but it may reflect future needs
- Addresses the needs of the businesses but not its implementation
- Result of completing the data modelling process

What it **identifies**:
- important entities (objects that become tables in a database)
- relationships among entities

What it ***does not identify***:
- attributes (objects that become columns or fields in a database)
- unique identifiers (primary key in database)

It is important to the business because it:
- describes the exact needs of a business
- creates discussion amongst the DBA and business owner
- prevents mistakes and misunderstanding
- documents the process of the business (also called business rules)

## What is a Logical Model?

A logical data model establishes the main structure of the data elements and the relationships among them, without focusing on the physical implementation of it

It is normally derived from a conceptual data model 

The characteristics of a logical data model are:
- the inclusion of entities and their relationships
- is called an entity relationship model (ERM)
- is illustrated in an entity relationship diagram (ERD)
- Specifies all attributes (characteristics) of the entities and their unique identifier (UID)
- Determines attribute **optionality** (whether it must have a know value or not) and relationship **cardinality** (relationships between data in a database)

## What is a Physical Model?

A physical data model is an extension of the logical data model and gives the specific physical implantation of a database

It defines table definitions, data types, and precision
It also identifies views, indexes, and other database objects

Shows all table structures, including:
- columns
- primary keys
- foreign keys

## Conceptual and Physical Models

Data modelling is the process of capturing the important concepts that shape a business and depicting them visually on a diagram

This blueprints creates better understanding of the business and allows for easier implementation of the physical database
