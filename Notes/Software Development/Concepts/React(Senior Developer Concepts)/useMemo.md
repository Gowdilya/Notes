#hooks #memoization 
The `useMemo` Hook can be used to keep expensive, resource intensive functions from needlessly running.


**useMemo** is a hook that returns a memoized value. It takes two arguments: a function that returns a value and a dependency array. ==It will call the function and return its result only if one of the dependencies has changed.==

==Use when you have to re-call / compute expensive computations!== Especially when it needs to be calculated again/reused in [[recursive]] examples like factorials.

```jsx
const memoizedResult = useMemo(() => {  
	return expensiveFunction(propA, propB);  
}, [propA, propB]);
```

```jsx
import { useState } from 'react';  
export function CalculateFactorial() {  
	const [number, setNumber] = useState(1);  
	const [inc, setInc] = useState(0);  
	const factorial = factorialOf(number);  
	
	const onChange = event => {  
		setNumber(Number(event.target.value));  
	};  
	const onClick = () => setInc(i => i + 1);  
return (  
	<div>  
	Factorial of  
	<input type="number" value={number} onChange={onChange} />  
	is {factorial}  
	<button onClick={onClick}>Re-render</button>  
	</div>  
	);  
}  

  

function factorialOf(n) {  
	console.log('factorialOf(n) called!');  
	return n <= 0 ? 1 : n * factorialOf(n - 1);  
}
```

