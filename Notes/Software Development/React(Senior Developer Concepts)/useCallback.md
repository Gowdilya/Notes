#interview #react #hooks #memoization
https://www.youtube.com/watch?v=uojLJFt9SzY

The React `useCallback` Hook returns a memoized [[callback]].

A [[callback]] is a function that is passed as an argument to another function. In the context of React, a callback is often used as an event handler or to pass data between components. The **useCallback** hook takes two arguments: a function and a dependency array. It will return a memoized version of the function that only changes if one of the dependencies has changed.

The `useCallback` and [[useMemo]] Hooks are similar. The main ==difference is that [[useMemo]] returns a memoized _value_ and `useCallback` returns a memoized _function_.== 

### Problem

==One reason to use `useCallback` is to prevent a component from re-rendering unless its props have changed.==

In this example, you might think that the `Todos` component will not re-render unless the `todos` change:


```jsx
import { useState } from "react";
import ReactDOM from "react-dom/client";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);

```

```jsx
import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

Try running this and click the count increment button.

You will notice that the `Todos` component re-renders even when the `todos` do not change.

Why does this not work? We are using `memo`, so the `Todos` component should not re-render since neither the `todos` state nor the `addTodo` function are changing when the count is incremented.

This is because of something called "[[referential equality]]".

## Solution

To fix this, we can use the `useCallback` hook to prevent the function from being recreated unless necessary.

Use the `useCallback` Hook to prevent the `Todos` component from re-rendering needlessly:


```jsx
import { useState, useCallback } from "react";
import ReactDOM from "react-dom/client";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```
```