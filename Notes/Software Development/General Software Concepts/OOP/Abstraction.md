

Abstraction:

Abstraction is a concept that allows you to define the essential characteristics of an object while hiding the unnecessary details. It focuses on what an object does rather than how it does it.

In C#, abstraction is primarily achieved through abstract classes and interfaces:

- Abstract classes: An abstract class is a class that cannot be instantiated on its own; it serves as a blueprint for other classes. Abstract classes can have both abstract (unimplemented) and concrete (implemented) methods. Subclasses (derived classes) are required to implement the abstract methods defined in the abstract class.

csharpCopy code

`public abstract class Shape {     public abstract double CalculateArea(); }`

- Interfaces: An interface defines a contract that a class must adhere to. It consists of method signatures but no method implementations. Classes can implement one or more interfaces, providing the required method implementations.

csharpCopy code

`public interface IDrawable {     void Draw(); }`

Abstraction promotes code reusability, flexibility, and helps in achieving a clean and organized codebase by enforcing certain behavior in derived classes.
- hide common data

Through the process of abstraction, a programmer hides all but the relevant data about an object in order to reduce complexity and increase efficiency.
![[Screenshot 2023-09-08 at 8.02.41 AM.png]]

```c#
abstract class MobilePhone { 
	public void Calling(); 
	public void SendSMS();
} 
public class Nokia1400: MobilePhone {} 

public class Nokia2700: MobilePhone {
	public void FMRadio(); 
	public void MP3(); 
	public void Camera();
} 
public class BlackBerry: MobilePhone { 
	public void FMRadio();
	public void MP3(); 
	public void Camera(); 
	public void Recording(); 
	public void ReadAndSendEmails();
}
```

**Example**

If somebody in your college tells you to fill in an application form, you will provide your details, like name, address, date of birth, which semester, the percentage you have, etcetera.

If some doctor gives you an application, you will provide the details, like name, address, date of birth, blood group, height, and weight.

See in the preceding example what is in common?

==Age, name, and address, so you can create a class that consists of the common data. That is called an abstract class.

That class is not complete, and other classes can inherit it.==