A function or component that takes another component as input and returns a third component.

[Higher-Order Components](https://reactjs.org/docs/higher-order-components.html) (HOC) are still valuable in the modern React environment because they use class and function components. As a result, they're the ideal bridge between historical and new React components when it is too reusable abstractions. In fact, in this article, we will discuss the difference between React Hook and HOCs.

A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.

Concretely, **a higher-order component is a function that takes a component and returns a new component.**

```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

It is a [[pure function]] . Note that a HOC doesn’t modify the input component, nor does it use inheritance to copy its behavior. Rather, a HOC _composes_ the original component by _wrapping_ it in a container component. A HOC is a pure function with zero [[side-effects]].


### PROP CONFUSION

Do you know HOCs are used for rendering? If there is a problem, an error message is displayed. It generates the specified component if there are no errors:  

```
import * as React from 'react';

const withError = (Component) => (props) => {
  if (props.error) {
    return <div>Something went wrong ...</div>;
  }

  return <Component {...props} />;
};

export default withError;
```