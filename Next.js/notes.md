# Next.js

## Facts
- ```layout.tsx``` applies persistent UI only to its folder and children (downward), and it unmounts completely when you leave that route segment.
- Next.js relies on the app/ routes. features/ is just imported by routes. Anything outside app/ is invisible to Next.js routing.
- Next.js routing automatically passes the output of ```page.tsx``` as children to its nearest ```layout.tsx```.
- In Next.js App Router, ```layout.tsx``` and ```page.tsx``` are Server Components by default (often SSR), and interactivity is added by nesting Client Components using "use client".
- In the Next.js App Router, Keep ```layout.tsx``` and ```page.tsx``` as Server Components (SSR by default) without "use client", and put all interactivity inside Client Components under features/.
- Without ```"use client"``` a component cannot have interactivity (state, effects, event handlers).
- If you want to use children inside a feature layout component, then you must explicitly wrap the child content with that layout component.
- The Next.js App Router automatically injects children, while in normal React components you must manually wrap and pass children.
- In Next.js App Router, if the page changes based on data use dynamic route, if the page never changes use normal route.
- A dynamic route defines a variable URL; the page receives params.id and, if no matching data exists for that value, it returns a real 404.
- ```<Link> </Link>``` is for navigating (hopping) to another route when the user clicks that link.
- Next.js route files use lowercase file names (e.g. page.jsx), while the exported function inside the file must use PascalCase (e.g. export default function Page()).
- ```"use client"``` does NOT block data fetching. Client Components can fetch data normally.
- In Next.js App Router, route files (page.jsx) should live under app/. Feature folders should contain reusable UI and logic, not route files.
- Modern routers (Next.js App Router, TanStack Router) separate routing files from feature/UI files. Routes define navigation; features define behavior and UI.
- When fetching API data from Client Component ("use client") ```useEffect``` is needed if you want an API call to run automatically without user interaction, with user interaction you don't need ```useEffect```. When fetching API data from Server Component (no "use client") you don't need to use ```useEffect```.
- Frontend development mainly focuses on client-side behavior and UI, while still interacting with server-side logic for data and rendering when needed.
- Layouts can be composed either feature-first (components with children) or route-first (route layouts combining components), depending on whether structure or reuse is the priority.
- In feature-first composition, parent components must be reused manually, while in route-first (Next.js App Router), layouts automatically provide `children` at the route level.




## Syntax
**Route Groups – ()**
```txt 
src/
 └─ app/
     └─ (dashboard)/
         ├─ layout.tsx        ← dashboard layout
         ├─ dashboard/
         │   └─ page.tsx      ← /dashboard
         └─ example/
             └─ page.tsx      ← /example
```
- () creates a route group that does not appear in the URL
- Used to organize routes and share layouts without changing paths
- All routes inside (dashboard) use layout.tsx
- Folder names inside the group (dashboard, example) become actual routes


**Dynamic Routes - []**
```txt
src/
 └─ app/
     └─ users/
         └─ [id]/
             └─ page.tsx      ← /users/:id
```
- ```[id]``` creates a dynamic route segment
- The folder name inside [] becomes a URL variable
- The URL can be - ```/users/1``` or ```/users/abc```
- The page receives the value through params.id
- The route matches the URL shape, not the data
- The page decides - data exists → render, data missing → return a real 404 (notFound())

**Dynamic Import – Disable SSR (Hydration Fix)**
```js 
import dynamic from "next/dynamic";

const ProfileDropdown = dynamic(
  () => import("@/features/dashboard/components/profileDropdown"),
  { ssr: false }
);
```
- Disables server-side rendering for the component
- Renders the component only on the client
- Use when hydration errors are caused by client-only behavior (e.g. window, document, portals, browser-only UI libraries)


**Interactivity injection into SSR layouts**
```tsx 
// features/dashboard/InteractiveLayout.tsx
"use client";

export default function InteractiveLayout() {
  return <button onClick={() => alert("clicked")}>Click</button>;
}
```
```tsx 
// app/dashboard/layout.tsx (Server Component)
import InteractiveLayout from "@/features/dashboard/InteractiveLayout";

export default function DashboardLayout({ children }) {
  return (
    <>
      <InteractiveLayout />
      {children}
    </>
  );
}
```
- Inject Client Components ```"use client"``` into App Router layouts (Server Components) to enable interactivity.
- Server Components define structure & data
- Client Components inject behavior


**Dynamic route**
```tsx
const examples = {
  "1": { title: "Apple" },
  "2": { title: "Banana" },
  "3": { title: "Cherry" },
};

export default function Page({
  params,
}: {
  params: { id: string };
}) {
  const data = examples[params.id];

  if (!data) {
    return <h1>Not found</h1>;
  }

  return <h1>{data.title}</h1>;
}
```
- Route matches → page renders
- id exists → data shown
- id missing → fallback UI

Let's use this route: 
```bash
app/examples/[id]/page.tsx
```
And this URL:
```bash
/examples/3
```
- What Next.js does:
- Sees /examples/3
- Matches it to /examples/[id]
- Extracts id = "3"
- Renders page.tsx
- Passes { params: { id: "3" } }


**Fetch data from API using async ("use client")**
```jsx
"use client";

import { useEffect } from "react";

const FakeStore = () => {
  useEffect(() => {
    const fetchData = async () => {
      const res = await fetch("https://fakestoreapi.com/products/1");
      const data = await res.json();
      console.log(data);
    };

    fetchData();
  }, []);

  return <div>Fake Store</div>;
};

export default FakeStore;
```
- Fetching data from API using ```useEffect```.
- It is needed if you want an API call to run automatically without user interaction.


**Next.js Server Component fetching data API using async (no "use client")**
```jsx
// app/products/page.tsx
const ProductsPage = async () => {
  const res = await fetch("https://fakestoreapi.com/products/1");
  const product = await res.json();

  return (
    <div>
      <h1>{product.title}</h1>
    </div>
  );
};

export default ProductsPage;
```
- Fetching data from API.

## Terminal Commands
### Terminal tool name 1

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description


### Terminal tool name 2

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description

## Tools
- Notes

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note




