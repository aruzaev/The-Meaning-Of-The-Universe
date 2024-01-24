# [[Lecture 2.2 - Entities,  Instances, and Attributes]]

## Entities

An object or element of significance to the business about which data must be known

Usually a noun (examples, events, people)

It's important to learn about entities because they are the things about which we store data

All entities must have an instance (a single occurrence of an entity)

![[Pasted image 20240123114947.png]]

Example:
A school needs to store data about entities such as: 
- STUDENTs
- TEACHERs
- COURSEs
- ROOMs
- GRADEs

Entities can be **tangible** (perceptible to the senses, especially touch), like a person or a thing; or **intangible** (incapable of being perceived by the senses), like a skill level

**ENTITY - concept that is abstract, not in the physical realm**
**INSTANCE - a single occurrence of an entity**

DOG can either be an instance or an entity:
- if we consider a list of different species of animal entities, a dog would be an **instance**
- if we consider a list of species of dog entities, an instance would be the specific breed of dog

## Attributes

The important details of an entity that are important to the business

Has a single value

Attributes are important because they provide specific information about an entity

Example:
- the entity FRUIT has attributes of name, type, region, and data picked

This specific information allows you to distinguish one instance (physical implementation of an entity) from another

Example:
- You need to list individual items on a customer's order to determine the bill at a restaurant (the orders will differ from customer to customer)
- When creating several sales report, you need to be able to identify a specific report from a list of them (unique identifier)

Attributes have values which can be:
- a number
- character string
- date
- image
- sound

These are called **data types** and each attribute has one piece of data with a specific data type 

![[Pasted image 20240123120036.png]]

family name can have a data type of a string and shoe size can be a number

An attribute **can only have one value at a time** but that value can change

Example:
	an entity CAR can have an attribute colour and model, but the car can only really have one colour or model

Some attributes have values that always change called **volatile** attributes (age, net worth, order data)

Some attributes have values that rarely change called **nonvolatile** attributes (date of birth, model, year of production)

Nonvolatile attributes are better because they won't need to be updated frequently
	updating the age of customers would take very long if we had 1,000,000, it would be easier to deduce their age from their dates of birth

**Optionality**: some attributes are mandatory (they must have a value) but some are optional (they can either be null or have a value)