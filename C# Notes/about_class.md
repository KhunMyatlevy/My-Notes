# Initialization

In programming, **initialization** refers to the process of assigning an initial value to a variable or object at the time of its creation. This ensures that the variable or object starts in a well-defined state before it is used. The method of initialization can vary depending on the programming language and the data type involved. For example, in languages like C++, variables can be initialized using constructors, while in languages like Python, initialization can occur through direct assignment. Proper initialization is crucial to prevent undefined behavior and to ensure that programs operate as intended.

---

# Fields in a Class

In object-oriented programming, **fields** (also known as **attributes**, **member variables**, or **data members**) are variables defined within a class that hold data or state about an object. They represent the properties or characteristics of an object and are used to store information specific to that object. Fields can be of various data types, including primitive types (e.g., integers, strings) and complex types (e.g., other objects).

**Example in C#:**

```csharp
public class Person
{
    // Field (attribute)
    private string name;

    // Constructor
    public Person(string name)
    {
        this.name = name;
    }

    // Getter method
    public string GetName()
    {
        return name;
    }
}
```

---

# Constructor in a Class

A constructor is a special method that is automatically called when an object is created. Its primary role is to initialize the object's fields to ensure it's in a valid state. Constructors can accept parameters to set initial values and can be overloaded to provide different ways of initializing objects.

### Key Points:
- Same name as the class.
- No return type.
- Can take parameters to set initial values.

### Example in C#:

```csharp
public class Person
{
    private string name;
    private int age;

    // Constructor with parameters
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    public string GetName() => name;
    public int GetAge() => age;
}
```

---

## Property

When fields are private, we use properties to access them. Properties allow controlled access to the field, using get to retrieve its value and set to assign a new value.

### Example in C#:

```csharp
public class Person
{
    private string name;

    // Property to access the private field
    public string Name
    {
        get { return name; }
        set { name = value; }
    }
}
```

---

## Static Method

A static method in a class belongs to the class itself, not to any specific object of that class. This means you can call a static method without creating an instance (object) of the class.

### Example in C#:

```csharp
public class MathOperations
{
    // Static method
    public static int Add(int a, int b)
    {
        return a + b;
    }
}

class Program
{
    static void Main()
    {
        // Calling the static method without creating an object
        int result = MathOperations.Add(5, 10);
        Console.WriteLine("The sum is: " + result);
    }
}
```

---

## Overloaded Method

Method Overloading in C# allows multiple methods with the same name but different parameters (type or number) within the same class.

### Key Points:
- Overloaded methods must differ by parameters (type, number, or both).
- Return type doesn’t affect overloading.
- It improves code readability by using the same method name for similar tasks.

### Example in C#:

```csharp
public class Calculator
{
    // Overloaded method to add integers
    public int Add(int a, int b)
    {
        return a + b;
    }

    // Overloaded method to add doubles
    public double Add(double a, double b)
    {
        return a + b;
    }
}

class Program
{
    static void Main()
    {
        Calculator calc = new Calculator();
        Console.WriteLine(calc.Add(5, 10));      // Calls Add(int, int)
        Console.WriteLine(calc.Add(5.5, 10.5));  // Calls Add(double, double)
    }
}
```

---

## Constructor Overloading

Constructor Overloading in C# allows defining multiple constructors with the same name (the class name) but different parameters (type or number).

### Key Points:
- Overloaded constructors must differ by parameters (type, number, or both).
- It allows initializing an object in different ways based on the passed arguments.
- The return type is always void (implicitly), and it's used to initialize the object’s fields.

### Example in C#:

```csharp
public class Person
{
    private string name;
    private int age;

    // Constructor with name and age
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // Overloaded constructor with only name
    public Person(string name)
    {
        this.name = name;
        this.age = 0;  // Default age
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {name}, Age: {age}");
    }
}

class Program
{
    static void Main()
    {
        Person person1 = new Person("John", 30);
        person1.DisplayInfo();  // Name: John, Age: 30

        Person person2 = new Person("Alice");
        person2.DisplayInfo();  // Name: Alice, Age: 0
    }
}
```

---

## Inheritance

Inheritance in C# allows a class (child class) to inherit fields, properties, methods, and other members from another class (parent class), enabling code reuse and creating a relationship between the classes.

