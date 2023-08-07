Two computers need to speak the same language to communicate.

This "language" that computers use is called a [protocol](https://en.wikipedia.org/wiki/Communication_protocol). The most popular protocol for web communication is [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview), which stands for Hypertext Transfer Protocol.

At the heart of HTTP is a simple request-response system. The "requesting" computer, also known as the ["client"](https://en.wikipedia.org/wiki/Client_(computing)), asks another computer for some information. That computer, ["the server"](https://en.wikipedia.org/wiki/Server_(computing)) sends back a response with the information that was requested.
![[Screenshot 2023-07-25 at 10.49.00 AM.png]]
We'll talk about the specifics of how the "requests" and "responses" are formatted later. For now, just think of it as a simple question-and-answer system.

- Request: "What are the items in the Fantasy Quest game?"
- Response: `A list of the items in the Fantasy Quest game`.
Example Fetch call in javascript:

```javascript
async function getItemData() {
  const response = await fetch('https://api.boot.dev/v1/courses_rest_api/learn-http/items', {
    method: 'GET',
    mode: 'cors',
    headers: {
      'X-API-Key': apiKey,
      'Content-Type': 'application/json'
    }
  })
  return response.json()
}

const items = await getItemData()
```

![[Screenshot 2023-07-25 at 10.54.49 AM.png]]

