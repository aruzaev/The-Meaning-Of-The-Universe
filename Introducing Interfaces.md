# [[Introducing Interfaces]]

An interface is a way to create classes in such a way that it separates the specification (blueprint) from the implementation

One class can implement many interfaces and one interface can be implemented by many classes

## Creating an Interface

```
modifier interface <InterfaceName> {
	// declaring the constants
	// method signatures - should be public by default
}
```

the `modifier` is usually public because we want to allow the interface to be implemented by any class, it is **implicitly public**

## Implementing Interfaces

```
modifier Class <ClassName> implements <InterfaceName> {
	// class body
}
```

The class must provide implementation for all the methods that have been declared in the interface

An interface can be used to declare a variable, reference data type

A reference data type is a fancy way of saying object that stores the reference to the value, **instead of the value itself**

When you declare a variable of a reference type, like `String`, you're actually pointing to an object that holds the actual data (rather than storing the data directly in the variable).

You can do this with an interface as well

It will **point to an on object that implements that interface**

## Interface and Inheritance

An interface can extend another interface

You must implement all methods from all of the interfaces being implemented

## Interfaces and Polymorphism



