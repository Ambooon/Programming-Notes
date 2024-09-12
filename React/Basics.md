 # Components and Props
Defining a component
```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

Rendering a component
```javascript
const element = <Welcome name="Sara" />;
```

# State 
```javascript
import React from "./react";

const [count, setCount] = React.useState(0)

function buttonClick(){
    setCount(prevCount => prevCount + 1);
}
```
In **setCount** you have two options. Either to just change the value of the state or change the value of the state base on the previous value.

```javascript
setCount(1); // Just completely changing the value
setCount(prevCount => prevCount + 1); // Value is based from the prev state

// This is an example changing from prev state of an object
setCount(prevState => (
    {
        ...prevState,
        [key]: value // the key is the one you want to change in an object
    })
);
```


# Conditional Rendering
```javascript
{isShown && <h1>Hello<h1/>}
```


# Map method

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
```

Rendering multiple elements
You should put keys in rendering multiple elements and keys must be unique. 
```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>  
							  // Keys must be unique
							  <li key={number.toString()}>
							  {number}
							  </li> );
```
Then we can include the entire **listItems** array inside a **ul** element.
``` javascript
<ul>{listItems}</ul>
```


