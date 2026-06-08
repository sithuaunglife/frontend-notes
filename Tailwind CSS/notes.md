# Tailwind CSS

## Facts
- ```flex``` children are laid out horizontally (left ↔ right)
- ```flex-col``` children are laid out vertically (top ↕ bottom)
- `dark:` utilities like `dark:text-red-500` are Tailwind overrides and only apply when dark mode is already enabled.
- `max-width` controls how big it’s allowed to grow.
- `min-width` controls how small it’s allowed to shrink.
- `sm:` ≥ small screens 640px+, `md:` ≥ medium 768px+, `lg:` ≥ large 1024px+, `xl:` ≥ extra large 1280px+.
- Tailwind is mobile first. You write styles for mobile by default, then add styles for bigger screens using sm, md, lg.
- `mx-auto` adds auto margin left/right. This centers the 400px box.
- Anything that uses `@import`, like: `@import url('https://fonts.googleapis.com/...');` `@import "some-library.css";`. These must come before: `@import "tailwindcss";`.
- `break-words` breaks long chunks if needed.
- `whitespace-normal` allows line breaks.
- `max-w-[220px]` gives a boundary.
- `max-h-[60vh]` sets the maximum height to 60% of the viewport height.
- `pr-2` adds right padding inside the container, creating space between the content and the scrollbar.
- Use temporary borders (`border-red-500`, `border-blue-500`, `border-green-500`), background colors (`bg-red-500/20`, `bg-blue-500/20`, `bg-green-500/20`), or outlines (`outline outline-2 outline-red-500`) to visualize element boundaries and inspect actual container sizes when debugging unexpected spacing, absolute positioning issues, Flexbox/Grid alignment problems, overflow issues, or parent containers that are larger than expected; if an absolutely positioned element appears far away, add a border to the relative parent first and verify the parent's size before modifying the child element's position.
- `!` in Tailwind adds `!important` to a utility class, e.g. `!w-fit` → `width: fit-content !important`, useful for overriding conflicting styles.

## Syntax
**Tailwind v4 Setup (globals.css)** 
```css
@import "tailwindcss";
@plugin "tailwind-scrollbar";
```
- Registers the scrollbar plugin in Tailwind v4
- Commonly used in Next.js projects using Tailwind v4
- Enables classes like: `scrollbar` `scrollbar-thin` `scrollbar-thumb-red-500` `scrollbar-track-gray-800`
- Allows styling native browser scrollbars directly with Tailwind classes

## Terminal Commands
### Tailwind plugin

**Tailwind installing custom scrollbar using Tailwind plugin**
```bash
pnpm install tailwind-scrollbar
```
- Installs the `tailwind-scrollbar` plugin.
- Allows styling native browser scrollbars using Tailwind utility classes.
- Useful for dashboards, admin panels, POS systems, and custom UI themes.

## Tools
- Notes


