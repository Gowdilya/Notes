# scope
```js
var a= 5;//global scope
```
^function scoped when used in a function

# let and const are block scoped
```
{
var a= 5;//global scope
let b = 2;
const c = 3;
}
let b = 2;
const c = 3;
^undefined
```


#Shadowing...