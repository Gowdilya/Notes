
#CSharp #OOP

```c#
class SimpleClass
{
    // Static variable that must be initialized at run time.
    static readonly long baseline;

    // Static constructor is called at most one time, before any
    // instance constructor is invoked or member is accessed.
    static SimpleClass()
    {
        baseline = DateTime.Now.Ticks;
    }
}
```

- A static constructor doesn't take access modifiers or have parameters.
- A class or struct can only have one static constructor.
- Static constructors cannot be inherited or overloaded.
- A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR). ==It is invoked automatically.==
- The user has no control on when the static constructor is executed in the program.
- A static constructor is called automatically. It initializes the [class](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/class) before the first instance is created or any static members declared in that class (not its base classes) are referenced. A static constructor runs before an instance constructor. If static field variable initializers are present in the class of the static constructor, they're executed in the textual order in which they appear in the class declaration. The initializers run immediately prior to the execution of the static constructor.
- If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/default-values).
- If a static constructor throws an exception, the runtime doesn't invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain. Most commonly, a [TypeInitializationException](https://learn.microsoft.com/en-us/dotnet/api/system.typeinitializationexception) exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor. For static constructors that aren't explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.
- The presence of a static constructor prevents the addition of the [BeforeFieldInit](https://learn.microsoft.com/en-us/dotnet/api/system.reflection.typeattributes#system-reflection-typeattributes-beforefieldinit) type attribute. This limits runtime optimization.
- A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor. When an explicit static constructor isn't required, initialize static fields at declaration rather than through a static constructor for better runtime optimization.
- The runtime calls a static constructor no more than once in a single application domain. That call is made in a locked region based on the specific type of the class. No additional locking mechanisms are needed in the body of a static constructor. To avoid the risk of deadlocks, don't block the current thread in static constructors and initializers. For example, don't wait on tasks, threads, wait handles or events, don't acquire locks, and don't execute blocking parallel operations such as parallel loops, `Parallel.Invoke` and Parallel LINQ queries.

Declaring a static class documents your intent for that class to be a collection of static functionality, and anyone adding instance members will get a compilation error.

A non-static class with static members usually indicates that the class is designed to be instantiated at some point. Static methods of these classes usually do one of two things:

1. Provide a factory method for creating an instance of that type;
2. Provide helper functionality that does not require an instance of the type;

Also, as mentioned already, extension methods can only be declared on a static class.