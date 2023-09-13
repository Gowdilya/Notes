 #OOP 
 Four key concepts of OOPs are [[Abstraction]], [[encapsulation]], [[Inheritance]], and [[Polymorphism]]. 

### Abstraction

Abstraction is a concept that allows you to define the essential characteristics of an object while hiding the unnecessary details. It focuses on what an object does rather than how it does it.
Use of Abstract classes, which have abstract methods(hides implementation detail) and normal methods(with implementation) or using Interface (only empty method signatures to hide all implementations detail).
```c#
public abstract class Shape
{
    public abstract double CalculateArea();
}
```

```c#
public interface IDrawable
{
    void Draw();
}
```

---

### Inheritance
Parent → Child, Child Inherits properties and methods of the parent
Shape→ Circle

```c#
public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}
```
---
### Polymorphism


==Allows objects of different classes to be treated as objects of a common base class or interface.==
Enables you to write more flexible and extensible code by providing a way for different classes to provide their own implementations for methods defined in a common interface or base class.
Polymorphism allows you to write code that can work with a variety of objects without knowing their specific types, and it is achieved through method overriding and interfaces. There are two main aspects of polymorphism in C#:


Method Overriding:
- Method overriding is a form of runtime polymorphism where a subclass provides a specific implementation for a method that is already defined in its superclass (base class).
- The base class method is marked with the `virtual` keyword, and the overriding method in the derived class is marked with the `override` keyword.
- When you call a method on an object, the method that is executed is determined by the actual type of the object at runtime.
``` c#
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows");
    }
}

```


Interfaces:

- Interfaces in C# provide a way to achieve polymorphism by defining a contract that a class must adhere to. A class can implement one or more interfaces.
- When a class implements an interface, it must provide implementations for all the methods defined in that interface.
- Objects of classes that implement the same interface can be treated interchangeably, allowing you to write code that works with a variety of objects regardless of their specific types.

Example:

```c#
public interface IDrawable
{
    void Draw();
}

public class Circle : IDrawable
{
    public void Draw()
    {
        Console.WriteLine("Drawing a circle");
    }
}

public class Rectangle : IDrawable
{
    public void Draw()
    {
        Console.WriteLine("Drawing a rectangle");
    }
}

```


C# (pronounced "C-sharp") is a modern, versatile, and object-oriented programming language developed by Microsoft. It has a rich set of features that make it a popular choice for developing a wide range of software applications, including desktop applications, web applications, mobile apps, and more. Here are some key features of C#:

1. **Garbage Collection (GC):**
    
    - One of the standout features of C# is its automatic memory management through garbage collection.
    - Garbage collection helps developers avoid memory leaks and simplifies memory management.
    - The .NET runtime automatically tracks and reclaims memory that is no longer in use, allowing developers to focus on writing code without worrying about explicit memory allocation and deallocation.
2. **Type Safety:**
    
    - C# is a statically typed language, which means that variables and objects must be declared with a specific type, and type safety is enforced at compile-time.
    - This helps catch type-related errors early in the development process, reducing the likelihood of runtime errors.
3. **Object-Oriented:**
    
    - C# is a fully object-oriented language, which means that everything in C# is an object, and it supports key object-oriented concepts like classes, objects, inheritance, encapsulation, and polymorphism.
4. **Managed Code:**
    
    - C# code is compiled into an intermediate language (IL) that runs on the .NET Common Language Runtime (CLR).
    - The CLR provides features such as automatic memory management (garbage collection), security, and cross-language integration.
5. **.NET Framework and .NET Core/.NET 5+**:
    
    - C# is often associated with the .NET ecosystem, which includes a vast class library for common tasks like file I/O, database access, and network communication.
    - With the introduction of .NET Core (now known as .NET 5 and later .NET 6, .NET 7, etc.), C# is also used for cross-platform development, allowing you to write code that runs on Windows, Linux, and macOS.
6. **Properties and Events:**
    
    - C# provides properties and events as language features to simplify the implementation of getter/setter methods and event handling.
7. **Delegates and Events:**
    
    - Delegates allow you to treat methods as first-class objects, enabling you to create dynamic method calls.
    - Events are a higher-level abstraction built on top of delegates and are commonly used for implementing the Observer pattern.
