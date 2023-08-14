https://www.youtube.com/watch?v=6qERg1Yt1QQ

The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM. This process is called [reconciliation](https://legacy.reactjs.org/docs/reconciliation.html).

ReactDOM(virtual DOM) will sync the state changes in the code to the real  HTML DOM.
VueJS also uses virtual DOM.
React DOM will update in batch... and trigger one pre-render, unless you specific to force re-render.

Redux is separate from React.


# How to Test
Uni-directional data flow
Jest, Jasmine