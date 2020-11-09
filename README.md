# Getting-started-with-inheritance-using-c#

### Introduction

Inheritance is one of the most important concepts in object-oriented programming. it allows the definition of a class in terms of another class. It also allows us to maintain and boost an application. Classes are created by absorbing the methods and variables of an existing class, It then adds its own methods to enhance its capabilities. This class is called a derived class because it inherits methods and variables from a base class. Objects of a derived class are objects of a base class, but not vice versa. A derived class can only access non-private base class members unless it inherits accessor functions.

### Prerequisites

1. Basic understanding of C# programming language. 
1. Basic understanding of how Classes work.

### Base classes and Derived classes

**Base** classes are used to generate derived classes that inherit the properties of the base class

![inheritance tree](https://raw.githubusercontent.com/mohamedgh16/Getting-started-with-inheritance-using-c-/main/tree%20of%20inheritance.png)

* An object is often an object of another class
* Every derived-class is an object of its base class
* Inheritance forms a tree-like Hierarchy
* Constructors are not inherited
* To specify class one is derived from class two
```c#
class one : two
```

### Protected and internal members

#### Protected members
Can be accessed by base class or any class derived from that base class

#### Internel members
Can only be accessed by classes declared in the same assembly

### Relationship between Base classes and Derived classes

The first thing a derived class does is call its base class constructor, either explicitly or implicitly



