```jsx
      setMessages((messages) => {
        return [...messages, newMessage];
      });
```

is Not the same as...

```jsx
	setMessages([...messages, newMessage]);
```

Since In the first one setMessages fires a function which uses the updated messages when setting state.
In the second one messages could be stale/outdated.