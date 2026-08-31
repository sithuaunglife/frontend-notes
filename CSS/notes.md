# CSS

## Facts
- `margin` is the space that pushes a card away from other elements.
- `padding` is the space inside the card that pushes its content away from the card's border.
- `text-align` → aligns text/content.
- `align-items` → aligns children inside Flex/Grid.
- `block` → takes the available width by default and starts on a new line. It can have `width` and `height`.
- `inline-block` → stays on the same line as other inline/inline-block elements while behaving like a box. It can sit beside other boxes and can have `width` and `height`.
- You don't need to give `display: flex` to a child to make it controllable by a flex parent. A flex parent's direct children automatically become flex items.
- You need to give a child `display: flex` to make it a flex container and control the content inside it.
- Flexbox can be nested: a parent can control its direct children, while a child can also become a flex container and control its own children.
- `flex: 1` on children makes them share the available space equally from the parent flex container.
- CSS has `width` and `height`, but there is no general size property for setting both.
- HTML elements have default CSS styles provided by the browser when you don't define your own CSS.
- `justify-content` → controls alignment on the main axis.
- `align-items` → controls alignment on the cross axis.
- The axes depend on flex-direction.
- For `row`: `justify-content` → X-axis / horizontal, `align-items` → Y-axis / vertical.
- For `column`: `justify-content` → Y-axis / vertical, `align-items` → X-axis / horizontal.
- `min-width` → "Don't go below me.". `768px` → `768px` and above.
- `max-width` → "Don't go beyond me.". `768px` → `768px` and below.
- `position: relative` is usually used on the parent to establish a positioning reference for an absolutely positioned child.
- `position: absoulte` is used on the child when you want to position it independently using `top`, `right`, `bottom`, or `left`.
- `align-self` is used when you want to control the alignment of a specific flex child independently from the other flex items.
- When the current row doesn't have enough available columns for the next item, Grid moves that item to the next row.
- You can't use `inline-block` and `flex` together on the same element because they both set the display property.
- Use `inline-flex` when you want an inline element that also acts as a flex container.

## Syntax
**Media Queries**
```css 
@media (max-width: 400px) {
  .heading {
    font-size: 20px;
    color: blue;
  }
}
```
- `@media` → responsive / viewport-based styling.
- `max-width: 400px` → applies when viewport is 400px or less.
- `min-width: 400px` → applies when viewport is 400px or more.

## Terminal Commands
### 

**Heading**
```bash
 <!-- code here -->
```
- Description

## Tools
- Notes


