The reason is that Javascript uses dynamic arrays. Even when your array does fill up that extra space you don’t need to do anything. Javascript under the hood will find space in memory, allocate double the amount of memory you need to store your original values as well as the new ones, and copy over the values.

Here are a few operations you’ll be doing with arrays along with their [time complexities](https://en.wikipedia.org/wiki/Time_complexity).
- Accessing value at a given index: O(1)
- Inserting value at the beginning: O(n)
- Updating value at a given index: O(1)

## Linear Search
```js
search(arr, v) is same as implmenting arr.indexOf(v);
```