8. **LINQ (Language Integrated Query):**
    
    - LINQ is a powerful feature that allows developers to write SQL-like queries directly in C# code for querying collections, databases, XML, and other data sources.
9. **Asynchronous Programming:**
    
    - C# provides support for asynchronous programming through the `async` and `await` keywords, making it easier to write responsive and efficient code for I/O-bound and CPU-bound operations.
10. **Nullable Value Types:**
    
    - C# allows you to declare value types (e.g., `int`, `float`) as nullable using the `?` modifier, which is useful when dealing with data that might not always have a value.
11. **Exception Handling:**
    
    - C# has robust exception handling mechanisms with `try`, `catch`, `finally`, and `throw` keywords, making it easy to handle and propagate exceptions in your code.
12. **Attributes and Metadata:**
    
    - C# supports custom attributes that allow you to add metadata to your code, which can be used for reflection, code analysis, and various other purposes.
13. **Interoperability:**
    
    - C# provides mechanisms for interoperating with code written in other languages like C and C++ through Platform Invocation Services (P/Invoke) and COM Interoperability.

These features, along with the support and tools provided by the .NET ecosystem, make C# a robust and versatile language for modern software development. C# is widely used in various domains, from game development (with Unity) to web development (with ASP.NET) and enterprise applications.


Each of these HTTP methods serves a specific purpose in the RESTful architecture:

- GET: Retrieve data.
- POST: Create new resources or submit data for processing.
- PUT: Update existing resources or create them if they don't exist.
- DELETE: Remove resources.

By having these distinct methods, REST allows for a clear and standardized way to interact with resources, making it easier for clients and servers to communicate effectively. Different methods correspond to different operations that can be performed on resources, which helps maintain a clear and consistent API design.

While it's technically possible to use the HTTP POST method to perform updates (similar to what you would do with PUT), doing so goes against the principles of the REST architectural style and can lead to confusion and inconsistency in your API design. Here are several reasons why using POST for updates instead of PUT is discouraged:

1. **Idempotence:** One of the key principles of REST is idempotence, which means that making the same request multiple times should have the same effect as a single request. PUT is designed to be idempotent, meaning that if you send the same PUT request multiple times, it should result in the same state on the server. In contrast, POST requests are not guaranteed to be idempotent. They may have different outcomes when repeated, making them less predictable for updates.

1. **Client Expectations:** Developers and client applications often rely on the expected behavior of HTTP methods. When you use POST for updates instead of PUT, you break the expected conventions, potentially leading to confusion and errors in client applications.
    
2. **HTTP Status Codes:** HTTP provides specific status codes (e.g., 200 OK, 201 Created, 204 No Content) that have well-defined meanings for each HTTP method. Using POST for updates may lead to less clear status code usage, as it's typically associated with resource creation.


# JS
### let and const

`let` and `const` create block-scoped variables. When declared within a block, they are only accessible within that block. This behavior was demonstrated in our previous examples:

### var

Variables created with `var` are scoped to their nearest function or the global scope (which we will discuss shortly). They are not block scoped:



Scope refers to the part of a program where we can access a variable. JavaScript allows us to nest scopes, and variables declared in outer scopes are accessible from all inner ones. Variables can be globally-, module-, or block-scoped.

A closure is a function enclosed with references to the variables in its outer scope. Closures allow functions to maintain connections with outer variables, even outside the scope of the variables.


## Global and Module Scope in JavaScript

In addition to block scopes, variables can be scoped to the global and module scope.

In a web browser, the global scope is at the top level of a script. It is the root of the scope tree that we described earlier, and it contains all other scopes. Thus, creating a variable in the global scope makes it accessible in every scope:

```html
<script>
	const foo = "foo";
</script>
<script>
	console.log(foo); // "foo"
		
	function bar() {
		if (true) {
			console.log(foo);
		}
	}

	bar(); // "foo"
</script>
```

Each module also has its own scope. Variables declared at the module level are only available within that module – they are not global:


```javascript
function foo() {
	if (true) {
		var foo = "foo";
	}
	console.log(foo);
}

foo(); // "foo"
```