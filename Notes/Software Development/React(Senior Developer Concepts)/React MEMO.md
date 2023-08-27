Only [[re-render]] component if any of its prop changes. Instead of default behaviour of re-rendering child component when parent component re-renders.
```jsx
import { memo } from 'react';  

  

const SomeComponent = memo(function SomeComponent(props) {  

// ...  

});
```



