https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/

```js
const express = require('express'); 
const bodyParser = require('body-parser');
const app = express(); 
app.use(bodyParser.json());
app.get('/articles', (req, res) => {   const articles = [];  
	// code to retrieve an article...   
	res.json(articles); 
}); 
app.post('/articles', (req, res) => {  
	// code to add a new article...   
	res.json(req.body); 
});
app.put('/articles/:id', (req, res) => {   
	const { id } = req.params;  
	// code to update an article...   
	res.json(req.body);
 });
app.delete('/articles/:id', (req, res) => {  
	const { id } = req.params;  
	// code to delete an article... 
	res.json({ deleted: id });
}); 
app.listen(3000, () => console.log('server started'));
```
## Use logical nesting on endpoints

When designing endpoints, it makes sense to group those that contain associated information. That is, if one object can contain another object, you should design the endpoint to reflect that. This is good practice regardless of whether your data is structured like this in your database. In fact, it may be advisable to avoid mirroring your database structure in your endpoints to avoid giving attackers unnecessary information.  

For example, if we want an endpoint to get the comments for a news article, we should append the `/comments` path to the end of the `/articles` path. We can do that with the following code in Express:

```js
const express = require('express');
const bodyParser = require('body-parser');
const app = express();
app.use(bodyParser.json()); 
app.get('/articles/:articleId/comments', (req, res) => {  
	const { articleId } = req.params;
	const comments = [];   
    // code to get comments by articleId 
      res.json(comments);
}); 
app.listen(3000, () => console.log('server started'));
```'
'


contain property?

row-gap vs gutter in grid
label element