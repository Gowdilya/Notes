```js
// JavaScript Array Method Cheat Sheet

// Create an array
const numbers = [1, 2, 3, 4, 5];

// Add elements to the end of the array
numbers.push(6);

// Remove the last element from the array
numbers.pop();

// Add elements to the beginning of the array
numbers.unshift(0);

// Remove the first element from the array
numbers.shift();

// Get the length of the array
const length = numbers.length;

// Find the index of an element
const index = numbers.indexOf(3);

// Find the last index of an element
const lastIndex = numbers.lastIndexOf(3);

// Check if an element exists in the array
const exists = numbers.includes(4);

// Create a new array by applying a function to each element
const doubled = numbers.map(num => num * 2);

// Filter elements based on a condition
const evenNumbers = numbers.filter(num => num % 2 === 0);

// Reduce the array to a single value
const sum = numbers.reduce((acc, num) => acc + num, 0);

// Combine multiple arrays
const combined = numbers.concat([6, 7, 8]);

// Remove elements from the array based on a condition
const filtered = numbers.filter(num => num !== 3);

// Sort the array
const sorted = numbers.sort((a, b) => a - b);

// Reverse the array
const reversed = numbers.reverse();

// Get a subset of the array
const subset = numbers.slice(1, 4);

// Check if all elements satisfy a condition
const allEven = numbers.every(num => num % 2 === 0);

// Check if at least one element satisfies a condition
const anyEven = numbers.some(num => num % 2 === 0);

// Find the first element that satisfies a condition
const firstEven = numbers.find(num => num % 2 === 0);

// Find the index of the first element that satisfies a condition
const firstEvenIndex = numbers.findIndex(num => num % 2 === 0);

// Execute a function on each element of the array
numbers.forEach(num => console.log(num));

// Create a new array with elements that pass a test
const filteredNumbers = numbers.filter(num => num > 2);

// Apply a function to all elements and accumulate the result
const total = numbers.reduce((acc, num) => acc + num, 0);

// Check if any element satisfies a condition
const anyPositive = numbers.some(num => num > 0);

// Convert the array to a string
const arrayAsString = numbers.join(', ');

// Convert the array to a string using a custom separator
const customSeparated = numbers.join(' - ');

// Copy a portion of the array to a new array
const copiedArray = numbers.slice(1, 3);

// Create a shallow copy of the array
const shallowCopy = numbers.slice();

// Remove, replace, or add elements with known positions
numbers.splice(2, 1); // Remove one element at index 2
numbers.splice(1, 0, 1.5); // Insert 1.5 at index 1

// Check if the array is empty
const isEmpty = numbers.length === 0;

// Clear all elements from the array
numbers.length = 0;

// Convert an array-like object to an array
const arrayFromObject = Array.from({ length: 5 }, (_, index) => index);

// Iterate over the array using for...of loop
for (const num of numbers) {
  console.log(num);
}


```