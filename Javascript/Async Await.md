`async` and `await` are syntax features introduced in ES2017 (ES8) that make working with asynchronous code easier and more readable. They provide a way to work with promises in a more synchronous style.

### `async` Functions

An `async` function is a function that is declared with the `async` keyword. It always returns a promise. If the function returns a value, the promise will be resolved with that value. If the function throws an error, the promise will be rejected with that error.

Here’s a basic example:

```js
async function greet() {
    return "Hello, world!";
}

greet().then(console.log); // Logs: Hello, world!
```

In the above example, `greet` is an `async` function that returns a string. The returned promise resolves to that string.

### `await` Expressions

Within an `async` function, you can use the `await` keyword to pause the execution of the function until a promise is settled (either resolved or rejected). The `await` expression is used to wait for a promise to resolve and then returns the resolved value.

Here’s an example of using `await`:

```js
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    return data;
}

fetchData().then(console.log);
```

In this example, `fetchData` is an `async` function that:

1. Uses `await` to pause until the `fetch` call completes and returns a `Response` object.
2. Uses `await` again to wait until the `response.json()` promise resolves with the actual data.
3. Returns the data, which is then logged to the console.

### Key Points

1. **Syntactic Sugar**: `async` and `await` provide syntactic sugar over promises. They make asynchronous code look and behave more like synchronous code, which can be easier to read and maintain.
    
2. **Error Handling**: You can use `try...catch` blocks inside `async` functions to handle errors that occur during the execution of `await` expressions.
    
```js
async function fetchData() {
    try {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        return data;
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}
```
    
3. **Top-Level Await**: As of ECMAScript 2022, you can use `await` at the top level in modules. This means you can use `await` outside of `async` functions, but this is only available in ES modules, not in regular scripts.
    
```js
// In an ES module
let data = await fetch('https://api.example.com/data').then(response => response.json());
console.log(data);
```
    

### Summary

- **`async`**: Declares a function as asynchronous and automatically returns a promise.
- **`await`**: Pauses the execution of an `async` function until a promise is settled and returns the result.

Using `async` and `await` simplifies the process of working with promises, making your code easier to read and understand.

![[Pasted image 20240905213246.png]]