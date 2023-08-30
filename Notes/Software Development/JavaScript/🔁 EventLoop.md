#JavaScript 

### Event loop

The JavaScript event loop is the model adopted by JavaScript to execute functions asynchronously. It is responsible for executing queued tasks, and it is the secret behind JavaScript’s ability to perform multithreading tasks.

JavaScript starts a script execution from the top and continues until the last line of execution. Typically, functions that are to be executed are stored in the callback queue.

The event loop constantly monitors both the callback queue and the callback stack. It checks whether the call stack is empty and pushes the next item in the callback queue to the call stack. The event loop does nothing if the call stack isn't empty. It waits until the call stack is empty and pushes the next function from the callback queue to the stack.

The following picture illustrates the JavaScript runtime, Web API, call stack, and event loop:

![[Pasted image 20230830094323.png]]

The event loop constantly pulls functions out of the callback queue and pushes them to the call stack whenever the call stack becomes empty. After the task in the call stack completes, the event loop takes the next item in the callback queue and sends it to the call stack to start executing. This is the basic principle of how the event loop works.

### Callbacks

Node.js makes heavy use of callbacks to perform quick I/O operations. Callbacks are functions, passed as arguments to another function. In JavaScript, callbacks are used to reduce unexpected freezing of applications.

A callback function is executed after the completion of the outer function, which takes it as an argument. It is used to run a function immediately after the completion of another function. The `setTimeout()` method is an example of a function that takes another function as an argument. Here is an example:

```
  const greeting = function() {
    console.log("Hello there")
}

  setTimeout(greeting, 3000)
```

A callback function (greeting) is passed as an argument to the `setTimeout()` method, and it executes immediately after the `setTimeout()` completes its execution of 3 seconds.

Callback functions allow JavaScript to execute codes asynchronously. While the `setTimeout()` function executes, other statements can execute simultaneously. Using this method, JavaScript can handle concurrency and execute multiple statements simultaneously.

### Promises

Promises are similar to callbacks in the sense that they can both be used to handle asynchronous tasks in JavaScript. Prior to the adoption of promises, callbacks were used to handle tasks asynchronously. However, handling multiple nested callbacks became a problem and resulted in callback hell, which caused unnecessary complexity to the program. Promises became the ideal way to handle multiple nested callbacks.

A promise is an object that produces a value after an asynchronous operation. It is a good way to determine whether the asynchronous operation is successful. An example of the use of a promise is written below:

```
  let promise = new Promise(function (resolve, reject) {
    resolve("done")
    reject("error")
}

  promise.then(function(value) {
    console.log(value)
})
```

A promise uses the `.then` and `.catch` methods to consume resolved and rejected promises.

Since promises run asynchronously, functions whose operation depends on the promise's outcome should be placed in the `.then` method, as shown in the code above. It would only run when the promise is gotten.

### Async/await

Using and chaining promises together gets bulky and confusing, `async/await` was introduced to solving this problem. It is used to efficiently run and identify asynchronous codes.

The `async` keyword is placed before a function to identify an asynchronous function and make sure the function always returns a promise.

The `await` keyword delays the function until a promise returns. A function will not complete its execution until a promise is received.

The `async` and `await` keywords work together to perform and run JavaScript code asynchronously. The await keyword cannot be used outside an async function. Here is an example of an async/await code:

```
  async function() {
    await setTimeout(() => {
      console.log("Welcome Back!")
    }, 2000)
}

  console.log("Hello")
```

Asynchronous functions take time to process and can run simultaneously in the background without blocking the execution of other processes.

Asynchronous functions in JavaScript are identified by the `async` keyword. This tells JavaScript that the function will take time before it finishes its execution and can go on with other tasks while it executes(i.e., run as a background process).

This allows JavaScript to run other operations outside the async function without waiting to get a response from the function. The await keyword identifies the part of the function that takes time to complete its execution. Here is the result of the code shown above:

```
  Hello
  Welcome Back!
```

As you can see, “Hello” displays before the “Welcome Back!” message. This is because the async function runs in the background and takes about two seconds to display “eat”. While executing the function in the background, JavaScript continues executing other statements without waiting for a result from the async function.

This is how JavaScript can perform tasks and execute statements concurrently in an overlapping manner.

Callbacks, promises, and async/await are JavaScript features that make it possible to run tasks concurrently with the help of the event loop and the browser's web APIs.


## Conclusion

There are a lot of problems with sequential code execution when processing data. It is difficult to know how long it will take to process the data. A sequential code will block all other codes and prevent the application from further execution.

Concurrent code eliminates the blocking problem of sequential coding and can handle multiple user requests or events simultaneously without any problems.

JavaScript is, by default, a single-threaded programming language and runs its code sequentially. However, JavaScript is not the best choice when building CPU-intensive applications because JavaScript is still a single-threaded language and can run a single process on a single core.

Other languages capable of handling heavy concurrent tasks should be considered when developing CPU-intensive applications.