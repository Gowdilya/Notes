
## Deprecated React lifecycle methods

A few lifecycle methods were deprecated in the [React version 16.3.0](https://reactjs.org/blog/2018/03/29/react-v-16-3.html):

- `componentWillMount`
- `componentWillReceiveProps`
- `componentWillUpdate`

One of the main reasons that these lifecycle methods were deprecated is because when React implemented async rendering, the incorrect use of one of these lifecycle methods could lead to large errors, encourage unsafe coding practices, and in some situations, result in memory leaks.

If you’re still using one of these lifecycle methods in your actual application and planning to upgrade to the newest React version, you should know that in the [React 17.0](https://reactjs.org/blog/2019/08/08/react-v16.9.0.html) version they were removed completely.

### Mounting phase with `componentDidMount`

This is the first stage of a React component’s lifecycle where the component is created and inserted into the DOM. In this lifecycle stage, we have the `componentDidMount` lifecycle method, and executes when our component mounts:
```js
componentDidMount() {
  console.log("The component has mounted successfully!");
  this.setState({
    loaded: true
  })
}
```
`componentDidMount` allows us to use `setState` so we can easily set and modify our state in the lifecycle method. This lifecycle method executes API calls, make calls to remote endpoints, and retrieves data.

In this stage, the `render` method renders the component into the DOM and is the only method required.

### Updating phase with `shouldComponentUpdate` and `componentDidUpdate`

This updating stage happens after the component mounts and renders into the DOM. A React component then updates when we have an update in our props or state.

We have some lifecycle methods that we can use in this specific lifecycle, such as `shouldComponentUpdate` and `componentDidUpdate`.

The `shouldComponentUpdate` lifecycle method is very easy; we simply return a boolean to determine if React should update the component. The default value for this method is `true`:

```js
shouldComponentUpdate() {
  return true;
}```

So, when React calls the `shouldComponentUpdate` method on the to-be-updated component, React will check the `shouldComponentUpdate` call result. If the result is `true`, React will proceed to update the component. If the result is `false`, React skips updating the component:

```js
const instance = new HelloComponent()
// HelloComponent is to be updated.
// React will shouldComponentUpdate method.
const isToRender = instance.shouldComponentUpdate()
if(isToRender) {
  // if the 'isToRender' is true, then the HelloComponent is updated.
  instance.render()
}
```

We also can simulate the `shouldComponentUpdate` method in a functional component using React Hooks. Using [[useMemo]] adds the `shouldComponentUpdate` method to functional components:
```js
function Parent({a, b}) {
  const HelloWorld = useMemo(() => <HelloComponent a={a} />, [a])
  return {HelloWorld}
}
```
The function argument is called when any of the dependencies in `useMemo` changes. So, looking at our above code, the `HelloComponent` only renders if `a` changes from its previous value.


### Unmounting phase with `componentWillUnmount`

This lifecycle is responsible for the cleanup in our DOM, especially when we want to remove a component from the DOM; in React, this is called unmounting.

We have just one lifecycle method for that lifecycle stage called `componentWillUnmount`. This lifecycle method is invoked when a component is about to be removed from the DOM:

```js
componentWillUnmount() {
  console.log("Component unmounted!");
}
```



# Next read on [[useEffect( for life cycle)]] equivalents to lifecycle methods