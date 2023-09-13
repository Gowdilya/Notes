#SOLID #Abstraction
  

The dependency inversion principle states that **high-level modules should depend on abstractions rather than low-level modules**. This helps to decouple the components in your application and can make your code more flexible, maintainable, and easier to test.
Also called Facade pattern/Adapter pattern


https://www.youtube.com/watch?v=9oHY5TllWaU
![[Screenshot 2023-09-07 at 7.47.30 PM.png]]
In the above example store depends on stripe API for payment process.
Might use stripe.pay() for example within store application.
Having code tightly coupled like this is problematic. Harder to test, since we can't test it without the Stripe API

A better way is to use Dependency Inversion Principle.
![[Screenshot 2023-09-07 at 7.49.19 PM.png]]
![[Screenshot 2023-09-07 at 9.13.15 PM.png]]
PaymentProcessor.checkCreditCard()
PaymentProcessor.pay()

Stripe is the specific implementation


# Example Store using Stripe
```js
class Store{
	constructor(user){
		this.stripe = new Stripe(user)
	}
	purchaseBike(quantity){
		this.stripe.makePayments(200 * quantity * 100)
	}
	purchaseHelmet(quantity){
		this.stripe.makePayment(15 * quantity * 100)
	}
}

class Stripe {
	constructor(user){
		this.user = user
		//this.stripe = new Stripe(user)
		this.payPal = new Paypal()
	}
	makePayment(amountInCents){
	console.log(`${this.user} made payment of $${amountInCents/100} with Stripe`)
	}
}
class Paypa{
	 makePayment(user, amountInDollars){
		 console.log(`${user} made payment of $${amountInDollars} with Paypal`)
	 }
}

const store = new Store('John')
store.purchaseBike(2)
store.purchaseHelmet(2)
```

# Store using Paypal api
```js
class Store{
	constructor(user){
		this.user = user
	}
	purchaseBike(quantity){
	this.paypal.makePayment(this.user, 200 * quantity)
		//this.stripe.makePayments(200 * quantity * 100)
	}
	purchaseHelmet(quantity){
		this.paypal.makePayment(this.user, 15 * quantity)
		//this.stripe.makePayment(15 * quantity * 100)
	}
}

class Stripe {
	constructor(user){
		this.user = user
	}
	makePayment(amountInCents){
	console.log(`${this.user} made payment of $${amountInCents/100} with Stripe`)
	}
}
class Paypa{
	 makePayment(user, amountInDollars){
		 console.log(`${user} made payment of $${amountInDollars} with Paypal`)
	 }
}

const store = new Store('John')
store.purchaseBike(2)
store.purchaseHelmet(2)
```

# Create intermediate api: Payment processor


```js
class Store{
	constructor(paymentProcessor){
		this.paymentProcessor = paymentProcessor
	}
	purchaseBike(quantity){
		this.paymentProcessor.pay( 200 * quantity)
	}
	purchaseHelmet(quantity){
		this.paymentProcessor.pay( 15 * quantity)
	}
}

class StripePaymentProcessor{
	constructor(user){
		this.stripe = new Stripe(user);
	}
	pay(amountInDollars){
		this.stripe.makePayment(amountInDollars * 100)
	}
}

class payPalPaymentProcessor{
	constructor(user){
		this.payPal = new PayPal(user);
	}
	pay(amountInDollars){
		this.payPal#SOL
		.makePayment(amountInDollars * 100)
	}
}

class Stripe {
	constructor(user){
		this.user = user
	}
	makePayment(amountInCents){
	console.log(`${this.user} made payment of $${amountInCents/100} with Stripe`)
	}
}
class Paypa{
	 makePayment(user, amountInDollars){
		 console.log(`${user} made payment of $${amountInDollars} with Paypal`)
	 }
}

const store = new Store(new StripePaymentProcessor('john'))
store.purchaseBike(2)
store.purchaseHelmet(2)
```