# [[Lecture 8.2 - Basic Mapping]]

When creating a conceptual model, our main focus is on defining the business rules and relationships

The database design focuses on storage, speed of retrieving information, and security

Meeting the business requirements is the most important part of designing a database

Tables have columns and rows

Each row mentions an instance of an entity

![[Pasted image 20240319153342.png]]

Each column has a specific type of value such as first name, last name, and employee number

Each table has a uid (PK) which distinguishes each individual row

The payroll id is a **unique key** which means that it does not allow two rows to have the same payroll id

The department id is a **foreign key** which refers to a PK column in the DEPARTMENTS table