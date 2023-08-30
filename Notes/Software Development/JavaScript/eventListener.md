#eventListener 
```js
const btn = document.querySelector(".increment_btn");
var pressedCount = 0;
btn.addEventListener("click", () => {
  btnPress.innerHTML = ++pressedCount;
});
```


### We can use event listener in React as well
[[Adding Event listener in react using useRef]]

```jsx
import React, { useRef, useEffect } from 'react';

function MyComponent() {
  const myRef = useRef(null);

  useEffect(() => {
    myRef.current.addEventListener('click', handleClick);
    return () => {
      myRef.current.removeEventListener('click', handleClick);
    };
  }, []);

  const handleClick = (event) => {
    console.log('Clicked!');
  };

  return <button ref={myRef}>Click me</button>;
```