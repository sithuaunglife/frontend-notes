# JavaScript

## Facts
- Curly braces ``` { } ``` is Object literal, Code block, Destructing pattern. 

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


** ``` { } ``` in Destructuring**
```js
const user = { name: "Sithu", age: 23 };
const { name } = user;
```
- This ```{ name }``` is not creating an object. It’s selecting the ``` name ``` key.
   
## Terminal Commands
### 

**Heading**
```bash
Terminal Code
```
- Description

## Tools
- Notes
