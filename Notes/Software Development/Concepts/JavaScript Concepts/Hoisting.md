Hoisting is the default behaviour of javascript where all the variable and function declarations are moved on top.

```js
hoistedVariable = 3; 
console.log(hoistedVariable); // outputs 3 even when the variable is declared after it is initialized 
var hoistedVariable;
```

``` js

function doSomething(){ 
	x = 33;
	console.log(x);
	var x; 
}

```


#### **Note - Variable initializations are not hoisted, only variable declarations are hoisted:**

```JS
var x; console.log(x); // Outputs "undefined" since the initialization of "x" is not hoisted 
x = 23;
```

> #### **Note - To avoid hoisting, you can run javascript in strict mode by using “use strict” on top of the code:**

```javascript
"use strict";
x = 23; // Gives an error since 'x' is not declared
var x; 
```