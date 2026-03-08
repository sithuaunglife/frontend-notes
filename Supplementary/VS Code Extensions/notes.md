# VS Code Extensions

## Facts
- Prettier format hotkey -> Windows / Linux: Shift + Alt + F, MacOS: Shift + Option + F
- Live Server runs on port 5500 by default.
- In VS Code, hovering over code shows helpful information such as: TypeScript type inference, function parameters and return types, variable types, documentation comments, sometimes the source definition of the code. The text inside () (for example (function), (const), (method)) indicates what kind of thing the identifier is.

## Syntax
### Arrow Function Snippets

**rfc (React Functional Component Export)** 
```jsx
import React from 'react'

export default function AuthType() {
  return (
    <div>AuthType</div>
  )
}
```
- Type ```rfc``` to create a React function component with export default.


**rfce (React Functional Component Export)** 
```jsx
import React from 'react'

function UserType() {
  return (
    <div>UserType</div>
  )
}

export default UserType
```
- Type ```rfce``` to create a React function component with export default.


**rafce (React Arrow Functional Component Export)** 
```jsx
import React from 'react'

const UserType = () => {
  return (
    <div>UserType</div>
  )
}

export default UserType
```
- Type ```rafce``` to create a React arrow function component with export default.


**tsrfc (TypeScript React Functional Component Export)** 
```tsx
import React from 'react'

type Props = {}

export default function AuthType({}: Props) {
  return (
    <div>AuthType</div>
  )
}
```
- Type ```tsrfc``` to create a TypeScript React function component with export default.


**tsrfce (TypeScript React Functional Component Export)** 
```tsx
import React from 'react'

type Props = {}

function authType({}: Props) {
  return (
    <div>authType</div>
  )
}

export default authType
```
- Type ```tsrfce``` to create a TypeScript React function component with export default.


**tsrafce (TypeScript React Arrow Functional Component Export)** 
```tsx
import React from 'react'

type Props = {}

const UserType = (props: Props) => {
  return (
    <div>UserType</div>
  )
}

export default UserType
```
- Type ```tsrafce``` to create a TypeScript React arrow function component with export default.

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