### Key Points:
- Base Class: The class whose members are inherited by other classes.
- Derived Class: The class that inherits members from the base class.
- A derived class can add its own members or override base class methods.
- The base keyword is used to access members of the parent class.

### Example in C#:

```csharp
public class Animal
{
    public string Name { get; set; }

    public void Eat()
    {
        Console.WriteLine("Eating...");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking...");
    }
}

class Program
{
    static void Main()
    {
        Dog dog = new Dog();
        dog.Name = "Buddy";
        dog.Eat();   // Inherited method from Animal class
        dog.Bark();  // Method of Dog class
        Console.WriteLine($"Name: {dog.Name}");
    }
}
```

---

## Abstract Class

An abstract class is a class that you cannot create objects from. It is meant to be inherited by other classes, which can then use its methods and properties. It may also have methods without a body (abstract methods), which must be defined in the classes that inherit it.

### Example in C#:

```csharp
public abstract class Animal
{
    public string Name { get; set; }

    // Abstract method (doesn't have a body)
    public abstract void Speak();
}

public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Woof!");
    }
}

class Program
{
    static void Main()
    {
        // Cannot create an object of Animal class directly
        // Animal animal = new Animal(); // This will give an error

        Dog dog = new Dog();
        dog.Name = "Buddy";
        dog.Speak();  // Output: Woof!
        Console.WriteLine($"Name: {dog.Name}");
    }
}
```

---

## Array of Objects

An array of objects is an array that stores multiple objects of a class. First, you create the array to hold the objects, and then you create instances (objects) of a class to store in that array. All the objects in the array will be of the same class.

### Example in C#:
```csharp
public class Car
{
    public string Model { get; set; }
    public int Year { get; set; }
}

class Program
{
    static void Main()
    {
        // Create an array of Car objects
        Car[] cars = new Car[2];

        // Create objects and assign them to the array
        cars[0] = new Car() { Model = "Toyota", Year = 2020 };
        cars[1] = new Car() { Model = "Honda", Year = 2022 };

        // Accessing objects in the array
        Console.WriteLine($"Car 1: {cars[0].Model}, Year: {cars[0].Year}");
        Console.WriteLine($"Car 2: {cars[1].Model}, Year: {cars[1].Year}");
    }
}
```

---

### Example: Using Object as an Argument in C#

Here’s an example of using an object as an argument in C# to change the color of a car:

```csharp
public class Car
{
    public string Model { get; set; }
    public string Color { get; set; }

    public Car(string model, string color)
    {
        Model = model;
        Color = color;
    }
}

class Program
{
    // Function that takes a Car object as an argument and changes its color
    static void ChangeCarColor(Car car, string newColor)
    {
        car.Color = newColor;
    }

    static void Main()
    {
        // Create a Car object
        Car myCar = new Car("Toyota", "Red");

        // Display original color
        Console.WriteLine($"Original Color: {myCar.Color}");

        // Change the color using the function
        ChangeCarColor(myCar, "Blue");

        // Display the new color
        Console.WriteLine($"New Color: {myCar.Color}");
    }
}
```

---

## Method Overriding

Method overriding provides a new version of a method inherited from a parent class. The method in the child class has the same signature as the one in the parent class, but the child class can change its behavior.

### Example in C#:

```csharp
using System;

public class Animal
{
    // Virtual method that can be overridden
    public virtual void MakeSound()
    {
        Console.WriteLine("Some animal sound");
    }
}

public class Dog : Animal
{
    // Overriding the MakeSound method
    public override void MakeSound()
    {
        Console.WriteLine("Bark");
    }
}

class Program
{
    static void Main()
    {
        Animal myAnimal = new Animal();
        myAnimal.MakeSound();  // Outputs: Some animal sound

        Dog myDog = new Dog();
        myDog.MakeSound();  // Outputs: Bark

        Animal animalDog = new Dog();
        animalDog.MakeSound();  // Outputs: Bark (due to method overriding)
    }
}
```

---

### Polymorphism and Method Overriding Example

This example demonstrates Polymorphism and Method Overriding in C# using a Vehicle class and its derived classes Car, Boat, and Bicycle. Method overwriting is way to achieve Polymorphism.

