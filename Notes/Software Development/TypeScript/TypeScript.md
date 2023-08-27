### 8. How to create objects in TypeScript?

Objects are dictionary-like collections of keys and values. The keys have to be unique. They are similar to arrays and are also sometimes called associative arrays. However, an array uses numbers to index the values, whereas an object allows you to use any other type as the key.

In TypeScript, an Object type refers to any value with properties. It can be defined by simply listing the properties and their types. For example,

```tsx
let pt: { x: number; y: number } = {
  x: 10,
  y: 20
};
```

### 9. How to specify optional properties in TypeScript?

An object type can have zero or more optional properties by adding a ‘?’ after the property name. 

```tsx
let pt: { x: number; y: number; z?: number } = {
  x: 10,
  y: 20
};
console.log(pt);
```


### 12. Explain the purpose of the never type in TypeScript.

As the name suggests, the never type represents the type of values that never occur. For example, a function that never returns a value or that always throws an exception can mark its return type as never.

```plaintext
function error(message: string): never {
throw new Error(message);
}
```

