# [[Lecture 8.3 - Relational Mapping]]

When building a house, you can have all the tools and materials ready at your disposal but if you don't know how many rooms there will be, what colour the house should be, and how many windows to have the final product can be very different from what the customer had in mind

It's important to make a blueprint, especially with a database

---

Relationships are mapped with the linkage of primary and foreign keys and show the relationship one table has to another

If we don't map the relationships, then we just have a bunch of standalone tables that don't seem to interact with each other at all 

## Rules for Relationships

Relationships are established by using foreign keys, which are columns in one table that reference the primary key in another table (another column with a unique identifier)

The foreign keys are located on the many side of the relationship (one department has many employees, the foreign key will be in the employee table)

Foreign key column can be **optional** or **mandatory**

![[Pasted image 20240322130121.png]]

## Mapping of Mandatory Relationship at the One Side

Foreign keys can only enforce mandatory relationships on the **many side**, this is a limitation of the physical model

This means that in a one-to-many relationship, you can enforce that the child table (the "many" side) must have a corresponding parent record, but you can't enforce the same requirement on the parent table (the "one" side) using foreign key constraints alone.

![[Pasted image 20240322130854.png]]

The model cannot enforce that a BAND must consist of at least one MUSICIAN

## Mapping of Nontransferable Relationships

**Nontransferable relationship**: when the foreign key column in a database cannot be updated

This is mostly enforced through code and documentation so that the code is appropriate for the business rule

![[Pasted image 20240322152750.png]]

## Mapping of Barred Relationships

Can be mapped as a foreign key column just like the above 1:M relationships

One small caveat is that it's also part of the **primary key**

![[Pasted image 20240322153213.png]]

## Cascade Barred Relationships

**Cascade barred relationships**: A series of relationships where the unique identifier of each entity in the chain is carried down to the entity on the next level

Never use more than two table prefixes for the naming scheme so that the name isn't too long

![[Pasted image 20240322153535.png]]

![[Pasted image 20240322153657.png]]

## Mapping Many-to-Many Relationships

Many to many relationships are resolved using an intersection table

This table includes foreign key columns that originate from the main tables on both sides

![[Pasted image 20240322153848.png]]

## Mapping One-to-One Relationships

You need to create a **foreign key** and a **unique key**

Columns within the foreign key are also a part of the unique key

If the relationship is **mandatory**, the foreign key will be on the mandatory side

![[Pasted image 20240322154201.png]]

If both sides are optional, then you can choose which table gets the foreign key

Some guidelines for this:

- put the foreign key in the table that has the fewest rows to save space
- put the FK where it makes sense from a business standpoint

![[Pasted image 20240322154354.png]]

## Mapping Arcs

The entity that has the arc will be the one to have the foreign keys from the other tables

Both foreign keys need to be set as optional in the main table (even if mandatory) because one of them will always be blank

![[Pasted image 20240322154634.png]]

![[Pasted image 20240322154720.png]]