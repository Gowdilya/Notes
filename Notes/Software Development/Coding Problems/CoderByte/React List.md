Your goal is to display an unordered list (UL) with list items (LI) within it. The content of each list item should contain two spans (SPAN), one with the name and the other with the age passed in to the DataList function. The span elements should be separated by a single space.

```jsx
import React, { useState } from 'react';
import { createRoot } from 'react-dom/client';
function DataList(props) {
	return (
	<h2>code goes here</h2>
	);
}

const data = [
{ name: 'Daniel', age: 25 },
{ name: 'John', age: 24 },
{ name: 'Jen', age: 31 },
];
const container = document.getElementById('root');
const root = createRoot(container);
root.render(<DataList data={ data } />);
```


# Solution:
```jsx
import React, { useState } from 'react';
import { createRoot } from 'react-dom/client';
  

function DataList(props) {
	const ListItems = props.data.map((listItem, i)=>( 
		<li key={i}>
			<span>{listItem.name}</span>
			{" "}
			<span>{listItem.age}</span>
		</li>
	))
return (
	<h2>
	<ul>
		{ListItems}
	</ul>
	</h2>
	);
}

  
const data = [
	{ name: 'Daniel', age: 25 },
	{ name: 'John', age: 24 },
	{ name: 'Jen', age: 31 },
];

  

const container = document.getElementById('root');
const root = createRoot(container);
root.render(<DataList data={ data } />);
```

