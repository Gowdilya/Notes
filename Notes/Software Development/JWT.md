#Node #interview 
https://www.simplilearn.com/tutorials/nodejs-tutorial/jwt-authentication

- [[#What is JSON Web Token?|What is JSON Web Token?]]
- [[#Why use it?|Why use it?]]
- [[#Structure|Structure]]
- [[#Use cases|Use cases]]
	- [[#Use cases#Authorization|Authorization]]
- [[#Information Exchange|Information Exchange]]
- [[#Session-based vs Token-based Authentication|Session-based vs Token-based Authentication]]
		- [[#Authorization#**Limited Scalability**|**Limited Scalability**]]



## What is JSON Web Token?
JSON Web Token (JWT) is a standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON Object

- Encrypted
- verified and trusted via public private key

## Why use it?
small foot print(data) **→** good for HTML and HTTP environments

Signed using shared secret and also public/private key pairs**→** Very secure(highest level security) 

It is easier to work with JWT as JSON parsers are common to most programming languages

Suitable for implementing authorization in large scale applications

## Structure

Header:
- Type of token: JWT
- Signing algorithm: SHA512

```json
{
"alg": "HS512",
"typ": "JWT"
}
```

Payload: Contains the claims that provide information about a user along with other information like token expiry time
```json
{
"sub": "9018234",
"name": "Smith Johns",
"admin": true
}
```

Signature: encoded header and payload along with the algorithm and secret

```
HMCASHA512(
	base64UrlEncode(header) + "." + base64UrlEncode(payload), secret
)
```


## Use cases

### Authorization
most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services and resources that are permitted with that token.

## Information Exchange
Securely transmit information between 2 parties



# Example
```js
const express = require("express");
const jwt = require("jsonwebtoken");

const app = express();

app.get("/api", (req, res) => {
  res.json({
    message: "Hey there! Welcome to this API service",
  });
});

app.post("/api/posts", verifyToken, (req, res) => {
  jwt.verify(req.token, "secretkey", (err, authData) => {
    res.json({
      message: "Posts created...",
      authData,
    });
  });
});

app.post("/api/login", (req, res) => {
  const user = {
    id: 1,
    username: "John",
    email: "john@gmail.com",
  };

  jwt.sign({ user: user }, "secretkey", (err, token) => {
    res.json({
      token,
    });
  });
});

function verifyToken(req, res, next) {
  const bearerHeader = req.headers["authorization"];
  if (typeof bearerHeader !== "undefined") {
    const bearerToken = bearerHeader.split(" ")[1];
    req.token = bearerToken;
    next();
  } else {
    res.sendStatus(403); //forbiden
  }
}
app.listen(3000, (req, res) => {
  console.log("server started on port 3000 ...");
});
```


**JWT is simply a token format.** **A cookie is an HTTP state management mechanism really**.

As demonstrated, a web cookie can contain JWT and can be stored within your browser's Cookies storage.

JWT is simply a [token format](https://www.rfc-editor.org/rfc/rfc7519?ref=jerrynsh.com).

A cookie is an [HTTP state management mechanism](https://www.rfc-editor.org/rfc/rfc6265?ref=jerrynsh.com) really.

As demonstrated, a web cookie can contain JWT and can be stored within your browser’s Cookies storage.

## Session-based vs Token-based Authentication

Rather, the right question to ask is “What is the difference between token-based authentication and session-based authentication?”

|TOKEN-BASED|SESSION-BASED|
|---|---|
|Stateless|Stateful|
|The authentication state is NOT stored anywhere on the server-side|The authentication state is stored on the server side (DB)|
|Easier to scale horizontally|[Harder to scale horizontally](https://www.authgear.com/post/session-vs-token-authentication?ref=jerrynsh.com#:~:text=in%20recent%20times.-,Limited%20Scalability,-Since%20Cookies%20are)|
|Commonly uses JWT for authentication|Commonly uses Session ID|
|Typically sent to the server via an HTTP Request `Authorization` Header (e.g. `Bearer <token>)`. Can use `Cookie` too|Usually sent to the server in the `Cookie` request header|
|Harder to revoke a user session|

#### **Limited Scalability**

Since Cookies are stored in your Server’s memory, it becomes inherently difficult to scale, especially where there are too many simultaneous users on the system. This is, however, quite the opposite with Token-based authentication. Read on to find out more.

“Bearer tokens”. Let’s assume we’ll use JWT as our authentication token from hereon.

What people call a “Bearer token” is a string (e.g. JWT) that goes into the `Authorization` header of any HTTP request. Unlike a browser cookie, it is not automatically stored anywhere, thus making this **CSRF impossible**.

```
GET <http://www.example.com>
Authorization: Bearer my_bearer_token_value          // HTTP Request Header
```

To make use of a “Bearer token”, we’ll need to explicitly store the JWT somewhere in our client (Cookies storage or Local Storage) and add that JWT to our HTTP `Authorization` header while making requests.

If your cookie (e.g. with a JWT) is set with the `HttpOnly` flag, retrieving your token from the client side would be impossible with JavaScript.