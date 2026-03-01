# React

## Facts
- React is a JavaScript library.
- React uses a combination of JavaScript, HTML-like syntax (JSX), and CSS.
- React DOM provides different APIs for rendering: Client API, Server API, Static API.
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
- JSX needs one parent element.
- How you USE something depends on how it was DEFINED. This rule applies when recalling object keys (e.g. state, props, stores). Example: Defined as data → use it as data, Defined as function → call it with ().
- It is recommended to use ```htmlFor``` in React Hook Form.
- JSX borrowed HTML’s attribute rules for string literals.
- JSX borrows the look of HTML, but it is JavaScript.
- To pass data as a prop, JSX must use propName={value} syntax. Example: item={item} is required to pass the item data.
- When passing props, if another component needs the same data, that component must receive it as a parameter (prop).
- Components push data into Zustand, and other components read that data by subscribing to the store.
- A component watches Zustand, and if the subscribed state changes, the component re-renders.
- In React Hook Form, a resolver is a function that lets an external validation library (like Zod) validate form data and return errors in the format React Hook Form understands.
- Inside JSX you can no longer declare variables.
- React follows a simple rule: JSX treats lowercase tags as strings (HTML elements), while PascalCase identifiers are treated as custom React components.
- ```useEffect``` runs after React finishes rendering the UI.
- ```useEffect``` is not for interactivity.
- A side effect is an interaction with something React does not control. ```useEffect``` is one way (but not the only way) to handle side effects.
- Vite Server runs on port 5173 by default.
- Controller is from react hook form. Controller is used to integrate controlled or custom components (date pickers, calendars, UI libraries) with React Hook Form when register cannot be used.
- useEffect handles custom side effects, while Controller handles custom UI components.
- You can't declare inside JSX.

## Syntax
**JSX → Under the Hood**
```js 
React.createElement(type, props, children);
```
- type → HTML tag or component
- props → JS object containing data
- children → nested UI
- React uses this to build the Virtual DOM tree.


**```&&``` (logical AND) — conditional rendering**
```jsx
{loading && <p>Loading...</p>}
```
- If loading is true → React renders <p>Loading...</p>
- If loading is false → React renders nothing
- ```&&``` is for render or not render


**```? :``` (ternary) — conditional choice**
```jsx
{loading ? <p>Loading...</p> : <p>Done</p>}
```
- If loading is true → show first part
- If loading is false → show second part
- ```? :``` is for render this or that


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


**React Hook Form define**
```jsx
 const {
    register, // connects inputs
    handleSubmit, // handles validation + submit
    formState: { errors }, // validation errors
    reset, // resets form state
  } = useForm();
```
- This calls the useForm() hook then destructures useful tools returned by React Hook Form.


**React Hook Form Object passing**
```jsx
 const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => {
    const newProductId = products[products.length - 1].id + 1;
    const newProduct = {
      id: newProductId,
      title: data.new_product_name,
      price: data.product_price,
      category: data.category,
      image: `/images/${newProductId}.png`,
    }
};
```
- React Hook Form creates an object and PASSES it to the parameter that it calls ``` ( ) ```, specifically: onSubmit, validation resolvers callbacks that RHF owns. The parameter itself never changes. It’s just a variable name.


**Normal React Component (manual children wrapping)**
```tsx 
// features/dashboard/DashboardPage.tsx
import LayoutShell from "./LayoutShell";

export default function DashboardPage() {
  return (
    <LayoutShell>
      <h1>Dashboard</h1>
    </LayoutShell>
  );
}
```
```tsx 
// features/dashboard/LayoutShell.tsx
export default function LayoutShell({
  children,
}: {
  children: React.ReactNode;
}) {
  return <main>{children}</main>;
}
```
- ```children``` must be explicitly wrapped and passed.


**Prop passing**
```ts
data.data.map((el: CategoryDetailType) => (
  <CategoryTableRow key={el.id} category={el} />
))
```
- ```category={el}``` category comes from props and it is defined by child

## Terminal Commands
### Day.js

**Install Day.js**
```bash
npm install dayjs
```
- This command install Day.js.

## Tools
- unDraw is svg picture tool. It can customize color according to your web color.

## My Confusion & Understanding

-Confusion: Does destructuring use the initial state? 

Understanding: My confusion was thinking destructuring used the previous empty state.
In reality, Zustand updates state first, then React re-renders and passes the updated data.








