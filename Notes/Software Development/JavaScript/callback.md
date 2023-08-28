#JavaScript 

A `callback` function is a function that is passed to another function as an argument and is executed after some operation has been completed. Below is an example of a simple callback function that logs to the console _after_ some operations have been completed.
```js
function modifyArray(arr, callback) {
  // do something to arr here
  arr.push(100);
  // then execute the callback function that was passed
  callback();
}

var arr = [1, 2, 3, 4, 5];

modifyArray(arr, function() {
  console.log("array has been modified", arr);
});
```







---

A [[callback]] is a function that is passed as an argument to another function.

In the context of [[React]], a callback is often used as an event handler or to pass data between components.
# callback in JavaScript
A **callback function** is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

==Examples of synchronous callbacks include the callbacks passed to [`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map), [`Array.prototype.forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach), etc. Examples of asynchronous callbacks include the callbacks passed to [`setTimeout()`](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout) and [`Promise.prototype.then()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then).==

Using a callback, you could call the calculator function (`myCalculator`) with a callback (`myCallback`), and let the calculator function run the callback after the calculation is finished:

### Example
```js
function myDisplayer(some) {  
  document.getElementById("demo").innerHTML = some;  
}  
  
function myCalculator(num1, num2, myCallback) {  
  let sum = num1 + num2;  
  myCallback(sum);  
}  
  
myCalculator(5, 5, myDisplayer);
```

## When to Use a Callback?

The examples above are not very exciting.

They are simplified to teach you the callback syntax.

Where callbacks really shine are in asynchronous functions, where one function has to wait for another function (like waiting for a file to load).

Asynchronous functions are covered in the next chapter.