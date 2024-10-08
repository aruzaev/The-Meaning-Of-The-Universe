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

Allows child classes to inherit the characteristics of an existing parent class

These characteristics include
- attributes (fields or variables)
- operations (methods)

Child classes can **extend** the parent class (the base class or the super class)

With extend we can:
- add new variables and methods
- redefine methods (modify existing behavior)

### General and Specialized Classes

Inheritance allows for existing classes to be specialized 

This makes it so that their behaviors are modified to suit the specific needs but they still have the addition of the functionality of their parent class

![[Pasted image 20240909085036.png]]

![[Pasted image 20240909085058.png]]

The professor and student all inherit the name and address fields that are seen in the student class, but they add their own specialized fields as well

### Inheritance Guidelines

- A class can only inherit one base class
	- the Student class can only be derived from the Person class and not any other base class at the same time
- Inheritance uses an "is-a" relationship style
	- e.x. Student is a Person
- Do not use it for a "has-a" relationship style
	- e.x. Student has-a name (students are not names)

### Benefits

- **Extensibility** - new functionality can be added to subclasses without changing existing classes
- **Reusability** - a set of classes can be used for many different applications, while also allowing base classes to be extended to add their own specialized functionality that is needed for the application
- **Reducing redundancy** - removes the need to recreate full classes to add new functionality, you can just extend it

### Deriving a Class

Here are the steps for declaring a derived class

1. Declare the inheriting class
2. Add the `extends` keyword to the declaration
3. Specify the name of the base class

```
public class Parent {
	private int x;
	...
}

public class Child extends Parent {
	private int y;
	// doesnt have access to x unless x is protected
	// need getter and setter to access x
}
```

### Accessibility Levels

- `public` - access is not restricted, class members are accessible to all other classes
- `private` - access is restricted and only accessible to inside the class itself
- `none (default or package)` - access is limited to any class in the same package
- `protected` - access is limited to the same package and to derived classes 

### Base Class Constructor

Private fields of a base class are not accessible in a subclass
To initialize those fields we need to pass them to the **base class constructor**

### The `super` keyword

The `super` keyword refers to the immediate parent class object (superclass)
It it used to:
- refer to the immediate parent class instance variable
- call a superclass constructor when creating instances of the derived class
- call a method of the superclass

### Invoking Base Class Construction

You can use the syntax: `super(<arguments>)` to invoke the constructor of the base class

```
class Child extends Parent {
	private int y;

	public Child(int x, int y) {
		super(x) // initialization of x from the Parent class
		this.y = y; // initialization of y from the Child class
	}
}
```

The `super(<arguments>)` call must be the first statement in a subclass constructor

Superclass constructor is always either called implicitly (without writing it) or explicitly

Java by default created a superclass constructor **without parameters**

### Simple Inheritance Example

Declaring a class Person

```
public class Person {
	private String name;

	public Person(String name) {
		this.name = name;
	}

	public void printName() {
		System.out.println("Name: " + name);
	}
}
```

```
public class Student extends Person {

	private int[] courses;

	public Student(String name, int[] courses) {
		super(name);
		this.courses = courses;
	}

	public void printCourses() {
		for (int c : courses)
			System.out.println("Course ID: " + c);
	}
}
```

### Inheritance: Important Aspects

- You can't do multiple inheritance, a Java class cannot be derived from two classes
- Inheritance is a transitive relation
	- if C is derived from B, and B is derived from A, then C inherits A as well
- Constructors are not inherited
	- They need to be chained using superclass constructors

### Inheritance: Important Features

- A child class inherits all the properties and methods of the base class
	- the derived class is just a specialized version of the base class
	- it can add new members but cannot removed the derived ones
- Declaring a method in a subclass with the same signature (name and arguments) as the one in the superclass overrides the inherited one
- Declaring a static method with the same signature hides the inherited one 

### Method Overriding

