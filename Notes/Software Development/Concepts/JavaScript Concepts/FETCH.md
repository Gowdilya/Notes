## JAVASCRIPT'S FETCH API

JavaScript's built-in [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) is used to make [[HTTP]] requests.
The `fetch` function is made available to us by the JavaScript language running in the browser, all we have to do is provide it with the parameters it requires.

## USING FETCH

```js
const response = await fetch(url, settings)
const responseData = await response.json()
```

## Basics
- `response` is the data that comes back from the server
- `url` is the URL we are making a request to
- `settings` is an object containing some request-specific settings
- The `await` keyword tells JavaScript to wait until the response comes back from the server before continuing
- `response.json()` converts the response data from the server into a JavaScript object