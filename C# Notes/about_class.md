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