# JavaScript

## Facts
- Curly braces ``` { } ``` is Object literal, Code block, Destructing pattern.
- If an arrow function needs more than one statement, use ``` { } ``` and an explicit ```return```.
An implicit-return arrow function can return only one expression.
- A return value belongs to the function caller, not the function itself.
- Expressions and Statements are not same they are different concepts.
- The right side of = is usually an expression and expressions produce values.
- Number, string, boolean, object, array, function, arrow function are all values.
- If JavaScript can store it, pass it, return it, or render it — it’s a value.
- In an object, one key can reference only one value, but that value can contain many things.
- One object key can hold one value — and that value can be a function, or an object that contains many functions.
- In function Parameters are placeholders. Arguments are the real values passed in.
- Parameters are just placeholders. The arrow function defines what should happen when real arguments are passed in later.
- When you destructure props, you are extracting object keys. If a key’s value is a function, you can use it as a function in that component (or pass it further).
- Function calling does not happen inside the arrow function. The arrow function only defines what should happen when it is called.
- Nested arrow functions can access the parameters of their outer function.
- ```.``` is used to access values inside an object by its key.
- ```value``` is used to control what’s inside both <input> and <option> elements.
- An <input> cannot display content by itself like <p> or <h1> does.
- When using ```...state.items, newItem``` the new values live in ```items``` not in ```newItem``` To access updated data later, always always read from ```items```. ```newItem``` is temporary and only exists at creation time.
- Destructuring reads current props, not previous state.
- JavaScript is single-threaded but asynchronous.
- Synchronous (sync) run one task runs at a time. Each task must finish before the next one starts. Example: A → B → C
- Asynchronous (async) tasks can be started, and JavaScript doesn’t wait for them to finish before moving on. Results come back later when ready. Example: Start A, Start B, Start C → results arrive when ready
- fetch() returns a Promise out of the box.
- ```await``` does not make JavaScript synchronous. It makes async code work like synchronous.
- ```try...catch``` is used to handle unpredictable failures so the app can recover gracefully and preserve user trust instead of crashing.
- ```try``` runs risky code, ```catch``` handles failure, ```finally``` cleans up. 
- ```throw``` acts as a stop-sign for invalid states, helping developers catch bugs early and protecting the app from unsafe behavior; once the issue is properly fixed, the ```throw``` can be removed.
- ```finally``` is for cancelling or resetting actions that were started earlier (like loading) and must stop, whether the operation succeeds or fails — basically cleanup. If you ever find yourself writing the same cleanup code in both try and catch, it belongs in ```finally```.
- ```try...catch``` is most commonly used around API fetching and other operations that can fail unpredictably.
- JSON is a string format
- JSON is a universal data format used as a bridge between different programming applications.
- ```JSON.parse()``` converts JSON (text/string) into a JavaScript value (object or array).
- ```JSON.stringify()``` converts JavaScript value (object or array) into a JSON (text/string).
- Fake Store API is a mock REST API made for frontend practice.
- Every usable API has documentation.
- Even API users (frontend) must follow REST standards.
- In an API, the URL becomes an endpoint. Example 1: ("https://fakestoreapi.com
") This is the base URL, not an endpoint. Example 2: ("https://fakestoreapi.com/products/1
") This is an endpoint because it points to a specific resource.
- Response 200 means the request was successful.
- In JSON, all keys are strings.
- JSON values can be string, number, boolean, array, object, or null.
- If there is no value, do not include the key at all. Use null only when the value exists but is intentionally empty.
- There is a tool called JSON Server.
- JSON Server is not used in production; it is only for testing and development.
- You do not need to run as admin to use ```curl``` on Windows in most cases.
- In API there is response time.
- In the terminal, endpoints are links.
- You can use DOM manipulation with JSON data.
- A function can only use: Variables inside itself, Variables from outer scope, Variables passed as parameters, Values returned from other functions.
- Destructuring ```{ }``` appears on the left side of ```=``` as a pattern to extract values.
- Destructuring replaces the variable name — it does not sit beside it.

## Syntax
**Object literal**
```js 
const user = {
  name: "Sithu",
  age: 23
};
```
- ``` { } ``` = object literal.
- Inside it → key/value pairs.


**``` { } ``` as a code block**
```js
if (true) {
  console.log("hello");
}
```
- When ``` { } ``` appears after a keyword such as:
- ``` if ```
- ``` for ```
- ``` while ```
- ``` function ```
- …it means a code block, NOT an object.


**``` { } ``` in arrow function**
- Example 1: 
```js
const add = (a, b) => {
  return a + b;
};
```
- Example 2:
```js
const makeUser = () => ({ name: "Sithu" });
```
- In Example 1, there is a return keyword, this ```{}``` is a block, not an object.
- In Example 2, the parentheses force JS to treat ```{}``` as an object, not a block.


**``` { } ``` in Destructuring**
```js
const user = { name: "Sithu", age: 23 };
const { name } = user;
```
- This ```{ name }``` is not creating an object. It’s selecting the ``` name ``` key.


**```e``` (event) controller**
```js
const handleClickSub = (e) => {
  e.preventDefault();
  console.log(e.target);
};
```
- ```e``` (event) is controller to read or control its default behavior. If there is no event to control don't need ```e``` in function.


**Arrow functions**
- Example 1: 
```js
setX((prev) => {
  return prev + 1;
});
```
- Example 2:
```js
setX((prev) => (prev + 1));
```
- In Example 1, ``` { } ``` creates a function body (code block), so you must use ```return``` to send a value back.
- In Example 2, there is no code block, so the arrow function uses an implicit return and the expression result is returned automatically.


**Fetching data using async**
```js
async function fetchData() {
  const res = await fetch("https://fakestoreapi.com/products/1");
  const data = await res.json();
  console.log(data);
}

fetchData();
```
- Fetching data from API.


**Basic try...catch**
```js
try {
  // code that may throw an error
} catch (error) {
  // code that runs if an error happens
}
```
- Basic ```try...catch```. 


**Async / Await try...catch**
```js
try {
  const res = await fetch(url)
  const data = await res.json()
} catch (error) {
  console.error(error)
}
```
- Async / Await try...catch.


**try...catch throw**
```js
try {
  if (!user) {
    throw new Error("User not found")
  }
} catch (error) {
  console.log(error.message)
}
```
- ```try...catch throw```. ```throw``` is like a stop sign and after fix it can be safely removed.


**try...catch finally**
```js
try {
  // risky code
} catch (error) {
  console.error(error)
} finally {
  // always runs (cleanup, reset state, etc.)
}
```
- ```try...catch finally```. ```finally``` is run no matter what, whether an error occurs or not.


**Fetch data from API**
```js
const baseUrl = "http://localhost:8000"
fetch(`${baseUrl}/fruits`)
  .then((res) => res.json())
  .then((json) => console.log(json));
```
- This code is used to fetch data from an API (JSON Server or backend) and log the response data to the console.
- It asks the server for fruit data and prints it in the browser console.


**map()**
```js
const numbers = [1, 2, 3];
const doubled = numbers.map((n) => {
  return n * 2;
});
// doubled → [2, 4, 6]
```
- numbers = [1, 2, 3]
- n represents each value inside numbers
- n will be 1, then 2, then 3


**Storing values in map()**
```js
const numbers = [1, 2, 3];
const doubled = numbers.map(el => {
  el = el * 2;
  return el;
});
```
- map() does not automatically store calculated values.
- map() only stores what you return.
- If you calculate something but don’t return it, the value is thrown away.
- If you want to return the calculated value, you must return the result of the calculation. Writing ```el * 2; return el;``` will return the original value because the calculated result was never returned. You can either assign and return it ```el = el * 2; return el;``` or simply return the calculation directly ```return el * 2;```.
- The original array is not modified.

## Terminal Commands
### Terminal hotkeys

**Stop Terminal → Stop Running Command**
```bash
Ctrl + C
```
- Stops the running command in the terminal.


### Curl

**Curl**
```bash
curl "https://fakestoreapi.com/products/1"
```
- Using ```curl``` to test an API on Windows.


### Json server

**Install json server**
```bash
npm install -g json-server
```
- This command install json server.


**Check json server version**
```bash
json-server --version
```
- This command check json server version.


**Run json server**
```bash
json-server --watch data.json --port 8000
```
- This command watches data.json and runs JSON Server on port 8000.

## Tools
- Notes
