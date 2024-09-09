# [[OOP Principles]]

## Fundamental Principles of OOP

- **Encapsulation** - Hiding the internals of a class
- **Inheritance** - Inheriting members from parent class
- **Abstraction** - Reducing complexity by focusing only on necessary date
- **Polymorphism** - Treating subclass members like the base class

## Encapsulation

Encapsulation is the protective barrier that hides the information from the outside

It prevents the code and the data from being accessed from outside of the class

The way that you do this is by:
- hiding the internal code by making the fields and internal methods in a class **private**
- providing access the the code using **public methods** (getters and setters)

### Benefits

Ensures that any changes to the structure of the code are local
- changing the internal code of the class does not affect the code outside of the class
- changing the internal logic of an internal method doesn't impact any external code or client code that uses that method

It makes it easier to maintain
- hiding the code reduces the complexity, especially when the project gets very large

It also allows you to add logic to ensure that a new value is valid before making the change or accessing the client's data
- makes it more safe and efficient

### Accessors and Mutators

**Mutator (setter)** - modifies the field value of an object
- the usual convention is naming setters `setFieldName`

**Accessor (getter)** - returns a field value of an object
- the usual convention is naming getters `getFieldName`

## Inheritance



