#SOLID #OOP #concept
https://stackify.com/solid-design-principles/
https://www.youtube.com/watch?v=vE74gnv4VlY&t=12s

# "Single Responsibility" Principle
"There should never be more than one reason for a [[class]] to change." The more responsibilities your class has, the more often you need to change it. If your class implements multiple responsibilities, they are no longer independent of each other. Easy to Understand, Easy to validate.

# "Open-closed" Principle
“Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.” 

Write your code so that you will be able to add new functionality without changing the existing code. That prevents situations in which a change to one of your classes also requires you to adapt all depending classes.

Inheritance introduces tight coupling if the subclasses depend on implementation details of their parent class.
Redefined from Open/Closed Principle to the [Polymorphic](https://stackify.com/oop-concept-polymorphism/) Open/Closed
It uses interfaces instead of superclasses to allow different implementations which you can easily substitute without changing the code that uses them. The interfaces are closed for modifications, and you can provide new implementations to extend the functionality of your software.

# "Liskov Substitution" Principle
#Liskov 

==Watch the video to understand how the Liskov principle is violated!==
[Web Dev Simplified - Liskov Substitution](https://www.youtube.com/watch?v=dJQMqNOC4Pc)
#Video

==Substitutability: if S is a subtype of T, then objects of type T may be replaced by objects of type S.==

"Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it."

If square is a subclass of rectangle, then anywhere rectangle is used we can use square.
**ECMAScript 2015**, also known as [[ES6]], introduced JavaScript Classes.

Example of Failed Liskov Principle:
```js
class Rectangle {
	constructor(width, height){
		this.width = width
		this.height = height
	}

	setWidth(width){
		this.width = width
	}

	setHeight(height){
		this.height = height
	}
	
	area(){
		return this.width * this.height
	}
}

class Square extends Rectangle {
	setWidth(width){
		this.width = width
		this.height = width
	}
	setHeight(height){
		this.width = height
		this.height = height
	}
}

function increaseRectangleWidth(rectangle){
	rectangle.setWidth(rectangle.width + 1)
}

const square = new Square(5,5);
const rectangle = new Rectangle(5,5);

increaseRectangleWidth(square);
increaseRectangleWidth(rectangle);

console.log(rectangle.area());//30
console.log(square.area());//36

```
The Above example fails Liskov since the area is not the same.

Another Instance of it not working below...
```js
class Bird(){
	fly(){
		console.log('I can fly')
	}
}

class Duck extends Birds {
	quack(){
		console.log('I can quack');
	}
}
class Penguin extends Bird{
	fly(){
	throw new Error('Cannot fly')
	}
	swim(){
		console.log("I can swim");
	}
}

function makeBirdFly(bird){
 bird.fly()
}
const duck = new Duck()
const penguin = new Penguin()

makeBirdFly(duck)
makeBirdFly(penguin)
```
![[Screenshot 2023-07-28 at 4.45.36 PM.png]]
According to Liskov every subclass of the Bird class should make the function work properly. But in this case the Penguin doesn't so this fails Liskov's principle. But the duck passes Liskov's substitution principle.


## Fix to ensure Liskov
```js
class FlyingBird(){
	fly(){
		console.log('I can fly')
	}
}

class SwimmingBird(){
	swim(){
		console.log("I can swim");
	}
}


class Duck extends FlyingBirds {
	quack(){
		console.log('I can quack');
	}
}
class Penguin extends SwimmingBird{
	fly(){
	throw new Error('Cannot fly')
	}
	
}

function makeFlyingBirdFly(bird){
 bird.fly()
}

function makeSwimmingBirdFly(bird){
 bird.swim()
}
const duck = new Duck()
const penguin = new Penguin()

makeBirdFly(duck)
makeBirdFly(penguin)
```
![[Screenshot 2023-07-28 at 4.50.53 PM.png]]


A problem with the above example is that a duck can also swim... and inheritance won't solve this issue. We may need [["Composition" vs Inheritance]]!

# "Interface Segregation" Principle
"Clients should not be forced to depend upon interfaces that they do not use."

# Dependency inversion  Principle

"Depend upon abstractions, [not] concretions."