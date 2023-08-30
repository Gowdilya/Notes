[Video Example on Debouncing & Throttling](https://www.youtube.com/watch?v=kCfTEoeQvQw)
#JavaScript #interview #important #eventListener

## Preparation Concepts
Use [[index.html]] Template.
Read [What are the args in debounce?](https://stackoverflow.com/questions/65229032/js-what-are-the-args-in-a-debounce-function)
[[How to call a function that returns another function in JavaScript?]]



## Using [[Lodash]]
```js
/***  Debouncing and Throttling in JavaScript
 Question 1 - Create a button UI and add debounce as follows =>
    --> Show "Button Pressed <X> Times" every time button is pressed
    --> Increase "Triggered <Y> Times" count after 800ms of debounce
*/

const btn = document.querySelector(".increment_btn");
const btnPress = document.querySelector(".increment_pressed");
const count = document.querySelector(".increment_count");

var pressedCount = 0;
var triggerCount = 0;

const debouncedCount = _.debounce(() => {
  count.innerHTML = ++triggerCount;
}, 800);

btn.addEventListener("click", () => {
  btnPress.innerHTML = ++pressedCount;
  debouncedCount();
});
```
google Search lodash cdn and copy paste the script tag
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Page Title</title>
</head>
<body>
<div>
    <h1>
        I made this
    </h1>
</div>
<button class="increment_btn">Increment</button>
<p> Button Pressed <span class="increment_pressed">0</span> Times</p>
<p>Triggered <span class="increment_count">0</span> Times</p>
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.21/lodash.min.js" integrity="sha512-WFN04846sdKMIP5LKNphMaWzU7YpMyCU245etK3g/2ARYbPK9Ub18eG+ljU96qKRCWh+quCY7yefSmlkQw1ANQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="script.js"></script>
</body>
</html>
```

### Throttle
```js
const btn = document.querySelector(".increment_btn");
const btnPress = document.querySelector(".increment_pressed");
const count = document.querySelector(".increment_count");

var pressedCount = 0;
var triggerCount = 0;

// const debouncedCount = _.debounce(() => {
//   count.innerHTML = ++triggerCount;
// }, 800);

const start = new Date().getTime();
const throttledCount = _.throttle(() => {
  const now = new Date().getTime();
  console.log(now - start);
  count.innerHTML = ++triggerCount;
}, 800);

btn.addEventListener("click", () => {
  btnPress.innerHTML = ++pressedCount;
  //debouncedCount();
  throttledCount();
});

```
# create our own debounce implementation

```js
const btn = document.querySelector(".increment_btn");
const btnPress = document.querySelector(".increment_pressed");
const count = document.querySelector(".increment_count");

var pressedCount = 0;
var triggerCount = 0;

const myDebounce = (cb, delay) => {
  let timer;

  return function (...args) {
    if (timer) clearTimeout(timer);
    timer = setTimeout(() => {
      cb(...args);
    }, delay);
  };
};
const debouncedCount = myDebounce(() => {
  count.innerHTML = ++triggerCount;
}, 800);

btn.addEventListener("click", () => {
  btnPress.innerHTML = ++pressedCount;
  debouncedCount();
});
```

# create our own throttle implementation


```js 
const btn = document.querySelector(".increment_btn");
const btnPress = document.querySelector(".increment_pressed");
const count = document.querySelector(".increment_count");

var pressedCount = 0;
var triggerCount = 0;

const myThrottle = (cb, d) => {
  let last = 0; //1100
  return (...args) => {
    let now = new Date().getTime();
    if (now - last < d) return; //2500 - 1100 = 1400
    last = now;
    return cb(...args);
  };
};

const start = new Date().getTime();
const throttledCount = myThrottle(() => {
  const now = new Date().getTime();
  console.log(now - start);
  count.innerHTML = ++triggerCount;
}, 800);

btn.addEventListener("click", () => {
  btnPress.innerHTML = ++pressedCount;
  throttledCount();
});
});```