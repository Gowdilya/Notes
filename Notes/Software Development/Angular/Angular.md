## How does Incremental DOM work? Can you compare this to Virtual DOM?

Incremental DOM is a JavaScript library that is used to efficiently update the DOM (Document Object Model) of a web page. It works by representing the entire DOM as a tree structure and allowing developers to make changes to it incrementally without redrawing the entire DOM. This can lead to significant performance improvements over traditional approaches that redraw the entire DOM every time a change is made.

When an update is made using Incremental DOM, the library compares the new tree structure with the previous one and identifies the minimum set of changes required to bring the DOM up to date. This allows for efficient updates, as only the necessary changes are made, rather than redrawing the entire DOM.

Virtual DOM, on the other hand, is a concept used by popular [JavaScript frameworks](https://anywhere.epam.com/en/blog/top-5-javascript-frameworks) like React and Vue. In [[Virtual DOM]], the framework maintains a virtual representation of the actual DOM, which is used to determine what changes need to be made to the actual DOM. When a change is made to the virtual DOM, the framework calculates the minimum set of changes required to update the actual DOM and applies them. This can lead to improved performance over traditional DOM manipulation, as it reduces the number of changes that need to be made to the actual DOM.


## Can you explain the role of NgModule in an Angular application?

The main purpose of an NgModule is to provide a compilation context for a group of related components, directives, and services. An NgModule specifies which components, directives, and services are included in the module and how they relate to each other. This allows Angular to perform efficient Ahead-of-Time (AOT) compilation, which results in faster application startup times and better performance.

An NgModule can contain several properties that specify which components, directives, and services are included in the module. These properties include:

- **Declarations:** This property specifies the components and directives that belong to the module.
- **Exports:** This property specifies which components and directives should be available for other modules.
- **Imports:** This property specifies which other modules should be imported into the current module.
- **Providers:** This property specifies which services should be provided at the module level.
- **Bootstrap:** This property specifies the root component that should be bootstrapped when the module is loaded.



# Angular 16
signals:![[Screenshot 2023-09-05 at 10.50.46 PM.png]]
signals are updated using set, update, mutate etc...![[Screenshot 2023-09-05 at 10.53.01 PM.png]]


# Signals vs Behaviour Subject RXJS
https://www.youtube.com/watch?v=iA6iyoantuo

```js
count = signal(0);
count = new BehaviourSubject(0);
```


# Access value in template
```ts
template:`
{{count()}} <!-- signal-->
{{count|async}} <!--BehaviourSubject -->
`
```

we can also access the value using count.getValue() instead of using pipe async.

Access imperatively in class

```js
logMyValue(){
	console.log(this.count()); //signal
}

logMyValue(){
	console.log(this.count.value); //BehaviourSubject
}
```

```js
count = signal(0);
doubleCount = computed(()=> this.count()*2);

count = new BehaviourSubject(0);
doubleCount = this.count.pipe(map(count)=> count * 2*));
```

doubleCount became an observable when using behaviour subject...


Therefore... we have to subscribe to read double count...
```js
someMethod(){
 console.log(this.doubleCount());
}


someMethod(){
 this.doubleCount.subscribe((value)=> console.log(value));
}
```
meaning we have to unsubscribe too

https://rangle.io/blog/angular-for-react-devs