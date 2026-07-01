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
- A rule of thumb in Motion. Ask yourself: "Does this element itself need to animate, or is it just a container?". If it's just a container for layout or semantics → use a normal `<section>`, `<div>`, etc. If it's something you want to animate → make it a motion.* component.
- `ease: "easeOut"` Controls how the animation changes speed over time (its easing curve). Starts fast and gradually slows down toward the end. Creates a smooth, natural-looking finish. Commonly used for elements entering the screen.
- Shadcn/ui components are just React components. Most Shadcn/ui components use forwardRef(), making them compatible with Motion. Instead of wrapping a component with `<motion.div>`, you can create a motion version of the component.
- Motion provides animated versions of standard HTML elements. Prefix the element with motion. to make it animatable.
- `whileInView` defines the animation state when the element enters the viewport (the visible area of the browser). The animation is triggered as the user scrolls and the element becomes visible. `whileInView={{ opacity: 1, x: 0 }}` opacity: 1 → Element becomes fully visible. x: 0 → Element moves to its final horizontal position. Typically used with an initial state: `initial={{ opacity: 0, x: -30 }}` `whileInView={{ opacity: 1, x: 0 }}` This makes the element fade in while sliding from left to right.
- `viewport` configures how and when whileInView is triggered. `viewport={{ once: true, amount: 0.2 }}`
- `once` `viewport={{ once: true }}` `true` → Animate only the first time the element enters the viewport. `false` (default) → Animate every time the element enters the viewport.
- `amount` `viewport={{ amount: 0.2 }}` Controls how much of the element must be visible before whileInView starts. `0` → Trigger as soon as any part is visible. `0.2` → Trigger when 20% of the element is visible.
`0.5` → Trigger when 50% is visible. `1` → Trigger only when the entire element is visible.
- Motion can animate interactions like hover, tap, and exit with simple props (`whileHover`, `whileTap`, `AnimatePresence`) instead of manually writing event handlers and animation logic.

## Syntax
**Common Scroll Pattern**
```js 
<motion.div
  initial={{ opacity: 0, y: 30 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, amount: 0.2 }}
/>
```
- 1. `initial` sets the element's starting state (hidden and shifted down).
- 2. The user scrolls until the element enters the viewport.
- 3. When 20% of the element is visible (`amount: 0.2`), `whileInView` animates it to `opacity: 1` and `y: 0`.
- 4. Because `once: true`, the animation plays only the first time the element enters the viewport.


**Motion + React Keys**
```js 
{categories.map((category) => (
  <motion.div
    key={category.title}
    variants={item}
  >
    ...
  </motion.div>
))}
```
- Motion uses React's reconciliation, so it relies on keys to know which elements are added, removed, or updated.

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