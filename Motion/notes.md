# Motion

## Facts
- Motion is a JavaScript animation library for building animations and interactive user experiences in React, Vue, and vanilla JavaScript applications.
- Avoid using `sessionStorage` just to stop Motion entrance animations from replaying in a portfolio. A simple entrance animation is usually sufficient since recruiters rarely reload a portfolio repeatedly.
- `import { motion } from "motion/react"` import motion.
- The `<motion />` component is the foundation of Motion for React. It extends standard HTML and SVG elements with animation capabilities. Common examples include `<motion.div>`, `<motion.button>`, and `<motion.img>`.
- `opacity: 0` → Fully transparent (invisible), `opacity: 0.5` → Partially transparent (semi-visible), `opacity: 1` → Fully opaque (fully visible)
- `staggerChildren: 0.15` delays the start of each child animation by **0.15 seconds** relative to the previous child.
- `variants` in Motion receives the variant object you define.
- `initial` → Where the animation starts.
- `animate` → Where the animation ends.
- `initial` and `animate` don't contain animation values themselves—they reference keys in the variants object.
- Child components don't need `initial` or `animate` when a parent is controlling the variants. The parent's `initial` and `animate` values are inherited by the children.

## Syntax
**Heading 1**
```js 
 <!-- code here -->
```
- Description


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Motion

**Installing motion**
```bash
pnpm install motion
```
- Install motion.


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