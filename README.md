# Getting-started-with-inheritance-using-c#

### Introduction

Inheritance is one of the most important concepts in object-oriented programming, it allows the definition of a class in terms of another class, it also allows us to maintain and boost an application.

Classes are created by absorbing the functions and variables of an existing class, it then adds its own functions to enhance their capabilities. This class is called a derived class because it inherits the functions and variables from a base class. Objects of a derived class are objects of a base class, but not vice versa. A derived class can't be able to access private base class members unless it inherits accessor functions.
### Table of Contents

1. Base classes vs Derived classes.

1. Protected and internal members.

1. Relationship between base classes and derived classes.

1. Constructors and destructors in derived classes.


### Prerequisites
Before we begin, the reader would need to have the following:

- A basic understanding of C# programming language. 

- A basic understanding of how Classes work.

### Base classes and Derived classes

**Base** classes are used to generate derived classes that inherit the properties of the base class.

Inheritance forms a tree-like Hierarchy:

![inheritance tree](https://raw.githubusercontent.com/mohamedgh16/Getting-started-with-inheritance-using-c-/main/tree%20of%20inheritance.png)

 **In inheritance**, an object is often an object of another class and all derived classes are objects of their base class, Also note that constructors are not inherited.
 This is how you specify a class child derived from class father: `class child: father`



### Protected members
Can be accessed by base class or any class derived from it.

### Internel members
Can only be accessed by a class declared within the same assembly.


### Relationship between Base classes and Derived classes

The base class constructor is the first thing to be called by a derived class, either explicitly or implicitly.

- **Override** keyword is needed if a derived-class function overrides a base-class function

- If a base class function is going to be overridden it must be declared **Virtual**



The following example will calculate the area and perimeter of a circle using inheritance: 

```c#
    public class Point
    {
       // point coordinate
      private int x, y;
      
      // constructor
      public Point( int xpoint, int ypoint )
      { // implicit call to object constructor
         X = xpoint;
         Y = ypoint;
         //Note that Output statements use a reference (This) to implicitly call the ToString method
         Console.WriteLine("point constructor: {0}", this)}
  
      public int X
      {
         get
         {return x;}
         set
         {x = value;}
      } // end property X
   
      public int Y
      {
         get
         {return y;}
         set
         {y = value;}
      } 
   
      // return string representation of Point
      public override string ToString()
      {return "[" + X + ", " + Y + "]";}
    } // end class Point
   ```
   The following class is the Derived class of class point
   ```c#
       public class Circle: Point
    {
       private double radius;
   
      // constructor
      public Circle( int xcircle, int ycircle, double radiuscircle )
         : base( xpoint, ypoint )
      {Radius = radiuscircle;
      Console.WriteLine("Circle constructor: {0}", this);}
   
      public double Radius
      {
         get
         {return radius;}
         set
         {radius = value;}
      }
      
      public double Diameter()
      {return Radius * 2;}
      
      public double Perimeter()
      {return Math.PI * Diameter();}
   
      
      public virtual double Area()
      {return Math.PI * Math.Pow( Radius, 2 );}
   
      // return string representation of Circle
      
      public override string ToString()
      {
      // using the tostring method with extra additions
         return "Center= " + base.ToString() +"; Radius = " + Radius;  // use property Radius 
      }
   } // end class Circle
   ```
   
  ### Constructors and Destructors in derived classes
  
   The constructor of a base class will be called implicitly or explicitly when Instantiating a derived class, this will cause a chain reaction when a base class is also a derived class.
   
   
   When a destructor is called, it executes its function and then invokes the derived class base class constructor.
   
   
   Let’s look at the code sample below to learn how to define a destructor.
   
   ``` c#
   // destructor inside the class point
   
      ~Point()
      {
         Console.WriteLine( "Point destructor: {0}", this );
      }    
   ```
   ```c#
   // destructor inside the class circle
      ~Circle()
      {
         Console.WriteLine( "Circle destructor: {0}", this );
      }
   ```   
   
   Example:
   
   ```c#
   static void Main( string[] args )
      {
         // instantiate objects
         Circle c = new Circle(6,8,4);  
      }
   ```
   The output is given as follows:
   ```c#
 point constructor: Center= [6, 8]; Radius = 0
Circle constructor: Center= [6, 8]; Radius = 4
Circle destructor: Center= [6, 8]; Radius = 4
Point destructor: Center= [6, 8]; Radius = 4

   ```
   
### Conclusion

In this tutorial, we have learned the importance of inheritance, how to define a base class and inherit its properties,
and understand the relationship between classes. however, it's just the start! We will learn more about inheritance in the upcoming tutorials.
Also, don't forget to test out the code to fully understand how it works.
