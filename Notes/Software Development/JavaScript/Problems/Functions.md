### What is function declaration/definition/statement?
```js
function square(num){
	return num *num
}
```

### Function expression
when you store a function inside a variable
```js
const square = function (num){
	return num *num
}
```
In the above, function is called an Anonymous(no-name) function...

## First class functions?
In javascript functions are first class functions since...
it can be passed as a variable, used as a callback etc


## What is IIFE?(immediately invoked function expression?)
```js
(function square(num){
	return num *num
})(5);
```
^It is immediately called with argument...


# IIFE question
```js
(function (x) {
  return (function (y) {
    console.log(x);//1
  })(2);
})(1);
```

Output: 1
 Because searches innerscope for x, then the parents scope... where x = 1
 happens because of closure

# Function Scope

Function scope overrides global scope...