```csharp
using System;

public class Vehicle
{
    // Base class method, marked virtual so it can be overridden
    public virtual void Move()
    {
        Console.WriteLine("Vehicle is moving");
    }
}

public class Car : Vehicle
{
    // Method overriding in the Car class
    public override void Move()
    {
        Console.WriteLine("Car is driving");
    }
}

public class Boat : Vehicle
{
    // Method overriding in the Boat class
    public override void Move()
    {
        Console.WriteLine("Boat is sailing");
    }
}

public class Bicycle : Vehicle
{
    // Method overriding in the Bicycle class
    public override void Move()
    {
        Console.WriteLine("Bicycle is pedaling");
    }
}

class Program
{
    static void Main()
    {
        Vehicle myVehicle = new Vehicle();   // Vehicle object
        Vehicle myCar = new Car();           // Car object (using Vehicle type)
        Vehicle myBoat = new Boat();         // Boat object (using Vehicle type)
        Vehicle myBicycle = new Bicycle();  // Bicycle object (using Vehicle type)

        myVehicle.Move();   // Outputs: Vehicle is moving
        myCar.Move();       // Outputs: Car is driving
        myBoat.Move();      // Outputs: Boat is sailing
        myBicycle.Move();   // Outputs: Bicycle is pedaling
    }
}
```

---

### Interface in a Class

When a class inherits from (or implements) an interface in C#, it must implement all the methods and properties defined by that interface.

In simpler terms:

- An interface defines what methods and properties a class should have, but not how they work.
- A class that inherits from an interface must provide the actual code (implementation) for those methods and properties.

If the class doesn't implement all the methods and properties from the interface, the compiler will throw an error.

Here's a quick example:

```csharp
public interface IAnimal
{
    void Speak();
    string Name { get; set; }
}

public class Dog : IAnimal
{
    public string Name { get; set; }

    public void Speak() 
    {
        Console.WriteLine("Bark!");
    }
}

class Program
{
    static void Main()
    {
        IAnimal myDog = new Dog();
        myDog.Speak();  // Outputs: Bark!
    }
}
```

---

### Simple Example of a List in C#

Here's a simple example of using a List in C#:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Create a list of integers
        List<int> numbers = new List<int>();

        // Add items to the list
        numbers.Add(10);
        numbers.Add(20);
        numbers.Add(30);

        // Access and print items from the list
        Console.WriteLine("List items:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }

        // Remove an item from the list
        numbers.Remove(20);

        // Print list after removal
        Console.WriteLine("\nAfter removal:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }
    }
}
```

---

### Polymorphism and Lists in C#

With polymorphism, you can store objects from different classes, including their subclasses, in the same list, as long as they inherit from a common base class or implement the same interface.

### Example with Polymorphism:

```csharp
using System;
using System.Collections.Generic;

public class Vehicle
{
    public string Name { get; set; }
}

public class Car : Vehicle
{
    public int Wheels { get; set; }
}

public class Boat : Vehicle
{
    public int Sails { get; set; }
}

public class ElectricCar : Car
{
    public int BatteryCapacity { get; set; }
}

class Program
{
    static void Main()
    {
        // List of Vehicle objects, but can hold objects of Car, Boat, and ElectricCar
        List<Vehicle> vehicles = new List<Vehicle>();

        // Add objects of different classes, including subclasses
        vehicles.Add(new Car() { Name = "Sedan", Wheels = 4 });
        vehicles.Add(new Boat() { Name = "Yacht", Sails = 3 });
        vehicles.Add(new ElectricCar() { Name = "Tesla", Wheels = 4, BatteryCapacity = 100 });

        // Print out the details
        foreach (var vehicle in vehicles)
        {
            Console.WriteLine($"Vehicle: {vehicle.Name}");
        }
    }
}
```

---

### Auto-Implemented Properties

In C#, auto-implemented properties allow you to quickly define properties without having to explicitly create a backing field. The compiler automatically provides the backing field for the property.

#### Example:

```csharp
public class Car
{
    // Auto-implemented property
    public string Model { get; set; }
    public string Color { get; set; }

    public Car(string model, string color)
    {
        Model = model;
        Color = color;
    }
}

class Program
{
    static void Main()
    {
        // Create an object of Car class
        Car myCar = new Car("Toyota", "Red");

        // Accessing auto-implemented properties
        Console.WriteLine($"Car Model: {myCar.Model}, Color: {myCar.Color}");
    }
}
```