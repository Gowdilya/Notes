#eventListener  #react #JavaScript 
- checkout JavaScript [[eventListener]] 

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