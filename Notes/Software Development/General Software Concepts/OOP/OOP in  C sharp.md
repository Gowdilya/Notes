 #OOP 
 Four key concepts of OOPs are [[Abstraction]], [[encapsulation]], [[Inheritance]], and polymorphism. Here learn how to implement OOP concepts in C# and .NET.
Here are the key features of OOP:

-  ==programs are organized around objects and data rather than action and logic.==
- decomposing a problem into many entities called objects and then building data and functions around these objects. ==
- A ==class ==is the core to C#.
==- ==In OOP languages, creating a class for representing data is mandatory.====
- ==A class is a blueprint of an object that contains variables for storing data and functions to perform operations on the data.==
- A ==class will not occupy any memory space; hence, it is only a logical representation of data.==

## Object

1. The software is divided into several small units called objects. The data and functions are built around these objects.
2. ==An object's data can be accessed only by the functions associated with that object.==
3. ==The functions of one object can access the functions of another object.==

Objects are the basic run-time entities of an object-oriented system. They may represent a person, a place, or any item the program must handle.

- "An object is a software bundle of related variables and methods."
- "An object is an instance of a class."

![[Screenshot 2023-09-07 at 11.16.07 PM.png]]

# Class
will not occupy any memory space.

Hence to work with the data represented by the class, you must create a variable for the class, which is called an object.
### new keyword
object is created using the new operator, memory is allocated for the class in a heap, the object is called an instance, and its starting address will be stored in the object in stack memory.

- When an object is created without the new operator, memory will not be allocated in a heap; in other words, an instance will not be created, and the object in the stack will contain the value **null**.
- When an object contains null, it is impossible to access the class members using that object.

The key concepts of OOPs are 

1. [[Abstraction]]
2. Encapsulation
3. Inheritance
4. Polymorphism
