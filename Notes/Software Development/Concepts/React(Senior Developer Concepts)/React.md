## 1. What’s the difference between redux-thunk and redux-saga? List the killer features of each.

## 3. What are GraphQL and REST? Compare them from a React developer’s perspective.
[[REST]] is a mature technology that has been widely used for building APIs for many years. It’s based on the principles of HTTP and uses HTTP verbs like GET, POST, PUT, and DELETE to interact with resources. [[REST]] APIs usually return JSON or XML data.

GraphQL, on the other hand, is a newer technology that was developed by Facebook. It allows clients to specify the data they need and returns only the requested data in a single response. This can be more efficient than REST, especially when dealing with complex data structures or when multiple requests would be needed with REST.

Here are some considerations for React developers who need to choose between GraphQL and REST:

- **Data requirements:** If your application requires a lot of different data from different endpoints, GraphQL can be a good option because it allows you to specify exactly what you need. With REST, you might have to make multiple requests to different endpoints to get all the data you need.
- **Caching:** REST APIs can be more easily cached, which can improve performance. GraphQL has its own caching mechanisms, but they can be more complex to implement.
- **Learning curve:** GraphQL can have a steeper learning curve for developers who are not familiar with it. REST is a more straightforward technology that many developers are already comfortable with.
- **Tooling:** There are many tools and libraries available for working with both REST and GraphQL. However, GraphQL has more specific tools and libraries available that can help you work more efficiently.

To sum up, both GraphQL and REST have their strengths and weaknesses, and the choice will depend on the specific requirements of your application.

If you need to work with complex data structures or want to minimize the number of requests to the server, GraphQL might be a better option. If you need to work with simpler data structures or want to take advantage of the caching capabilities of HTTP, REST might be the optimal choice.