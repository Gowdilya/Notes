https://www.youtube.com/watch?v=KAWUf_Qz7qM

# Event Propagation

# Event Bubbling
Starts on the element → parent → Parent

Almost all events start from the bottom and go to the top layer![[Screenshot 2023-08-20 at 5.32.06 PM.png]]

event.stopPropagation()
prevents event from firing on the next element up the chain

### Event Target
The most deeply nested element that caused the event is accessed via event.target

![[Screenshot 2023-08-20 at 5.52.42 PM.png]]


### Event Capturing

```js
elem.addEventListenet("click", onButtonClick, {capture:true});

```