Redefining the functionality of a base class method inside of a child class using the same list of parameters (or else it would be an entirely different method and won't override)

When a method is called for a child object, we use the overridded method instead of the super class method

### The `@Override` Annotation

This tells the compiler that a method in the superclass is meant to be overridden

The overriding method must have the same signature as the overridden base method

The signature consists of
- return type
- method name
- parameters list

### Abstract Classes

Used solely for the purpose of subclassing

They are templates which define common sets of behavior that are shared by concrete classes that inherit them

Declared with the word `abstract`

### Abstract Class Features

May be partially implemented or fully unimplemented without any errors
- unimplemented methods are declared as `abstract` and left empty

Cannot be instantiated

A non-abstract class that is trying to inherit an abstract class must have all methods in the abstract class implemented

Child classes that don't implement abstract methods must be declared as abstract

![[Pasted image 20240909113139.png]]

### Abstract Methods

This is a method that doesn't have a body

It declares the method signature and the return type that the concrete subclass must implement

They have no body since it isn't the actual implementation

Ends in a semicolon

`abstract returnType methodName(Parameters);`

### Abstract Method Features

Abstract methods are created to be overridden in the concrete subclass

These abstract declarations are only allowed inside of abstract classes
- if a subclass doesn't have implementations for some of its parent's abstract method, the subclass also becomes ab abstract class
  
![[Pasted image 20240909113725.png]]

## Polymorphism

<<<<<<< HEAD
We just learned about inheritance and encapsulation. If you have any questions do not hesitate to bring them on the 15th. Let's start part of this series where we talk about obstruction very simple.

Template.
=======
The ability to take many forms

Allows the objects of subclasses to be treated as objects of a base class

### Example

Imagine a base class called Shape

Different shapes have different ways of calculating the area, so we can define a different getArea() method for each type of shape

Using a base class reference, calling the getArea() method on any type of shape will give the correct results

![[Pasted image 20240911164038.png]]

### Casting Objects

An object of a subclass is able to be treated as if it was part of the parent class, or any of its ancestor classes

This is called upcasting (we are casting up the hierarchy)

### Upcasting

There are two ways of upcasting:

1. `Employee e = new Manager()` // making the reference be the base class object
2. 
   ```
   public void giveRaise(Employee e) {...}
   Manager m = new Manager();
   giveRaise(m);
   ```
   
   Through a method that accepts a reference to a base class object

Upcasting doesn't change the object itself, it only gives it a different label

The unique methods of the object are hidden because the parent class doesn't have those methods, hidden until it's downcasted

### Accessing Members with Upcasting

When upcasting happens, only the fields and methods declared by the base class are accessible

When a method is called through the base class, if it is overridden by the subclass, the subclass version will be executed

### Example

![[Pasted image 20240911170954.png]]

```
Employee e = new Manager();

e.setGoals(); // employee method ran since doesn't exist in manager
e.getSalary(); // manager method ran since overide
e.runReview(); // compile time error since employee doesn't have that method, its hidden
```

### Polymorphism Methodology

Ensures that the appropriate method of the subclass through its base class reference

Implemented using a technique called late method binding
- the exact method to be called is determined at run time, just before making the call

![[Pasted image 20240911171414.png]]

![[Pasted image 20240911171427.png]]

### Downcasting

A higher class can be downcast to a subclass

```
Employee e = new Manager();
...
Manager m = (Manager) e;
```

This isn't safe and the object referenced must be a member of the downcast time

Or else we get the `ClassCastExaption` at run time

![[Pasted image 20240911171655.png]]

The issue here is that Contractor and Manager are **sibling classes** meaning that they exist on the same hierarchy level and they don't have an "is-a" relationship

One way to make this code work is by using something called the `instanceof` operator
### instanseof Operator

This is used to test whether an object is a member of a specific type

Comparison operator

Used to test whether a cast will work without an exception being thrown

```
Employee e = new Contractor();

if (e instanceof Manager) {
	Manage m = (Manager) e
} else {
	System.out.println("e is not a Manager");
}
```

### Benefits of Polymorphism

It enables programmers to deal with generalities, leading to less confusion when handling the specifics

Programmers can command objects to behave in manners that are appropriate to the objects 
- even before these objects are made

Makes the code simpler
- Can ignore type specific details

Makes it easier to maintain

Makes it very extensible
- can add other subclasses later and have them work with the existing code
>>>>>>> 7f814dd57c178bd6cbf6cf8171f5695026b96eee
