#JavaScript 
```js

...
<body>
<div>
	DIV<form action="">
	    FORM
	    <button>BUTTON</button>
	    </form>
</div>
</body>

```

### What is Event Bubbling?
It is the default behaviour of the event to go from bottom to up, button→form → div

```js
const div = document.querySelector("div");
const form = document.querySelector("form");
const button = document.querySelector("button");

form.addEventListener("click", function () {
  alert("form");
});

div.addEventListener("click", function () {
  alert("div");
});

button.addEventListener("click", function () {
  alert("button");
});
```

# Reverse order of events via ==event capture==
div→form → button
```js
const div = document.querySelector("div");
const form = document.querySelector("form");
const button = document.querySelector("button");

div.addEventListener(
  "click",
  function () {
    alert("div");
  },
  { capture: true }
);

form.addEventListener(
  "click",
  function () {
    alert("form");
  },
  { capture: true }
);


button.addEventListener(
  "click",
  function () {
    alert("button");
  },
  { capture: true }
);
```

Capture=true takes precedent... then follows bubbling. When Capture = true its called trickeling

```js
const div = document.querySelector("div");
const form = document.querySelector("form");
const button = document.querySelector("button");



div.addEventListener(
  "click",
  function () {
    alert("div");
  },
  { capture: true }
);

form.addEventListener(
  "click",
  function () {
    alert("form");
  },
  { capture: true }
);

button.addEventListener(
  "click",
  function () {
    alert("button");
  },
  { capture: true }
);
```



## Event.target vs this.target vs event.currentTarget

### Current Target
CurrentTarget: TagName logged in order button→form → div, as BUTTON, FORM, DIV

### Target
stays as BUTTON through the propagation button→form → div,

### This.target
works same as current Target above? this.tagName
logged in order button→form → div, as BUTTON, FORM, DIV
```js
const d = document.querySelector("div");
const form = document.querySelector("form");
const button = document.querySelector("button");

form.addEventListener("click", func);

d.addEventListener("click", func);

button.addEventListener("click", func);

function func(event) {
  alert("currentTarget = " + event.currentTarget.tagName + ", target = " + event.target.tagName + ", this=" + this.tagName);
}
```

How to close modal  based on clicking outside modal?
Check e.target.className, and only close if modalcontainer ...not modal.