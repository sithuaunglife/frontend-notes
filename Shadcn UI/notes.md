# Shadcn UI

## Facts
- ```<body className={`dark`}>``` changes to dark mode in Shadcn UI.
- In shadcn/ui, dark mode is controlled by the `dark` class on `<html>` or `<body>` (CSS variables).
- In shadcn/ui, dark theme styles are defined under the `.dark` selector in `styles/globals.css`.
- On Windows when using shadcn presets with URLs → use CMD, not PowerShell.
- Shadcn needs WireGuard as Protocol in VPN to work in my country (Myanmar).
- Base UI and Radix UI are different libraries with different DOM behaviors, even though their APIs look similar.
- Hydration errors aren’t always SSR issues, they can happen when incompatible UI libraries (e.g., Base UI vs Radix UI) are mixed.
- In shadcn/ui, `background` defines the main surface, `foreground` is primary content on it, `muted` is a subtle surface, and `muted-foreground` is low-emphasis content on muted surfaces, all adapting automatically to light and dark themes.
- Shadcn/ui’s purpose is to avoid hard-coded Tailwind color utilities (like `dark:`) by using semantic, theme-aware CSS variables.
- Shadcn/ui provides a theme-aware color system that automatically adapts to light and dark modes, so you don’t need to manually adjust colors.

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


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Shadcn

**My shadcn present**
```cmd
pnpm dlx shadcn@latest create --preset "https://ui.shadcn.com/init?base=base&style=nova&baseColor=neutral&theme=red&iconLibrary=lucide&font=roboto&menuAccent=bold&menuColor=default&radius=default&template=next&rtl=false" --template next
```
- An opinionated shadcn/ui initialization preset for Next.js built as a clean and scalable starting point for modern applications, featuring:
- Style: Nova
- Base color palette: Neutral
- Theme: Red
- Menu accent: Bold
- Icon library: Lucide
- Font: Roboto
- Border radius: Default


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




