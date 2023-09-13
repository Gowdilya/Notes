Encapsulation is defined as **the wrapping up of data under a single unit**. It is the mechanism that binds together code and the data it manipulates. In a different way, encapsulation is a protective shield that prevents the data from being accessed by the code outside this shield.![[Screenshot 2023-09-08 at 8.15.28 AM.png]]

```c#
// C# program to illustrate encapsulation
using System;

public class DemoEncap {

	// private variables declared
	// these can only be accessed by
	// public methods of class
	private String studentName;
	private int studentAge;

	// using accessors to get and
	// set the value of studentName
	public String Name
	{

		get { return studentName; }

		set { studentName = value; }
	}

	// using accessors to get and
	// set the value of studentAge
	public int Age
	{

		get { return studentAge; }

		set { studentAge = value; }
	}
}

// Driver Class
class GFG {

	// Main Method
	static public void Main()
	{

		// creating object
		DemoEncap obj = new DemoEncap();

		// calls set accessor of the property Name,
		// and pass "Ankita" as value of the
		// standard field 'value'
		obj.Name = "
		Ankita& quot;
		;

		// calls set accessor of the property Age,
		// and pass "21" as value of the
		// standard field 'value'
		obj.Age = 21;

		// Displaying values of the variables
		Console.WriteLine(" Name : " + obj.Name);
		Console.WriteLine(" Age : " + obj.Age);
	}
}

```

### **Advantages of Encapsulation:**

- **Data Hiding:** The user will have no idea about the inner implementation of the class. It will not be visible to the user that how the class is stored values in the variables. He only knows that we are passing the values to accessors and variables are getting initialized to that value.
- **Increased Flexibility:** We can make the variables of the class as read-only or write-only depending on our requirement. If we wish to make the variables as read-only then we have to only use Get Accessor in the code. If we wish to make the variables as write-only then we have to only use Set Accessor.
- **Reusability:** Encapsulation also improves the re-usability and easy to change with new requirements.
- **Testing code is easy:** Encapsulated code is easy to test for unit testing.

Encapsulation is a fundamental concept in object-oriented programming (OOP) that refers to the bundling of data and the methods that operate on that data within a single unit. In C#, this is typically achieved through the use of classes.

The idea behind encapsulation is to keep the implementation details of a class hidden from the outside world, and to only expose a public interface that allows users to interact with the class in a controlled and safe manner. This helps to promote modularity, maintainability, and flexibility in the design of software systems.

```C#
public class BankAccount {
	private decimal balance;

	public BankAccount(decimal initialBalance)
	{
		balance = initialBalance;
	}

	public void Deposit(decimal amount)
	{
		balance += amount;
	}

	public void Withdraw(decimal amount)
	{
		if (balance >= amount) {
			balance -= amount;
		}
		else {
			Console.WriteLine("Insufficient funds.");
		}
	}

	public decimal GetBalance() { return balance; }
}

class Program {
	static void Main(string[] args)
	{
		BankAccount myAccount = new BankAccount(1000);

		myAccount.Deposit(500);
		Console.WriteLine("Balance: "
						+ myAccount.GetBalance());

		myAccount.Withdraw(1200);
		Console.WriteLine("Balance: "
						+ myAccount.GetBalance());
	}
}

```