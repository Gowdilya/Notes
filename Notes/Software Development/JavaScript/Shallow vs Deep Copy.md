**Shallow copy: means that only the first level of the object is copied.** **Deeper levels are referenced.** **Deep copy: means that all levels of the object are copied**.


```js
const obj = { name: 'Version 1', additionalInfo: { version: 1 } }; 
const shallowCopy1 = { ...obj };
const shallowCopy2 = Object.assign({}, obj); shallowCopy1.name = 'Version 2';
shallowCopy1.additionalInfo.version = 2; 
shallowCopy2.name = 'Version 2';
shallowCopy2.additionalInfo.version = 2; 
console.log(obj); // { name: 'Version 1', additionalInfo: { version: 2 } }
console.log(shallowCopy1); // { name: 'Version 2', additionalInfo: { version: 2 } }
console.log(shallowCopy2); // { name: 'Version 2', additionalInfo: { version: 2 } }
```

- After updating a property in the first level of the cloned objects, **the original property is not updated**.
- After updating a property in a deeper level, **the original property is also updated**. This happens because, in this case, deeper levels are referenced, not copied.


# Deep copy
[[JSON Methods]]

A deep copy can be achieved using **JSON.parse()** **+** **JSON.stringify()**:

```js
const obj = { name: 'Version 1', additionalInfo: { version: 1 } };

const deepCopy = JSON.parse(JSON.stringify(obj));

deepCopy.name = 'Version 2';
deepCopy.additionalInfo.version = 2;

console.log(obj); // { name: 'Version 1', additionalInfo: { version: 1 } }
console.log(deepCopy); // { name: 'Version 2', additionalInfo: { version: 2 } }
```

As you can see in this code snippet:

- After updating a property in the first level of the cloned objects, **the original property is not updated**.
- After updating a property in a deeper level, **the original property is neither updated**. This happens because, in this case, deeper levels are also copied.

# Performance

For obvious reasons, **shallow copies are a lot faster than deep copies**. But this doesn’t mean that you should always use a shallow copy, because sometimes you will also need a copy of the nested objects. So, which option should I use?

- If the depth of your object is equal to one, use a shallow copy.
- If the depth of your object is bigger than one, use a deep copy.