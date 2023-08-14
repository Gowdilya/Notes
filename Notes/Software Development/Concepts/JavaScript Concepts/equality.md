# ===
```js
var a = 10;
var b = 10;
console.log(a === b); //true
```
output: true


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


- **Strict comparison (e.g., ===)** checks for value equality without allowing _coercion_
- **Abstract comparison (e.g. ==)** checks for value equality with _coercion_ 

# The Comparison Algorithm — Object.is()

The `Object.is()` [algorithm](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is#description) determines whether two values are the same if:

1. Both values are `undefined` or `null`.
2. Both values are either `true` or `false`.
3. Both values are `Strings` having the same characters, length, and order.
4. Both values are `Numbers` with the same value or `NaN`.
5. Both values are `Objects` that point to one memory location.

React applies these rules to [[re-render]] components whenever a state change is made.