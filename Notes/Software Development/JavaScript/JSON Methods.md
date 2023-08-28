#JSON #JavaScript 
# JSON.stringify()
The **`JSON.stringify()`** static method converts a JavaScript value to a JSON string, optionally replacing values if a replacer function is specified or optionally including only the specified properties if a replacer array is specified.

```js
console.


console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
// Expected output: '[3,"false",false]'

console.log(JSON.stringify({ x: [10, undefined, function () {}, Symbol('')] }));
// Expected output: '{"x":[10,null,null,null]}'

console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5)));
// Expected output: '"2006-01-02T15:04:05.000Z"'
```


# JSON.parse()

The **`JSON.parse()`** static method parses a JSON string, constructing the JavaScript value or object described by the string. An optional _reviver_ function can be provided to perform a transformation on the resulting object before it is returned.

```js
const json = '{"result":true, "count":42}';
const obj = JSON.parse(json);

console.log(obj.count);
// Expected output: 42

console.log(obj.result);
// Expected output: true
```