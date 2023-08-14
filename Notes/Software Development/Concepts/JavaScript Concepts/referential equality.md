
```js
var a = {
	key:10;
}
var b = { 
	key:10;
}
console.log(a === b); //false```

```
output: false
Because, whenever we compare objects with equality we are really doing [[referential equality]]
Basically checking if both objects are allocated at the same space in memory.(Same memory pointer)


```js
var a = {
	key:10;
}
var b = a;
console.log(a === b); //false```
