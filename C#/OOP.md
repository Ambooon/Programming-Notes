# Encapsulation
## Classes
Class are group of code that contains fields, property and methods. Class is like a blueprint. By instantiating the class you create an object. Object have the concrete values.

Class are reference type. Meaning if you pass class in another class. You are actually passing the reference of that class. So any changes in both class will reflect to one another. Also the equal operation for class are comparing their reference and not their value.
```csharp
MyClass class1 = new();
MyClass class2 = class1; // class1 and class2 are the same with just diff. name
```

Example of creating a class
```csharp
public class Student(string FirstName, string LastName, int Year)
{
	public string FirstName { get; } = FirstName;
	public string LastName { get; } = LastName;
	public int Year { get; } = Year;
	
	public void Introduce() {
		Console.WriteLine($"I am {FirstName} {LastName}.");
	}
}

```

## Structs
Structs are value type. Meaning if you pass it, it will copy the value of the struct and create a new copy. The equality for structs are they are compared by their value.
```csharp
public struct Coords(double X, double Y)
{
    public double X { get; } = X;
    public double Y { get; } = Y;

    public override string ToString() => $"({X}, {Y})";
}
```

## Records
Records are like both class and structs. They are reference type and immutable by default. They are value equality meaning when using equality operation they are compared in their actual values. You can inherit but only in records only. This is useful in data models that depends on value equality and objects that are immutable.
```csharp
public record Person(string FirstName, string LastName);

public static class Program
{
    public static void Main()
    {
        Person person = new("Nancy", "Davolio");
        Console.WriteLine(person);
        // output: Person { FirstName = Nancy, LastName = Davolio }
    }

}
```


# Access Modifiers

1. **Public** - Available to all
2. **Private** - Available only in the scope where it is declared
3. **Internal** - Available in the library
4. **Protected** - Available in inherited class
5. **Private Protected** (rare)
6. **Private Internal** (rare)

# Inheritance

## Abstract Class
Abstract class are use for inheritance. They act as a base class that you can inherit from. They can't be instantiated, only inherited.
```csharp
public abstract class Shape
{
    public abstract int GetArea();
}

public class Square : Shape
{
    private int _side;

    public Square(int n) => _side = n;

    // GetArea method is required to avoid a compile-time error.
    public override int GetArea() => _side * _side;

    static void Main()
    {
        var sq = new Square(12);
        Console.WriteLine($"Area of the square = {sq.GetArea()}");
    }
}
// Output: Area of the square = 144
```

Using the constructor of derived class
```csharp
public Cylinder(double r, double h): base(r, h) {}
```

## Interface
Interface is like a contract that the class should be implementing. In interface you just declare the things that the class should have. There is no implementation in the interface. The implementation will be up to the class that uses that interface. 

```csharp
public interface IShape
{
    double Area { get; }
    double Perimeter { get; }
    void Draw();
}

```

```csharp
public class Rectangle : IShape
{
    public double Width { get; }
    public double Height { get; }

    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }

    public double Area => Width * Height;

    public double Perimeter => 2 * (Width + Height);

    public void Draw()
    {
        Console.WriteLine($"Drawing a rectangle with width {Width} and height {Height}");
    }
}

```


# Polymorphism
## Abstract
There is no implementation in the abstract. This is for contract only that tells the subclass what it should implement. Can only be use in abstract classes

## Virtual
Virtual has default implementation. This keyword tell that the method or property can be override by subclass.

## Base class
The base keyword allows the subclass to call the base or derived methods and constructor.