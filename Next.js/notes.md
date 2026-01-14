# Example Title

## Facts
- Notes

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




