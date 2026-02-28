# TypeScript

## Facts
- If a type is reused or represents domain data → put the ```types``` file outside (global). If a type is local and disposable → keep the ```types``` file inside the feature.
- Types files are written in PascalCase to represent models or contracts, not runtime values, and to distinguish them from functions and variables.
- Zod pattern: Schema (rules) -> Types (z.infer) -> Form (useForm<T>) -> Defaults (must match T)
- ```export type UserEditFormValues = z.infer<typeof profileEditFormSchema>``` ```UserEditFormValues``` is just a custom name for the type. ```z.infer<typeof profileEditFormSchema>``` generates a reusable TypeScript type from the Zod schema that can be used anywhere in the project. It is often placed in a ```types``` file for global reuse. It is most commonly used for form handling and API requests.
- TypeScript disappears at runtime. It only performs type checking during compile time.
- Most shared domain types (like User) are defined once and connected through the Zustand store, so components can reuse them without redefining the types.
- A generic type acts as a placeholder that adapts to whatever specific type is provided to it when used.
- ```<T>``` is a generic type parameter that serves as a placeholder and becomes whatever specific type is passed to it when the generic is used.
- If a field exists in the Zod schema, it must: exist in the UI (Controller / input), exist in defaultValues, exist in the TypeScript type, use the exact same name everywhere. If the schema requires a field that is not rendered in the UI: Validation will fail, onSubmit will not run, It will feel like the button is “not clickable”.
- When creating reusable components or functions always type them.
- Use typescript annotation when typeScript cannot infer type, defining component props / function contracts, Inference is too loose (any, empty array).
- In typescript - ```:``` → type a variable, ```<T>``` → configure a generic function.
- ```:``` just says - This variable thing has this type. ```<T>``` just says - This thing is generic and needs a type supplied.
- Typescript is like a security guard checking codes not turn the code into something.
- TypeScript mainly improves DX (Developer Experience).

## Syntax
**Void**
```ts
function logMessage(message: string): void {
  console.log(message)
  return; // allowed (no value returned)
}
```
- ```void``` means a function does not return any value using the return keyword (it may have return; but not return something).


**Zod + TypeScript Type Flow**
```tsx 
export const customerSchema = z.object({
  name: z.string().min(1, "Name is required"),
  email: z.string().email("Invalid email"),
  phone: z.string().min(7, "Phone number is too short"),
  dateOfBirth: z.coerce.date({
    required_error: "Date of birth is required",
  }),

  gender: z.enum(["male", "female", "other"], {
    required_error: "Please select a gender",
  }),

  address: z.string().min(5, "Address is required"),

  acceptTerms: z.literal(true, {
    errorMap: () => ({ message: "You must accept the terms" }),
  }),
});

export type CustomerFormValues = z.infer<typeof customerSchema>; //This get the schema type from above, CustomerFormValues is passed below function.

const onSubmit = async (data: CustomerFormValues) => {         //<CustomerFormValues is used as type checker>
    try {
      await updateProfile({
        name: data.name, // include only what the API expects
      });

      console.log("Profile updated successfully");
    } catch (error) {
      console.error(error);
    }
  };
```
- Define schema with Zod
- Handles runtime validation.
- Use z.infer<typeof schema> → Generates a TypeScript type from the schema.
- Use that type in functions (e.g., onSubmit) → Provides compile-time type checking.


**Destructuring Typed Props**
```ts
type Props = {
  category: CategoryDetailType;
};

function CategoryTableRow({ category: {id, title, created_at, user}}: Props)
```
- ```Props``` is an object
- It has a property called ```category```
- The value of that property must follow ```CategoryDetailType```
- TypeScript understands: category has id, category has title, category has created_at, category has user because ```CategoryDetailType``` defines those fields.
- I define ```category: CategoryDetailType``` so TypeScript knows the shape of ```category```. Because TypeScript knows the shape, I am allowed to destructure its fields safely.


**Typing in .map() (TypeScript + React)**
- Example 1: 
```ts
data.data.map((el: CategoryDetailType) => (
  <CategoryTableRow key={el.id} category={el} />
))
```
- Example 2:
```ts
const categories: CategoryDetailType[] = data.data;

categories.map((el) => (
  <CategoryTableRow key={el.id} category={el} />
));
```
- Example 3:
```ts
type CategoryTableRowProps = {
  category: CategoryDetailType;
};

function CategoryTableRow({ category }: CategoryTableRowProps) {
  return <div>{category.name}</div>;
}
```
- You can type your data in three ways.
- Type at the source or component level, not inside .map() unless necessary.


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




