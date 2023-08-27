#hooks 

> [!NOTE] Don't Confuse with [[getting a ref to the DOM node]] which utilizes useRef

> 


If we tried to count how many times our application renders using the `useState` Hook, we would be caught in an infinite loop since this Hook itself causes a re-render.

To avoid this, we can use the `useRef` Hook.

Use `useRef` to track application renders.

```jsx
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom/client";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />)
```
![[Screenshot 2023-08-09 at 10.34.29 AM.png]]![[Screenshot 2023-08-09 at 10.37.33 AM.png]]![[Screenshot 2023-08-09 at 10.40.49 AM.png]]


# see  [[clearInterval() setInterval()]]

```jsx
import React, { useRef, useEffect, useState } from "react";

export default function Countdown() {
  const [num, setNum] = useState(100);
  const [pause, setPause] = useState(false);
  
  let intervalRef = useRef();
  
  const decreaseNum = () => setNum((prev) => prev - 1);

  useEffect(() => {
    intervalRef.current = setInterval(decreaseNum, 1000);

    return () => clearInterval(intervalRef.current);
  }, []);
  
  const handleClick = () => {
    if (!pause) {
      clearInterval(intervalRef.current);
    } else {
      intervalRef.current = setInterval(decreaseNum, 1000);
    }
    setPause((prev) => !prev);
  };
  
  return (
    <div>
      <div>{num}</div>
      <button onClick={handleClick}>{pause ? "Run" : "Pause"}</button>
    </div>
  );
}
```