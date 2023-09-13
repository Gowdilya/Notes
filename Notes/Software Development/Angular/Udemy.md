# [Angular Version Update](https://www.udemy.com/course/complete-angular-developer-zero-to-mastery/learn/lecture/29938280#overview)
https://update.angular.io/


# Starting the server
- Angular comes with a server
- Required for HTTP Requests
- Monitor files for changes
- Not suitable for production

```shell
ng serve
```

```
npm start
```
Behind the scenes `npm start` runs `ng serve` for Angular
http://localhost:4200/
`Ctrl + C will exit the server`


# Configuration
download extention to use ,editorconfig for VSCode
[Review Config Files](https://www.udemy.com/course/complete-angular-developer-zero-to-mastery/learn/lecture/29537559#overview)

serve - builds for development
build - builds for production

# Main entry file
`src/main.ts`

```ts
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';


platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
```


# Compilation
Just in time compilation and ahead time compilation
### Just in time
browser will compile code when the files are downloaded!
[[Just in Time Comilation.canvas|Just in Time Comilation]]


| Just In time | Ahead of Time | 
| -------- | -------- | 
| Larger file size | Small file size| 
 |   Loads slower since compiler needs to run in browser.    | Loads faster since compiled on deliver to the browser. | 

```ts
// JIT 
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
platformBrowserDynamic()

//AOT
import { platformBrowser } from '@angular/platform-browser';
platformBrowser()
```


# Enable production mode

Reactivity or change detection is the process of updating the html whenever the data changes in an app

### Change detection
- When the app is initialized
- During changes in our data
- Manually triggering change detection

Change detection runs twice when an app is initialized.

