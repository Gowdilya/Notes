```js
const log = (e: SyntheticEvent<HTMLInputElement>): void => {
  // ...
}

const log = (e: ChangeEvent<HTMLInputElement>): void => {
  // ...
}

const log = (e: KeyboardEvent<HTMLInputElement>): void => {
  // ...
}
```


```js
import React, {SyntheticEvent} from 'react';

const Logger = () => {
  // This is not great, but at least
  // some type-safety it guarantees.
  const log = (e: SyntheticEvent): void => {
    console.log(e.target.value);
  }
  
  return (
    <input 
      type="text" 
      onInput={log} 
      defaultValue="Hey!" />
  );
}
```