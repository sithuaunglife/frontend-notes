# React

## Facts
- React is a JavaScript library.
- React uses a combination of JavaScript, HTML-like syntax (JSX), and CSS.
- React DOM provides different APIs for rendering: Client API, Server API, Static API.
- React has Legacy API
- Props look like HTML attributes, but they are JS objects passed into a component.
- Props customize a component by giving it data, options, or behavior from the outside.
- React JSX uses expressions, not statements.
- If user interaction or async data causes UI update → React lifecycle concept. If you changing source code it causes UI update → Dev tooling concept.
- Render and re-render happen at runtime while the user is using the application, when reactive data changes (such as state, props, context, or async results), not when the developer edits source code during development.
- Re-rendering and browser refresh are not the same. Re-render means:React runs your component function again to update UI. React updates the UI (component or parts of it) when state/props change. Only the necessary parts change. Page does not reload. Browser refresh is not involved.
- State/props change → React re-renders → Then React updates DOM.
- state change → React component runs again (re-render) → Virtual DOM compare → Real DOM update (only changed parts).
- Browser refresh means:Whole React app is destroyed and started again.
- Mounting does NOT mean you coded the component before or placed it in a layout. Mounting happens at during runtime when React puts the component into the DOM. If you refresh browser mounting always happen. If you refresh browser mounting always happen so re-render always happen. 
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
- ```formData``` validate form values.
- ```formData``` is simply the collected and validated data from your form at the moment the user clicks submit. 
- Inside JSX you can no longer declare variables.
- React follows a simple rule: JSX treats lowercase tags as strings (HTML elements), while PascalCase identifiers are treated as custom React components.
- ```useEffect``` runs after React finishes rendering the UI.
- ```useEffect``` is not for interactivity.
- ```useEffect``` really means “After render is finished and DOM is updated… now you can safely do real world actions.”
- A side effect is an interaction with something React does not control. ```useEffect``` is one way (but not the only way) to handle side effects.
- Vite Server runs on port 5173 by default.
- Controller is from react hook form. Controller is used to integrate controlled or custom components (date pickers, calendars, UI libraries) with React Hook Form when register cannot be used.
- useEffect handles custom side effects, while Controller handles custom UI components.
- You can't declare inside JSX.
- Data sometimes come from prop passing after mapping. Example: ```data.data.map((el: CategoryDetailType)=>(<CategoryTableRow key={el.id} category={el} />)``` category={el} is data passing.
- React does not save component execution or local variables. But it saves state, refs, and previous render tree so it can manage UI updates efficiently.
- ```useRef``` value persists across re-renders because React keeps the same ref object. The value only resets when the component unmounts, such as during route change, conditional removal, key change, or browser refresh.
- ```useRef``` acts like a persistent storage box attached to a component. It keeps values across re-renders but does not trigger rendering. Other logic such as state updates, effects, or event handlers may read from or write to it.
- useState → storing value AND telling React to update UI, useRef → storing value WITHOUT telling React anything.
- When state/props change → that mounted component re-renders. If a component is already mounted in the DOM, and its state changes or its props change, React will re-run that whole component function.

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


**Layout Hierarchy**
```tsx
function HeroLayout({ children }: Props) {
  return (
    <>
      <Header />          // fixed layout element
      <HeroSection />     // fixed landing section
      {children}          // dynamic sections injected here
    </>
  );
}
```
- HeroLayout is a wrapper (parent layout)
- Header and HeroSection are owned / controlled by the layout
- Anything passed between <HeroLayout> ... </HeroLayout> becomes children
- If a route uses HeroLayout, then Header and HeroSection will also be rendered automatically, because they are fixed elements defined inside the layout


**Prop passing**
```ts
data.data.map((el: CategoryDetailType) => (
  <CategoryTableRow key={el.id} category={el} />
))
```
- ```category={el}``` category comes from props and it is defined by child


**payload**
```ts
export const categoryCreateFormSchema = z.object({
  title: z.string().min(1, "Title is required"),
  stay_here: z.boolean(),
  confirm: z.boolean().refine((val) => val === true, {
    message: "You must check to create new category",
    path: ["confirm"],
  }),
});

function useCategoryCreate() {
  const form = useForm<CategoryCreateFormValues>({
    resolver: zodResolver(categoryCreateFormSchema),
    defaultValues: {
      title: "",
      stay_here: false,
      confirm: false,
    },
  });

  const router = useRouter();

  const onSubmit = async (formData: CategoryCreateFormValues) => {
    try {
      const { stay_here, confirm, ...payload } = formData;
      const res = await storeCategory(payload);
      const json = await res.json();
```
- ``` const { stay_here, confirm, ...payload } = formData;``` this is the data I am sending to backend
- ```...payload``` can be renamed. It is a variable 
- ```...payload``` is born from ```formData```
- ```const res = await storeCategory(payload);``` it is sending data from frontend to backend
- ```formData``` is from react hook form
- Because resolver connects Zod validation to React Hook Form, I could reuse the values from schema above

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








