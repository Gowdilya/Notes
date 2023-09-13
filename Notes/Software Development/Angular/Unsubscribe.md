#NgRx
```js


destroy$ = new Subject<void>();

ngOnDestroy(){
	 this.destroy$.next();
}

someMethod(){
 this.doubleCount.pipe(takeUntill(this.destroy$)).subscribe((value)=> console.log(value));
}
```