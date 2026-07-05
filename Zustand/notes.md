# Zustand

## Facts
- Zustand store has initial (predefined) state, and it only changes when you call its actions (functions) with data.

## Syntax
**Zustand create()**
```js 
const useCategoryStore = create((set) => {
  return {
    categories: [
      { id: 0, title: "All" },
      { id: 1, title: "Bread" },
      { id: 2, title: "Cake" },
      { id: 3, title: "Coffee" },
      { id: 4, title: "Smoothie" },
    ],
    activeCategory: "All",
  }})
```
Everything you return inside create() in Zustand becomes the store state (values + functions)
- string → state
- number → state
- array → state
- object → state
- function → also state (but we call these “actions”)
They all live in one store object and Zustand doesn't care what it is


**Zustand get()**
```js
const { products } = get();
```
- ```get()``` returns the entire Zustand store state object
- { products } destructures only the products property
- It does not keep the entire state, only products


**Zustand built in hydration storage**
```js
  hasHydrated: false,
  setHasHydrated: (state) => set({ hasHydrated: state }),

  onRehydrateStorage: () => (state) => {
    state.setHasHydrated(true);
  },
```
- `onRehydrateStorage(...)` is a Zustand persist lifecycle callback that runs after state is rehydrated from storage


**Zustand Local Storage**
```js
{
  name: "bakery-products"
}
```
- Defines the localStorage key name used by Zustand Persist to save and restore store state

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