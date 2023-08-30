
### Synchronous vs asynchronous

```js
//Sync
console.log('start');
console.log("Subscrible to gow");
console.log('Finish');

```
Above code will be executed line by line

### Asynchronous code
```js
console.log('start');
setTimeout(()=>{
	console.log("Subscribe to gow");
}, 0);
console.log('Finish');
```
### "Subscribe to gow" is console.logged last?Even if time=0, Why?
JavaScript is a Single Threaded language, so setTimeout will not be run in parallel, instead JS will run all the synchronous code line by line as usual and then runs the async code...(setTimeout).

setTimout is apart of JavaScripts WEB API.