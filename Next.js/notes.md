# Example Title

## Facts
- ```layout.tsx``` applies persistent UI only to its folder and children (downward), and it unmounts completely when you leave that route segment.
- Next.js relies on the app/ routes. features/ is just imported by routes. Anything outside app/ is invisible to Next.js routing.
- Next.js routing automatically passes the output of ```page.tsx``` as children to its nearest ```layout.tsx```.
- In Next.js App Router, ```layout.tsx``` and ```page.tsx``` are Server Components by default (often SSR), and interactivity is added by nesting Client Components using "use client".
- In the Next.js App Router, Keep ```layout.tsx``` and ```page.tsx``` as Server Components (SSR by default) without "use client", and put all interactivity inside Client Components under features/.
- Without ```"use client"``` a component cannot have interactivity (state, effects, event handlers).
- If you want to use children inside a feature layout component, then you must explicitly wrap the child content with that layout component.
- The Next.js App Router automatically injects children, while in normal React components you must manually wrap and pass children.

## Syntax
**Route Groups – ()**
```css 
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




