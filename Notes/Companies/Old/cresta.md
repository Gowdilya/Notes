reactQuery

### Responsive design

Applies style when window size is smaller than 768px
```
@media screen and (max-width: 768px) {

}
```

Tailwind

|Breakpoint prefix|Minimum width|CSS|
|---|---|---|
|`sm`|640px|`@media (min-width: 640px) { ... }`|
|`md`|768px|`@media (min-width: 768px) { ... }`|
|`lg`|1024px|`@media (min-width: 1024px) { ... }`|
|`xl`|1280px|`@media (min-width: 1280px) { ... }`|
|`2xl`|1536px|`@media (min-width: 1536px) { ... 


## Typography
Use px for small, fixed-size elements like borders or shadows. Use em for typography and other scalable elements that need to change size relative to their parent element. Use rem for scalable typography and responsive layouts that need to change size relative to the root element.



## TypeScript

React.FC is typing for functional Component

https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement

```
const TextInput: React.FC<TextInputProps> = ({ onSendMessage }) => {

 React.KeyboardEvent<HTMLInputElement>
 
React.ChangeEvent<HTMLInputElement>
```


# async in JS

**1. Promises:**

A Promise in NodeJS is similar to a promise in real life. It is an assurance that something will be done. Promise is used to keep track of whether the asynchronous event has been executed or not and determines what happens after the event has occurred. It is an object having 3 states namely:

- **Pending:** Initial State, before the event has happened.
- **Resolved:** After the operation completed successfully.
- **Rejected:** If the operation had error during execution, the promise fails.

**Example:** While requesting data from a database server, the Promise is in a pending state until the data is received. If the data is received successfully, then the Promise is in resolved state and if the data could not be received successfully, the Promise is in the rejected state.

**Error Handling of Promises:** For a successfully resolved promise, we use .then() method and for rejected promise, we use .catch() method. To run a code after the promise has been handled using .then() or .catch() method, we can .finally() method. The code inside .finally() method runs once regardless of the state of the promise.

```js
const promise = new Promise(function (resolve, reject) {
    const string1 = "geeksforgeeks";
    const string2 = "geeksforgeeks";
    if (string1 === string2) {
      resolve();
    } else {
      reject();
    }
  });
 
  promise
    .then(function () {
      console.log("Promise resolved successfully");
    })
    .catch(function () {
      console.log("Promise is rejected");
    });
```

> [!NOTE]
> Output: Promise resolved successfully

**2. Async/Await:**

Async/Await is used to work with promises in asynchronous functions. It is basically syntactic sugar for promises. It is just a wrapper to restyle code and make promises easier to read and use. It makes asynchronous code look more like synchronous/procedural code, which is easier to understand.

await can only be used in async functions. It is used for calling an async function and waits for it to resolve or reject. await blocks the execution of the code within the async function in which it is located. 

**Error Handling in Async/Await:** For a successfully resolved promise, we use try and for rejected promise, we use catch. To run a code after the promise has been handled using try or catch, we can .finally() method. The code inside .finally() method runs once regardless of the state of the promise.


```js

const helperPromise = function () {
    const promise = new Promise(function (resolve, reject) {
      const x = "geeksforgeeks";
      const y = "geeksforgeeks";
      if (x === y) {
        resolve("Strings are same");
      } else {
        reject("Strings are not same");
      }
    });
 
    return promise;
  };
 
  async function demoPromise() {
    try {
      let message = await helperPromise();
      console.log(message);
    } catch (error) {
      console.log("Error: " + error);
    }
  }
 
  demoPromise();
```


## Chaining

```js
function test() {
    return func1()
    .then(v1 => {
        return func2(v1);
    })
    .then(v2 => {
        return func3(v1, v2);
    });
}
```

> **Chaining using Async/Await**

```js
async function test() {
    let v1 = await func1();
    let v2 = await func2(v1); 
    return await func3(v1, v2);  
}
```

**1.Callbacks** with the danger of entering callback hell 2.**Promises** to escape callback hell 3.**async/ await** to write “synchronous” code with promises 4.**Observables** to handle streams of data and apply operator magic Please find all example source code on the following [gist](https://gist.github.com/santoshshinde2012/2f9a9a34c8e6523b46c97c0de9d3cf5f).


# TypeScript

### Type annotation

Type annotations are a crucial concept in TypeScript. They allow developers to specify the data types of variables, function parameters, and return types. This can help catch errors during development and improve code readability.
```tsx
let age: number = 27;
```

# 2. Interfaces

Interfaces are used to define the structure of an object. They specify the names and types of the object’s properties and can be used to enforce consistency across multiple objects.

```tsx
interface Person { name: string; age: number; }
```

# 3. Classes

Classes are a core concept in object-oriented programming, and TypeScript has full support for them. Classes allow developers to define blueprints for objects that share the same properties and methods. They can also include constructors, access modifiers, and inheritance.

For example,

class Animal {   
    name: string;   
    constructor(name: string) {   
        this.name = name;   
    }   
}

This defines a `Animal` class with a `name` property and a constructor that sets the `name` property.


# 4. Generics

Generics are a powerful feature in TypeScript that allow for the creation of reusable code. They allow developers to create functions and classes that can work with a variety of data types.

For example,
```tsx
function identity<T>(arg: T): T {  
return arg;  
}
```

This defines a generic `identity` function that returns the same value that is passed to it.


# 6. Type Inference

Type inference is a feature of TypeScript that allows developers to omit type annotations in certain situations.

For example,
```ts
let age = 27;
```


This will automatically be inferred as a `number` type because it is assigned a numeric value. Type inference can also be used with function parameters and return types, such as:




# 7. Union and Intersection Types

Union types allow for the combination of two or more data types into one. This can be useful when a function or variable can accept multiple types of data.

For example,
```tsx
let age: number | string = 27;
```


This specifies that the `age` variable can be of type `number` or `string`. Intersection types, on the other hand, allow for the creation of a new type that includes all properties and methods of multiple types.

For example,
```tsx
type Animal = Dog & Cat;
```


This creates a new type `Animal` that has all properties and methods of both the `Dog` and `Cat` types.


# 8. Type Guards

Type guards are a feature in TypeScript that allow developers to check the type of a variable at runtime. This can be useful when working with union types or other situations where the type of a variable may not be known.

For instance,
```tsx
if (typeof age === "number") {   
    console.log(age * 2);   
}
```


https://refine.dev/blog/typescript-omit-utility-type/#typescript-omit-with-interface