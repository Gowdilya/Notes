
- [[callback]]

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

- Given a string, reverse each word in the sentence: For example `Welcome to this Javascript Guide!` should be become `emocleW ot siht tpircsavaJ !ediuG`

```js
var string = "Welcome to this Javascript Guide!";

// Output becomes !ediuG tpircsavaJ siht ot emocleW
var reverseEntireSentence = reverseBySeparator(string, "");
// Output becomes emocleW ot siht tpircsavaJ !ediuG
var reverseEachWord = reverseBySeparator(reverseEntireSentence, " ");

function reverseBySeparator(string, separator) {
    return string.split(separator).reverse().join(separator);
  }
```

**String → array**
stringVar.split(separator)

**arrayMethod**
array.reverse()

**array → string**
array.join(separator)


## How to check if an object is an array or not? Provide some code.

The best way to find whether an object is instance of a particular class or not using `toString` method from `Object.prototype`

```js
var arrayList = [1 , 2, 3];

if(Object.prototype.toString.call(arrayList) === '[object Array]') {
  console.log('Array!');
}
```



`Array.isArray` is supported by Chrome 5, Firefox 4.0, IE 9, Opera 10.5 and Safari 5

The JavaScript statement `[Object.prototype.toString.call()](https://medium.com/better-programming/what-is-object-object-in-javascript-object-prototype-tostring-1db888c695a4)` can indeed differentiate between numbers, objects, and even arrays, because it returns a string that specifies the object type in more detail than `typeof`.


```js
console.log(Object.prototype.toString.call(arrayList));
console.log(Object.prototype.toString.call(37)) // [object Number]
console.log(Object.prototype.toString.call(37).slice(8, -1).toLowerCase()) // number

console.log(Object.prototype.toString.call("37")) // [object String]
console.log(Object.prototype.toString.call("37").slice(8, -1).toLowerCase()) // string

console.log(Object.prototype.toString.call(Infinity)) // [object Number]
console.log(Object.prototype.toString.call(Infinity).slice(8, -1).toLowerCase()) // number

console.log(Object.prototype.toString.call(NaN)) // [object Number]
console.log(Object.prototype.toString.call(NaN).slice(8, -1).toLowerCase()) // number

// Works equivalently as using typeof === "number"
const isNumber = value => Object.prototype.toString.call(value).slice(8, -1).toLowerCase() === "number"
```


# Global This


## _Q4_: 

How to empty an array in JavaScript?

Junior 

  [![Top 179 JavaScript Interview Questions](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAABmJLR0QA/wD/AP+gvaeTAAABAElEQVRYhe3WMUrEQBjF8Z9rmtVKwRtoY2NjsYcQOw/gBTyAhYWItfUWItjZWm8jHkDtBAs7sVCw2F1BcLfIIAEJ2Wwc08y/SeZl+OZ9LwkzJBIts1CiT/5rvU6khWYmq3hellBdShNtPYFkIBlIBpoYOMN7YbyLJ3ziGquxDSxhJdxnuMQQp9jEeoPaJqr3g35hzjK+5Z13/W6stN5ffQNDXGBH/hoOsNikYN0EyJvZx2PQ+zXrzWxgLVzP8VXQt+WbV4YBPmIYOMEbjvGCu6DvhflXOMIr7mMY2MANRnhAL+gdHOIZY9xiK4aBeYn+F8xN1Yko1tnwh9YTSCRaZwoVuz6Z81xSgwAAAABJRU5ErkJggg== "Top 179 JavaScript")  **JavaScript**  179](https://www.fullstack.cafe/interview-questions/javascript "JavaScript Interview Questions")  

Problem

```
var arrayList =  ['a', 'b', 'c', 'd', 'e', 'f'];
```

# How could we empty the array above?

Answer

**Method 1**

```
arrayList = [];
```

Above code will set the variable `arrayList` to a new empty array. This is recommended if you don't have **references to the original array** `arrayList` anywhere else because It will actually create a new empty array. You should be careful with this way of empty the array, because if you have referenced this array from another variable, then the original reference array will remain unchanged, Only use this way if you have only referenced the array by its original variable `arrayList`.

For Instance:

```
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList = []; // Empty the array
console.log(anotherArrayList); // Output ['a', 'b', 'c', 'd', 'e', 'f']
```

**Method 2**

```
arrayList.length = 0;
```

Above code will clear the existing array by setting its length to 0. This way of empty the array also update all the reference variable which pointing to the original array. This way of empty the array is useful when you want to update all the other reference variable which pointing to `arrayList`.

For Instance:

```
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList.length = 0; // Empty the array by setting length to 0
console.log(anotherArrayList); // Output []
```

**Method 3 [[splice()]]
**

```
arrayList.splice(0, arrayList.length);
```

Above implementation will also work perfectly. This way of empty the array will also update all the references of the original array.

```js
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList.splice(0, arrayList.length); // Empty the array by setting length to 0
console.log(anotherArrayList); // Output []
```

**Method 4**
Above implementation can also empty the array. But not recommended to use often.

```js
while(arrayList.length) {
  arrayList.pop();
}
```

Above implementation can also empty the array. But not recommended to use often.
## How would you check if a number is an integer?

```
function isInt(num) {
  return num % 1 === 0;
}

console.log(isInt(4)); // true
console.log(isInt(12.2)); // false
console.log(isInt(0.3)); // false
```


# Check if Object instance of class or superclass