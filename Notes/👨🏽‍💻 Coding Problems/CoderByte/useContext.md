```jsx
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom/client";

const UserContext = createContext();

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Component1 />);
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_context2)

---

[❮ Previous](https://www.w3schools.com/react/react_useeffect.asp)[Log in to track progress](https://www.w3schools.com/signup/?utm_source=classic&utm_medium=react_tutorial&utm_campaign=button_lower_navigation "Sign Up and improve Your Learning Experience")[Next ❯](https://www.w3schools.com/react/react_useref.asp)

```js
 const doubledFibonacciNumbers = fibonacciNumbers.map(number => number * 2)

```

```js
const users = [ { name: "Jesse", age: 21, height: "1.90cm" }, { name: "Tom", age: 25, height: "1.67cm" }, { name: "Anna", age: 34, height: "1.59cm" } ] 


const userNames = users.map(({ name }) => name)
```


```js
const userNames = ['Jesse', 'Tom', 'Anna'] function App() {


const renderListOfUserNames = (names) => { 
return names.map(name => <li>{name}</li>)
				 }
				 
				 
				 
				 return ( <div> <ul> {renderListOfUserNames(userNames)} </ul> </div> ); }
															
															
															export default App;
```