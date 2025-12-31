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

## Terminal Commands
### 

**Heading**
```bash
Terminal Code
```
- Description

## Tools
- Notes
