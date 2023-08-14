#JavaScript 
# clearInterval
The global **`clearInterval()`** method cancels a timed, repeating action which was previously established by a call to [`setInterval()`](https://developer.mozilla.org/en-US/docs/Web/API/setInterval "setInterval()"). If the parameter provided does not identify a previously established action, this method does nothing.
# setInterval
The **`setInterval()`** method, offered on the [`Window`](https://developer.mozilla.org/en-US/docs/Web/API/Window) and [`Worker`](https://developer.mozilla.org/en-US/docs/Web/API/Worker) interfaces, repeatedly calls a function or executes a code snippet, with a fixed time delay between each call.

This method returns an interval ID which uniquely identifies the interval, so you can remove it later by calling [`clearInterval()`](https://developer.mozilla.org/en-US/docs/Web/API/clearInterval "clearInterval()").

```
setInterval(code)
setInterval(code, delay)

setInterval(func)
setInterval(func, delay)
setInterval(func, delay, arg0)
setInterval(func, delay, arg0, arg1)
setInterval(func, delay, arg0, arg1, /* …, */ argN)
```


### [Example 2: Alternating two colors](https://developer.mozilla.org/en-US/docs/Web/API/setInterval#example_2_alternating_two_colors)

The following example calls the `flashtext()` function once a second until the Stop button is pressed.

```js
// variable to store our intervalID
let nIntervId;

function changeColor() {
  // check if an interval has already been set up
  if (!nIntervId) {
    nIntervId = setInterval(flashText, 1000);
  }
}

function flashText() {
  const oElem = document.getElementById("my_box");
  oElem.className = oElem.className === "go" ? "stop" : "go";
}

function stopTextColor() {
  clearInterval(nIntervId);
  // release our intervalID from the variable
  nIntervId = null;
}

document.getElementById("start").addEventListener("click", changeColor);
document.getElementById("stop").addEventListener("click", stopTextColor);
```