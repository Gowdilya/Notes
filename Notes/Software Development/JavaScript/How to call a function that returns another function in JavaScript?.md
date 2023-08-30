
```js
let outerFunction = function() {
    return function() {
       console.log("Inner function");
    }
 }
 let innerFunction = outerFunction();
 innerFunction(); // "Inner function"
```

You can also call the inner function by:
```js
outerFunction()(); // "Inner function"
```

Can Also have arrow function inside of a function
```js
let outerFunction = () => () => console.log("Inner function"); let innerFunction = outerFunction(); innerFunction(); // "Inner function"
```

```js
// A function that returns another function
function createMultiplier(x) {
    return function(y) {
       return x * y;
    };
 }
 
 // Call the createMultiplier function and assign the returned function to a variable
 let double = createMultiplier(2);
 
 // Use the returned function to perform a calculation
 console.log(double(5)); // Output: 10
```