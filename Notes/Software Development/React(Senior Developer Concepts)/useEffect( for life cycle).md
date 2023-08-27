```js
useEffect(() => {
  // Pass an array of dependencies and the useEffect hook will only run if one of the dependencies changes.
}, [name]);
```

“If you’re familiar with React class lifecycle methods, you can think of `useEffect` Hook as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined.”

### Using `componentDidMount` in functional components with `useEffect`

This is how we can perform the equivalent of `componentDidMount` in functional components using the `useEffect` Hook:

 ```js
useEffect(() => {
  // Inside this callback function we perform our side effects.
});
```


### Using the `componentDidUpdate` with `useEffect`

To perform the equivalent of the `componentDidUpdate` using the `useEffect` Hook, we should do this:

```js
useEffect(() => {
  // Inside this callback function we perform our side effects.
}, [dependency]);
```


### Using `componentWillUnmount` with `useEffect`
[To clean up after a component unmounts](https://blog.logrocket.com/understanding-react-useeffect-cleanup-function/), we have a simple way to perform the equivalent of the `componentWillUnmount` using the `useEffect` Hook.

The only thing that we need to do is to return a function inside the callback function of the `useEffect` Hook like this:

```js
useEffect(() => {
  window.addEventListener("mousemove", () => {});
  return () => {
    window.removeEventListener("mousemove", () => {})
  }
}, []);
```