#set #map

**In Maps, the data is stored as a key-value pair whereas in Set data is a single collection of values that are unique**
# Set
collection of values that can be accessed without a specific key. The elements are unique and the addition of duplicates is not allowed. Sets are mostly used to remove duplicates from any other data structure

```js
let sample = new Set();
sample.add("Hello");
sample.add("Hello");
sample.add(1);
sample.add(2);
sample.add(1);
sample.add("Bye")
sample.add("@");

for (let item of sample) {
	console.log(item);
	}
```
Console.log:
Hello  
1  
2  
Bye  
@

# Map
Maps are used to store data in key-value pairs where keys are used to uniquely identify an element and values contain the data associated with it.
```javascript
const map1 = new Map();

map1.set('a', 1);
map1.set('b', 2);
map1.set('c', 3);

console.log(map1.get('a'));
// Expected output: 1

map1.set('a', 97);

console.log(map1.get('a'));
// Expected output: 97

console.log(map1.size);
// Expected output: 3

map1.delete('b');

console.log(map1.size);
// Expected output: 2
```


![[Screenshot 2023-08-07 at 11.13.37 PM.png]]