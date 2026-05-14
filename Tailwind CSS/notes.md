# Tailwind CSS

## Facts
- ```flex``` children are laid out horizontally (left ↔ right)
- ```flex-col``` children are laid out vertically (top ↕ bottom)
- `dark:` utilities like `dark:text-red-500` are Tailwind overrides and only apply when dark mode is already enabled.
- In shadcn/ui, `background` defines the main surface, `foreground` is primary content on it, `muted` is a subtle surface, and `muted-foreground` is low-emphasis content on muted surfaces, all adapting automatically to light and dark themes.
- Shadcn/ui’s purpose is to avoid hard-coded Tailwind color utilities (like `dark:`) by using semantic, theme-aware CSS variables.
- Shadcn/ui provides a theme-aware color system that automatically adapts to light and dark modes, so you don’t need to manually adjust colors.
- `max-width` controls how big it’s allowed to grow.
- `min-width` controls how small it’s allowed to shrink.
- `sm:` ≥ small screens 640px+, `md:` ≥ medium 768px+, `lg:` ≥ large 1024px+, `xl:` ≥ extra large 1280px+.
- Tailwind is mobile first. You write styles for mobile by default, then add styles for bigger screens using sm, md, lg.
- `mx-auto` adds auto margin left/right. This centers the 400px box.
- Anything that uses `@import`, like: `@import url('https://fonts.googleapis.com/...');` `@import "some-library.css";`. These must come before: `@import "tailwindcss";`.
- `break-words` breaks long chunks if needed.
- `whitespace-normal` allows line breaks.
- `max-w-[220px]` gives a boundary.

## Syntax
**Shadcn using custom font**
```css 
@import url('https://fonts.googleapis.com/css2?family=Playwrite+AU+NSW:wght@100..400&display=swap');

@theme inline {
  --font-heading: "Playwrite AU NSW", cursive; 
} 

@layer base {
  .font-heading {
    font-family: var(--font-heading);
  }
}
```
- In globals.css with shadcn ui, defining `--font-heading` + `.font-heading` creates a custom font utility
- If you use `--font-sans` at `@theme inline` it change the entire font


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


