# Getting-started-with-inheritance-using-c#

### Introduction

Inheritance is one of the most important concepts in object-oriented programming, it allows the definition of a class in terms of another class, it also allows us to maintain and boost an application.

Classes are created by absorbing the methods and variables of an existing class, it then adds its own methods to enhance its capabilities. This class is called a derived class because it inherits methods and variables from a base class. Objects of a derived class are objects of a base class, but not vice versa. A derived class can only access non-private base class members unless it inherits accessor functions.

### Prerequisites
Before we dive right in, the reader would need to have the following:

- A basic understanding of C# programming language. 

- A basic understanding of how Classes work.

### Base classes and Derived classes

**Base** classes are used to generate derived classes that inherit the properties of the base class.

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
Can be accessed by base class or any class derived from that base class.

#### Internel members
Can only be accessed by classes declared in the same assembly.

### Relationship between Base classes and Derived classes

The first thing a derived class does is call its base class constructor, either explicitly or implicitly.

- **Override** keyword is needed if a derived-class method overrides a base-class method

- If a base class method is going to be overridden it must be declared **Virtual**

The following example will calculate the area and perimeter of a circle using inheritance: 

```c#
    public class Point
    {
       // point coordinate
      private int x, y;
      
      // constructor
      public Point( int xValue, int yValue )
      { // implicit call to Object constructor occurs here
         X = xValue;
         Y = yValue;}
  
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
       public class Circle : Point
    {
       private double radius;
   
      // constructor
      public Circle4( int xValue, int yValue, double radiusValue )
         : base( xValue, yValue )
      {Radius = radiusValue;}
   
      public double Radius
      {
         get
         {return radius;}
         set
         {radius = value;}
      }
      
      public double Diameter()
      {return Radius * 2;}
      
      public double Circumference()
      {return Math.PI * Diameter();}
   
      
      public virtual double Area()
      {return Math.PI * Math.Pow( Radius, 2 );}
   
      // return string representation of Circle
      
      public override string ToString()
      {
      // use base reference to return Point string representation
         return "Center= " + base.ToString() +"; Radius = " + Radius;  // use property Radius 
      }
   } // end class Circle
   ```
   
  ### Constructors and Destructors in derived classes
  
   Instantiating a derived class causes the base class constructor to be called implicitly or explicitly, can cause a chain reaction when a base class is also a derived class.
   
   
   When a destructor is called, it performs its task and then invokes the derived class base class constructor.
   
   
   Let’s look at the code sample below to learn how to define a destructor.
   
   ``` c#
   //Note that Output statements use a reference (This) to implicitly call the ToString method
   // destructor inside the class point
   
      ~Point()
      {
         Console.WriteLine( "Point4 destructor: {0}", this );
      }    
   ```
   ```c#
   // destructor inside the class circle
      ~Circle()
      {
         Console.WriteLine( "Circle5 destructor: {0}", this );
      }
   ```   
   
   Example:
   
   ```c#
   static void Main( string[] args )
      {
         C circle1, circle2;
   
         // instantiate objects
         circle1 = new C( 72, 29, 4.5 );
         circle2 = new C( 5, 5, 10 );
      }
   ```
   The output is given as follows:
   ```c#
   Point4 constructor: Center = [72, 29]; Radius = 0
Circle5 constructor: Center = [72, 29]; Radius = 4.5
Point4 constructor: Center = [5, 5]; Radius = 0
Circle5 constructor: Center = [5, 5]; Radius = 10
 
Circle5 destructor: Center = [5, 5]; Radius = 10
Point4 destructor: Center = [5, 5]; Radius = 10
Circle5 destructor: Center = [72, 29]; Radius = 4.5
Point4 destructor: Center = [72, 29]; Radius = 4.5

   ```
   
### Conclusion

In this tutorial, we have learned the importance of inheritance, how to define a base class and inherit its properties,
and understand the relationship between classes. however, it's just the start! We will learn more about inheritance in the upcoming tutorials.
Also, don't forget to test out the code to fully understand how it works.
