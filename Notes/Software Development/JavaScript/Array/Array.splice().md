#Array #JavaScript 

changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.


```js
var arrayList = [1, 2, 3, 4, 5];

const startIndex = 2;
const deleteCount = 2;
const replaceBy = "E";
arrayList.splice(startIndex, deleteCount, replaceBy, replaceBy, replaceBy);
console.log(arrayList);
```
OutPut:  [ 1, 2, 'E', 'E', 'E', 5 ]