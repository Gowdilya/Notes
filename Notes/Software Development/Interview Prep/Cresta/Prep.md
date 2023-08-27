custom event
https://javascript.info/dispatch-events
event bubbling
promises
https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent

https://blog.logrocket.com/custom-events-in-javascript-a-complete-guide/
## [Custom events](https://javascript.info/dispatch-events#custom-events)

For our own, completely new events types like `"hello"` we should use `new CustomEvent`. Technically [CustomEvent](https://dom.spec.whatwg.org/#customevent) is the same as `Event`, with one exception.

In the second argument (object) we can add an additional property `detail` for any custom information that we want to pass with the event.

For instance:


https://blog.logrocket.com/custom-events-in-javascript-a-complete-guide/#dispatching-custom-events-in-javascript

**Interview Response:** A custom event is a user-defined event that can be created and dispatched to perform actions not covered by built-in events.

https://www.hellojavascript.info/docs/browser-related-questions/browser-events/dispatching-custom-events