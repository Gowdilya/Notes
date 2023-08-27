# Manipulating the DOM with Refs

React automatically updates the [DOM](https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction) to match your render output, so your components won’t often need to manipulate it. However, sometimes you might need access to the DOM elements managed by React—for example, to focus a node, scroll to it, or measure its size and position. There is no built-in way to do those things in React, so you will need a _ref_ to the DOM node.

### You will learn

- How to access a DOM node managed by React with the `ref` attribute
- How the `ref` JSX attribute relates to the `useRef` Hook
- How to access another component’s DOM node
- In which cases it’s safe to modify the DOM managed by React

To access a DOM node managed by React, first, import the `useRef` Hook:

```js
import { useRef } from 'react';
```

Then, use it to declare a ref inside your component:

```js
const myRef = useRef(null);
```

Finally, pass your ref as the `ref` attribute to the JSX tag for which you want to get the DOM node:

```jsx
<div ref={myRef}>
```