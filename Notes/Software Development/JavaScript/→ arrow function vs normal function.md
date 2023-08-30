```js
	const shape = {
		radius: 10,
		diameter(){
			return this.radius * 2;
		},
		perimeter: ()=> 2 * Math.PI * this.radius ///this points to window object
	};
	console.log(shape.diameter());//20
	console.log(shape.perimeter());//undefined
```
Output: 
20
undefined
# this
points to window object in perimeter in above example, unlike diameter it points to shape object.