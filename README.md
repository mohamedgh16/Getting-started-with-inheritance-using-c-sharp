# Getting-started-with-inheritance-using-c#

### Introduction

Inheritance is one of the most important concepts in object-oriented programming, it allows the definition of a class in terms of another class. Inheritance allows us to maintain and boost an application, it also provides the reusability of code functionality and gives better performance.

Classes are created by absorbing the functions and variables of an existing class, it then adds its own functions to enhance their capabilities, this class is called a derived class because it inherits the functions and variables from a base class. Objects of a derived class are objects of a base class, but not vice versa. 
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
 This is how you specify a class child derived from class father: `class child: father`.



### Protected members and Internal members
**Protected members** Can be accessed by base class or any class derived from it, on the other hand
**Internal members** Can only be accessed by a class declared within the same assembly.


### Relationship between Base classes and Derived classes

The base class constructor is the first thing to be called by a derived class, either explicitly or implicitly.
**Override** keyword is needed if a derived-class function overrides a base-class function,
But if a base class function is going to be overridden it must be declared **Virtual**.



The following example will calculate the area and perimeter of a circle using inheritance. 

in this piece of code, we will define two private point coordinates, then we will define a constructor that takes two integers from the main.

**Note** that Output statements use a reference (This) to implicitly call the ToString method.

```c#
    public class Point
    {
      private int x, y;
      
      public Point( int xpoint, int ypoint )
      {
         X = xpoint;
         Y = ypoint;
         Console.WriteLine("point constructor: {0}", this);}
  ```
  Here we define the set and get Accessors to access the private members of the class, then we will override the ToString method.
  
  **Note** that the ToString method will return a string representation of class Point.
  ```c#
      public int X
      {
         get
         {return x;}
         set
         {x = value;}
      } 
   
      public int Y
      {
         get
         {return y;}
         set
         {y = value;}
      } 
   
      public override string ToString()
      {return "[" + X + ", " + Y + "]";}
    } // end class Point
   ```
   The following class is the Derived class of class point.
   
   In class Circle, we don't need to define the point coordinates because they're already inherited as we can see `: base(xpoint,ypoint)`. 
   Now we define the radius of the circle the constructor and the Accessors.
   
   ```c#
       public class Circle: Point
    {
       private double radius;
   
      public Circle( int xpoint, int ypoint, double radiuscircle )
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
      ```
      
      Now we need to define the functions that will help us calculate the area and perimeter of the circle,
      then we will override the ToString method, just like we did in class Point.
     
      
      ```c#
      
      public double Diameter()
      {return Radius * 2;}
      
      public double Perimeter()
      {return Math.PI * Diameter();}
   
      
      public virtual double Area()
      {return Math.PI * Math.Pow( Radius, 2 );}
   
      // return string representation of Circle
      
      public override string ToString()
      {
      // using the ToString method with extra additions
         return "Center= " + base.ToString() +"; Radius = " + Radius;   
      }
   } // end class Circle
   ```
   Take a look at the following code:
   ```c#
   static void Main(string[] args)
        {
            Circle c = new Circle(6,8,4);

            Console.WriteLine("Area : " + c.Area());
            Console.WriteLine("Perimeter : " + c.Perimeter());
        }
   ```
   
   
   the output after execution:
   ```c#
   point constructor: Center= [6, 8]; Radius = 0
   Circle constructor: Center= [6, 8]; Radius = 4
   Area : 50.2654
   Perimeter : 25.1327
   ```
   
  ### Constructors and Destructors in derived classes
  
   The constructor of a base class will be called implicitly or explicitly when Instantiating a derived class,
   this will cause a chain reaction when a base class is also a derived class.
   
   
   When a destructor is called, it executes its function and then invokes the derived class base class constructor.
   
   
   Let’s look at the code sample below to learn how to define a destructor.
   
   **Note** that you need to include this piece of code inside the class Point.
   
   ``` c#
      ~Point()
      {
         Console.WriteLine( "Point destructor: {0}", this );
      }    
   ```
   
   **Note** that you need to include this piece of code inside the class Circle.
   
   ```c#
   // destructor inside the class circle
      ~Circle()
      {
         Console.WriteLine( "Circle destructor: {0}", this );
      }
   ```   
   
   This is an example of how constructors and destructors work:
   
   ```c#
   static void Main( string[] args )
      { 
         Circle c1 = new Circle(6,8,4); 
         Circle c2 = new Circle(16,18,8);
      }
   ```
   The output in order is given as follows:
   ```c#
point constructor: Center= [6, 8]; Radius = 0
Circle constructor: Center= [6, 8]; Radius = 4
point constructor: Center= [16, 18]; Radius = 0
Circle constructor: Center= [16, 18]; Radius = 8
Circle destructor: Center= [16, 18]; Radius = 8
Point destructor: Center= [16, 18]; Radius = 8
Circle destructor: Center= [6, 8]; Radius = 4
Point destructor: Center= [6, 8]; Radius = 4

   ```
   
### Conclusion

In this tutorial, we have learned the importance of inheritance, how to define a base class and inherit its properties,
and understand the relationship between classes. however, it's just the start! We will learn more about inheritance in the upcoming tutorials.
Also, don't forget to test out the code to fully understand how it works.
