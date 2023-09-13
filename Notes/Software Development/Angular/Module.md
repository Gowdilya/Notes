#JavaScript #Angular

# ES2015 modules

```js
import b from './b'

console.log(b.foo)
```

```js
export default {
	foo: 'Hello world!'
}
```

- Duplicate Modules
- Circular dependency
- Harder to manage overall

# Angular Modules
- Not a replacement of ES2015 Modules
- Groups modules by features

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```


using Decorator for annotating a class as a Module
adds meta data to the class