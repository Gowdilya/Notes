# **1. Find the frequency of elements in array**

## **Method 1**: Using [[reduce()]] method of array


```js
let arr = ["hello", "world", "java", "hello", "java"];

function countWord(words) {
  let result = words.reduce((allNames, name) => {
    if (name in allNames) {
      allNames[name]++;
    } else {
      allNames[name] = 1;
    }
    return allNames;
  }, {});
  return result;
}

console.log(countWord(arr));

```