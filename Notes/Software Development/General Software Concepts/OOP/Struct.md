In C#, `struct` is the [value type](https://www.tutorialsteacher.com/csharp/csharp-value-type-and-reference-type) data type that represents data structures. It can contain a parameterized constructor, static constructor, constants, fields, methods, properties, indexers, operators, events, and nested types.

`struct` can be used to hold small data values that do not require inheritance, e.g. coordinate points, key-value pairs, and complex data structure.


```c#
struct Coordinate
{
    public int x;
    public int y;
}
```

A `struct` object can be created with or without the `new` operator, same as primitive type variables.


```c#

struct Coordinate
{
    public int x;
    public int y;
}

Coordinate point;
Console.Write(point.x); // Compile time error  

point.x = 10;
point.y = 20;
Console.Write(point.x); //output: 10  
Console.Write(point.y); //output: 20 

```

A `struct` cannot contain a parameterless constructor. It can only contain parameterized constructors or a static constructor.

```c#
struct Coordinate
{
    public int x;
    public int y;

    public Coordinate(int x, int y)
    {
        this.x = x;
        this.y = y;
    }
}

Coordinate point = new Coordinate(10, 20);

Console.WriteLine(point.x); //output: 10  
Console.WriteLine(point.y); //output: 20  
```


```c#
struct Coordinate
{
    public int x { get; set; }
    public int y { get; set; }

    public void SetOrigin()
    {
        this.x = 0;
        this.y = 0;
    }
}

Coordinate point = Coordinate();
point.SetOrigin();

Console.WriteLine(point.x); //output: 0  
Console.WriteLine(point.y); //output: 0
```

# [[Static constructor]]

```c#
struct Coordinate
{
    public int x;
    public int y;

    public Coordinate(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public static Coordinate GetOrigin()
    {
        return new Coordinate();
    }
}

Coordinate point = Coordinate.GetOrigin();

Console.WriteLine(point.x); //output: 0  
Console.WriteLine(point.y); //output: 0  
```