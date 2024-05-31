# [[Lecture 8.4 - Subtype Mapping]]

Mapping subtypes is important because it makes sure that the correct information is being stored with each type

i.e. a builder who uses different kinds of bulbs for a new house, the bedroom will have dim lights and the kitchen bright lights

## Single Table Implementation

Creates a single table for the supertype entity and its subtypes

Rules:
- only one table is ever made, no matter how many subtypes there are
- one column for each attribute of the supertype in the table and original optionality for the attribute
- also a column for each attribute in the **subtypes** but they are all optional
- unique identifiers become primary and unique keys
- Supertype relationships are like normal
- Subtype relationships become optional FK columns
- A check constraint is needed to make sure all columns that are mandatory are not null
- a **mandatory column** should be made to act as a **separator** between the different subtypes of the entity

![[Pasted image 20240322155943.png]]

A note about the OTHER subtype:An OTHER subtype is recommended in the conceptual model to ensure that the subtypes are exhaustive.However, by the time we start the design phase, we should have done extensive analysis to determine ifanother subtype is truly needed. If so, then this subtype must be named, and its attributes specified. If not,then the OTHER subtype is not part of the transformation process.

![[Pasted image 20240322160317.png]]

### When to use the Single Table Implementation?

This is a common and flexible implementation and oftentimes should be considered as the **first choice**

It is appropriate where:
- most of the attributes are at the supertype level
- most of the relationships are at the supertype level
- business rules are globally the same for the subtypes

## Two Table Implementation

You create a table for each of the subtypes

Rules:
- One table per first-level subtype
- one column for each attribute of the supertype and subtypes in the table and original optionality for the attribute
- primary uid of the supertype becomes a **primary key** for each table
- secondary uid of the subtypes become **unique keys** for each table
- All supertypes get a foreign key for each relationship with original optionality
- For subtypes, the FK is placed in the table it is mapped to with original optionality
	- this removes the need for a check constraint

![[Pasted image 20240322161541.png]]

![[Pasted image 20240322161559.png]]

Continue notes next week



