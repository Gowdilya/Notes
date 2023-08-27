Are like JavaScript libraries that can be used in a Node.js application to include a set of functions

To include a moduleuse require()

**HTTP is an independent module.** **[[Express.js]] is made on top of the HTTP module**.

```
var http = require('http')
```

HTTP comes inbuilt along with NodeJS that is, we don’t need to install it explicitly.

HTTP module provides various tools (functions) to do things for networking like making a server, client, etc.

Express along with what HTTP does provide many more functions in order to make development easy.

Express provide _express.static_ function for static asset hosting. Example: _app.use(express.static(‘public’));_

HTTP does not provide function for static hosting, you require to write your own.