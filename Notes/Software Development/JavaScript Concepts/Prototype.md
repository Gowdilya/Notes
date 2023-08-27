
## The prototype chain
```js
const myObject = {
  city: "Madrid",
  greet() {
    console.log(`Greetings from ${this.city}`);
  },
};

myObject.greet(); // Greetings from Madrid

```
![[Screenshot 2023-08-08 at 2.55.36 PM.png]]