#JavaScript #Promises
- [[referential equality]]  (objects are compared by reference/memory location, not values when using "===")
- [[pure function]] independent of  state changes or data changes. Outputs are only dependent on arguments and always consistent for the same input(arguments). Also has no [[side effects]]

JS Objects
- [[Shallow vs Deep Copy]]: Shallow Copy → Only First level of objects are copied, deeper levels are referenced. Hence you can alter the original unintentionally.
```js
const obj = { name: 'Version 1', additionalInfo: { version: 1 } }; 
const shallowCopy1 = { ...obj };
const shallowCopy2 = Object.assign({}, obj); shallowCopy1.name = 'Version 2';
shallowCopy1.additionalInfo.version = 2; 
shallowCopy2.name = 'Version 2';
shallowCopy2.additionalInfo.version = 2; 
console.log(obj); // { name: 'Version 1', additionalInfo: { version: 2 } }
console.log(shallowCopy1); // { name: 'Version 2', additionalInfo: { version: 2 } }
console.log(shallowCopy2); // { name: 'Version 2', additionalInfo: { version: 2 } }
```
Deep Copy → copy of every level, change in deeper levels of copy won't effect original

A deep copy can be achieved using **JSON.parse()** **+** **JSON.stringify()**:

```js

const obj = { name: 'Version 1', additionalInfo: { version: 1 } };

const deepCopy = JSON.parse(JSON.stringify(obj));

deepCopy.name = 'Version 2';
deepCopy.additionalInfo.version = 2;

console.log(obj); // { name: 'Version 1', additionalInfo: { version: 1 } }
console.log(deepCopy); // { name: 'Version 2', additionalInfo: { version: 2 } }
```


# JavaScript concurrency model

[[Concurrency]] -  is **the ability for a program to be decomposed into parts that can run independently of each other**.

[[🔁 EventLoop]] - How JavaScripts concurrency works. JavaScript handles concurrency by default with an asynchronous programming model using event loops, callbacks, promises, or async/await. 


> [!NOTE] Synchronous vs Asynchronous
> JavaScript executes synchronous code first, and then asynchronous code

```js
console.log("start");

function importantAction(username) {
  setTimeout(() => {
    return `Subscribe to ${username}`;
  }, 1000);
}

const message = importantAction("Roadside Coder");

console.log(message); // will log undefined

console.log("stop");

//Important Action gets executed last... since its async
```


### Callback
```js
function importantAction(username, cb) {
  setTimeout(() => {
    cb(`Subscribe to ${username}`);
  }, 1000);
}

const message = importantAction("Roadside Coder", function (msg) {
  console.log(msg);
});

console.log("stop");
```
Output:
start
stop
Subscribe to Roadside Coder `last since its async`


### Promises
Solution to Pyramid of hell/ callback hell
```js
console.log("start");

const sub = new Promise((resolve, reject)=>{
    setTimeout(()=>{
        const result = true;
        if (result){
            resolve("Subscribed to Roadside Coder");
        }else{
            reject(new Error("Why aren't you subscribed to roadside coder?"));
        }
    }, 2000)
});

sub.then((res)=>{
    console.log(res);
}).catch((err)=>{
    console.log(err);
})
console.log("stop");
```

## Promises
https://www.youtube.com/watch?v=HaJdoFp2OEc

```js
console.log("start");

function importanAction(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Subscribe to ${username}`);
    }, 1000);
  });
}

function likeTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Like the ${video} video`);
    }, 1000);
  });
}

function shareTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Share the ${video} video`);
    }, 1000);
  });
}

importanAction("Roadside Coder")
  .then((res) => {
    console.log(res);
    likeTheVideo("JS Interview Question Video").then((res) => {
      console.log(res);
      shareTheVideo("JS Interview Question Video").then((res) => {
        console.log(res);
      });
    });
  })
  .catch((err) => {
    console.error(err);
  });
console.log("stop");
```

### Promises Chaining
return Promise and chain using .then to have cleaner code
```js
console.log("start");

function importanAction(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Subscribe to ${username}`);
    }, 1000);
  });
}

function likeTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Like the ${video} video`);
    }, 1000);
  });
}

function shareTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Share the ${video} video`);
    }, 1000);
  });
}

importanAction("Roadside Coder")
  .then((res) => {
    console.log(res);
    return likeTheVideo("JS Interview Question Video");
  })
  .then((res) => {
    console.log(res);
    return shareTheVideo("JS Interview Question Video");
  })
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.error(err);
  });
  
console.log("stop");
```

### Promise combinator
Promise.all()
- ==runs in parallel==
- if any fail then complete fail
- if success returns array with complete array of returns

```js
console.log("start");

function importanAction(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Subscribe to ${username}`);
    }, 1000);
  });
}

function likeTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Like the ${video} video`);
    }, 1000);
  });
}

function shareTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Share the ${video} video`);
    }, 1000);
  });
}

Promise.all([
  importanAction("RoadSideCoder"),
  likeTheVideo(),
  shareTheVideo("JavaScript Interview Questions"),
])
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.error("Error:Promise failed", err);
  });
  
console.log("stop");
```
Output:
start
stop
[
  'Subscribe to RoadSideCoder',
  'Like the undefined video',
  'Share the JavaScript Interview Questions video'
]


![[Screenshot 2023-08-30 at 12.18.51 PM.png]]

> [!NOTE] In Promise.all() Remember if any one of them fail, the whole thing fails

### Promise.race()
returns the first promise that gets fulfilled or fails

### Promise.allSettled()
even if any one of the promises fails, will still return all in array format.

### Promise.any()
returns the first fulfilled fulfilled, and ignores all failure. Unless all of them fail.


# Async await(most modern and best for chaining promises)

```js

async function result(params){
	await importanAction("Roadside Coder");
}
const result = async () =>{
    const message1 = await importanAction("Roadside Coder");
}
```

```js
console.log("start");

function importanAction(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Subscribe to ${username}`);
    }, 1000);
  });
}

function likeTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Like the ${video} video`);
    }, 1000);
  });
}

function shareTheVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`Share the ${video} video`);
    }, 1000);
  });
}

const result = async () =>{
    const message1 = await importanAction("Roadside Coder");
    const message2 = await likeTheVideo("Roadside Coder");
    const message3 = await shareTheVideo("Roadside Coder");
    console.log({message1, message2, message3});
}
result();
console.log("stop");
```

Output: 
start
stop
{
  message1: 'Subscribe to Roadside Coder',
  message2: 'Like the Roadside Coder video',
  message3: 'Share the Roadside Coder video'
}


### Error handling  Async await... via try catch
```js
const result = async () => {
  try {
    const message1 = await importanAction("Roadside Coder");
    const message2 = await likeTheVideo("Roadside Coder");
    const message3 = await shareTheVideo("Roadside Coder");
  } catch (error) {
    console.log("Promises Failed", error);
  }
  console.log({ message1, message2, message3 });
};
```

cleanest way of handling promises



### Promises Question #interview 

### What's the output?

```js
console.log("start");

const promise1 = new Promise((resolve, reject)=>{
	console.log(1);// synchronis code so gets executed first
	resolve(2);
	console.log(3);
});

promise.then((res)=>{
	console.log(res);// executed llast since it happens after resolve which is async and last
});
console.log("end");

```
Output: 
start
1
3
end
2


> [!NOTE] Java Script always looks for Synchronous code first
>  during initialization of promise javascript executed console.log since its syncronous code... JS will always execute sync and then async


If there is no resolve, it will not go inside .then block

