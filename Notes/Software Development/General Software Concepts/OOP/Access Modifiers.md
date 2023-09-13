
|   |   |
|---|---|
|`public`|The code is accessible for all classes|
|`private`|The code is only accessible within the same class|
|`protected`|The code is accessible within the same class, or in a class that is inherited from that class. You will learn more about [inheritance](https://www.w3schools.com/cs/cs_inheritance.php) in a later chapter|
|`internal`|The code is only accessible within its own assembly, but not from another assembly. You will learn more about this in a later chapter|


There's also two combinations: `protected internal` and `private protected`.

## Private Modifier

If you declare a field with a `private` access modifier, it can only be accessed within the same class:

### Example

```c#
class Car
{
  private string model = "Mustang";    
  static void Main(string[] args)`
  {
    Car myObj = new Car();     
    Console.WriteLine(myObj.model);`
  }
}
```