# React

## Facts
- React is a JavaScript library.
- React uses a combination of JavaScript, HTML-like syntax (JSX), and CSS.
- React DOM provides different APIs for rendering:
- Client API
- Server API
- Static API
- React has Legacy API
- Props look like HTML attributes, but they are JS objects passed into a component.
- Props customize a component by giving it data, options, or behavior from the outside.
- React JSX uses expressions, not statements.
- Before ```return```: JavaScript world.
Normal JavaScript rules apply (statements like if, for, variable declarations, functions, etc.).
Inside ```return ( ... )```: JSX world.
JSX only allows expressions (things that produce values), not statements like if or while.
- ```set``` is a built-in function provided by Zustand for updating the store.
- Real values are passed to functions through JSX expressions (often in event handlers).
- ```get()``` is a Zustand built-in function. When called, it returns the entire current store state object, which can then be destructured.

## Syntax
**JSX → Under the Hood**
```js 
React.createElement(type, props, children);
```
- type → HTML tag or component
- props → JS object containing data
- children → nested UI
- React uses this to build the Virtual DOM tree.


**Zustand create()**
```js 
const useCategoryStore = create((set) => {
  return {
    categories: [
      { id: 0, title: "All" },
      { id: 1, title: "Bread" },
      { id: 2, title: "Cake" },
      { id: 3, title: "Coffee" },
      { id: 4, title: "Smoothie" },
    ],
    activeCategory: "All",
  }})
```
Everything you return inside create() in Zustand becomes the store state (values + functions).
- string → state
- number → state
- array → state
- object → state
- function → also state (but we call these “actions”)
They all live in one store object and Zustand doesn't care what it is.


**Zustand get()**
```js
const { products } = get();
```
- ```get()``` returns the entire Zustand store state object.
- { products } destructures only the products property.
- It does not keep the entire state, only products.

## Terminal Commands
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


### Day.js

**Install Day.js**
```bash
npm install dayjs
```
- This command install Day.js.

## Tools
- unDraw is svg picture tool








