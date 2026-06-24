# JavaScript

## Facts
- JavaScript was originally created for browsers, but today it runs in many places. (Example: Computer/Mobile Apps, Desktop Apps, Cloud Servers)
- JavaScript can command computer since it is programming language.
- `let` is declaring(creating) variable. For example: `let x=5`. `=` is the assignment operator. It assigns the value on the right (5) to the variable on the left (x).
- `var` is a JavaScript keyword used to declare a variable.
- `let lunchbox = ["rice", "curry"]` it is setting up array. lunchbox[0] it is indexing/accessing the first item ("rice") of array.
- `let myself = {name: "John", age:22}` it is object. `name` is key while `John` is value. `myself["name"]` it is accessing the `name` value (John). You can also use `myself.name` to get value.
- Typing only the variable can show its value in the browser console or Node.js REPL.
- Variables are usually temporary and disappear when the program stops or when you close/refresh the browser page.
- In browser console `localStorage.setItem("x",5)` stores the value `5` in Local Storage under the key `x` and keep them. 
- In browser console `localStorage.getItem("x")` get value stored under the key `x`.
- In the browser console, the ↑ (Up Arrow) and ↓ (Down Arrow) keys let you navigate through previously executed commands, similar to a terminal.
- `++` means +1 while `--` means -1.
- `===` checks whether both the value and the data type are strictly equal and the same.
- `!==` checks whether two values are not strictly equal. It returns true if the value is different or the type is different.
- JavaScript can concatenate values even when the data types are different. When using + with a string, JavaScript automatically converts the other value to a string. Example: `"John" + 5` will result `John5`. 1. number + number → numeric addition, result is a number. 2. string + string → string concatenation, result is a string. 3. string + number → number is converted to a string, result is a string. 4. number + string → number is converted to a string, result is a string.
- If you want to use JavaScript inline inside an HTML file, use `<script> </script>`.
- For larger projects, it's common to write JavaScript in a separate file such as app.js and link it to the HTML file. `<script src="app.js"></script>` in <body></body> to link external JavaScript file.
- `console.log()` prints/displays a value to the browser console.
- For `%` JavaScript asks: How much is left over after dividing 10 by 3? (10 ÷ 3 = 3 remainder 1) So: (10 % 3 // 1)
- Semicolon `;` is used to end a statement. JavaScript can often insert semicolons automatically (ASI). Many developers use semicolons for consistency.
- A statement is an instruction that JavaScript executes to perform an action, such as creating variables, calling functions, making decisions, or returning values.
- `[]` creates an Array in JavaScript.
- `{}` creates an Object in JavaScript.
- `{}` creates a block. A block groups one or more statements together so JavaScript can treat them as a single unit. Think of `{}` as a box. Without the box, JavaScript usually takes only the next statement.
- `var` is still valid JavaScript, but modern JavaScript primarily uses `let` and `const`.
- `let` can be declared outside a block, but when declared inside `{}`, it is only accessible within that block. `var` is not block-scoped, so variables declared with `var` inside a block are still accessible outside the block.
- `{}` creates a block. Variables declared with let and const inside that block have block scope.
- `undefined` means a variable exists, but it has not been assigned a `value` yet.
- `null` is intentionally set to "nothing".
- `let` and `const` cannot be redeclared in the same scope, but var can be redeclared.
- `const` means you cannot reassign the variable to a different value later.
- Most modern code editors can detect JavaScript errors and show them with a red underline or squiggly line.
- `undefined` is a primitive data type in JavaScript. It is also the default value assigned to variables that have been declared but not given a value.
- Variable names in JavaScript can contain letters (`a-z`, `A-Z`), numbers (`0-9`) (but cannot start with a number), underscores (`_`), and dollar signs (`$`). They cannot contain spaces or special characters such as `@`, `#`, `%`, `&`, `!`, or `-`. Variable names are also case-sensitive, so `myName` and `MyName` are considered different variables.
- You cannot write `'I'm John!'` because the apostrophe in `I'm` closes the string early. Use `"I'm John!"` or `'I\'m John!'` instead.
- The backslash `\` is called the escape character. It tells JavaScript to treat the character after it differently instead of its normal meaning.
- Inside template literals (backticks ` `), you can freely use both single quotes `'` and double quotes `"` without escaping them. Template literals also support interpolation using `${}`, which allows you to insert variables or expressions directly into a string.
- JavaScript has only one number type: Number. There are no separate integer and float types. Both whole numbers and decimal numbers are stored as Number values.
- Primitive variables store the actual value. Object variables store a reference to an object in memory.
- var and let can exist without a value (undefined). `const` cannot exist without a value.
- An expression is anything that produces a value.
- JavaScript generally ignores extra spaces, tabs, and line breaks.
- JavaScript often works even if you forget a semicolon because of Automatic Semicolon Insertion (ASI). However, missing semicolons can sometimes cause unexpected bugs. Many other programming languages require semicolons and will produce errors if they are missing. Using semicolons consistently can make code clearer and help avoid certain issues.
- `fruits [0] = "aa"` replaces the value stored at index `0` of the array. It does not reassign the `fruits` variable itself, so it is allowed with `const`.
- Arrays are mutable even with `const`.
- You can declare an empty array with `const` and add values later because you're modifying the array, not reassigning it.
- Object properties must have a value, but that value can be an `empty string` `null` `undefined` an empty array or an empty object.
- For boolean variables (true, false), it is better to use names like is, can and should. Example: `const canVote = true;` `const isLoading = false` `shouldRetry = false`
- In JavaScript `1` is truthy while `0` is falsy.
- `NaN` stands for "Not a Number". It appears when a numeric operation cannot produce a valid number. `NaN` is falsy. 
- JavaScript supports both Imperative and Declarative programming styles.
- Imperative focuses on how to do something step by step while Declarative focuses on the desired result and lets JavaScript handle the implementation details.
- React and modern frontend development mainly use the Declarative style through methods like `map()` `filter()` and React components, although Imperative code is still used when necessary.
- Array is an ordered list of values. You access items using their index (position) with `[]`.
- `const [first, second] = fruits;` this is array destructuring.
- Curly braces ``` { } ``` is Object literal, Code block, Destructuring pattern.
- If an arrow function needs more than one statement, use ``` { } ``` and an explicit ```return```. An implicit-return arrow function can return only one expression.
- A return value belongs to the function caller, not the function itself.
- Expressions and Statements are not same they are different concepts.
- The right side of = is usually an expression and expressions produce values.
- Number, string, boolean, object, array, function, arrow function are all values.
- undefined → missing value. You didn’t set it, so JavaScript gives it automatically.
- `?.` protects the thing before it, not after it. Example 1: (`user?.name`) user is protected.
- `&&` → one-sided condition “maybe show”.
- `? :` → two-sided condition “choose between two things”.
- `[...items, newItem]` combines old items with the new one.
- `{ items: newItem }` replaces the old items completely.
- The key always stays the same. Only the value changes whether you replace it or build a new one using spread.
- null → empty value. You set it yourself on purpose.
- If JavaScript can store it, pass it, return it, or render it — it’s a value.
- In an object, one key can reference only one value, but that value can contain many things.
- One object key can hold one value — and that value can be a function, or an object that contains many functions.
- In function Parameters are placeholders. Arguments are the real values passed in.
- Parameters are just placeholders. The arrow function defines what should happen when real arguments are passed in later.
- When you destructure props, you are extracting object keys. If a key’s value is a function, you can use it as a function in that component (or pass it further).
- Function calling does not happen inside the arrow function. The arrow function only defines what should happen when it is called.
- Nested arrow functions can access the parameters of their outer function.
- ```.``` is used to access values inside an object by its key.
- ```value``` is used to control what’s inside both ```<input>``` and ```<option>``` elements.
- An ```<input>``` cannot display content by itself like ```<p>``` or ```<h1>``` does.
- When using ```...state.items, newItem``` the new values live in ```items``` not in ```newItem``` To access updated data later, always always read from ```items```. ```newItem``` is temporary and only exists at creation time.
- There are naming conventions like: camelCase (helloWorld), PascalCase (HelloWorld), kebab-case (hello-world) and snake_case (hello_world).
- In JavaScript PascalCase case is commonly used for classes and React components.
- kebab-case is commonly used for file names and CSS properties.
- snake_case is commonly used in databases, Python, and some APIs.
- Destructuring reads current props, not previous state.
- JavaScript is single-threaded but asynchronous.
- Synchronous (sync) run one task runs at a time. Each task must finish before the next one starts. Example: A → B → C
- Asynchronous (async) tasks can be started, and JavaScript doesn’t wait for them to finish before moving on. Results come back later when ready. Example: Start A, Start B, Start C → results arrive when ready
- fetch() returns a Promise out of the box.
- ```await``` does not make JavaScript synchronous. It makes async code work like synchronous.
- ```try...catch``` is used to handle unpredictable failures so the app can recover gracefully and preserve user trust instead of crashing.
- ```try``` runs risky code, ```catch``` handles failure, ```finally``` cleans up. 
- ```throw``` acts as a stop-sign for invalid states, helping developers catch bugs early and protecting the app from unsafe behavior; once the issue is properly fixed, the ```throw``` can be removed.
- ```finally``` is for cancelling or resetting actions that were started earlier (like loading) and must stop, whether the operation succeeds or fails — basically cleanup. If you ever find yourself writing the same cleanup code in both try and catch, it belongs in ```finally```.
- ```try...catch``` is most commonly used around API fetching and other operations that can fail unpredictably.
- JSON is a string format
- JSON is a universal data format used as a bridge between different programming applications.
- ```JSON.parse()``` converts JSON (text/string) into a JavaScript value (object or array).
- ```JSON.stringify()``` converts JavaScript value (object or array) into a JSON (text/string).
- If I want to work with the data, I use ```JSON.parse()``` to convert the JSON string into a JavaScript object. If I want to send data to the backend, I use ```JSON.stringify()``` to convert the JavaScript object into a JSON string.
- Fake Store API is a mock REST API made for frontend practice.
- Every usable API has documentation.
- Even API users (frontend) must follow REST standards.
- In an API, the URL becomes an endpoint. Example 1: ("https://fakestoreapi.com
") This is the base URL, not an endpoint. Example 2: ("https://fakestoreapi.com/products/1
") This is an endpoint because it points to a specific resource.
- Response 200 means the request was successful.
- In JSON, all keys are strings.
- JSON values can be string, number, boolean, array, object, or null.
- If there is no value, do not include the key at all. Use null only when the value exists but is intentionally empty.
- There is a tool called JSON Server.
- JSON Server is not used in production; it is only for testing and development.
- You do not need to run as admin to use ```curl``` on Windows in most cases.
- In API there is response time.
- In the terminal, endpoints are links.
- You can use DOM manipulation with JSON data.
- A function can only use: Variables inside itself, Variables from outer scope, Variables passed as parameters, Values returned from other functions.
- Destructuring ```{ }``` appears on the left side of ```=``` as a pattern to extract values.
- Destructuring replaces the variable name — it does not sit beside it.
- ```const { name: username } = user;``` While destructuring the ```user``` object, take the name property and store it in a variable called ```username```.
- A parameter is just a variable that receives something.
- ```?.``` is optional chaining if data exists it gives data, if no data it prevents crash.
- A function exists after building it. The function will start working only after you call it and pass parameters into it. When parameters are passed in, the function runs. After it finishes running, it stops working. The function itself still exists, but the temporary values inside it disappear. You need to use return to send the processed value out of the function. If you want to store that value, you need to use a variable like const as a box to hold it. It is like a machine — it works when you input something into it. After it finishes processing, it stops. If you want the finished product from the machine, you need to return it, and if you want to keep it, you need a box to store it.
- In function in parameter with machine analogy if the machine expects material but you give nothing: In JavaScript → it receives undefined, In TypeScript → the supervisor stops you, With default value → machine uses backup material.
- A function contains instructions ```return``` is used to send a value outside the function.
- ```const``` inside a function stores a value temporarily within that function.
- Inside the function → placeholders (parameters). When calling the function → real values are passed in.
- You call the function once then store the returned value in a variable outside.
- A function can use variables from the scope where it is defined.
- Even if I destructure the function somewhere else, it can still use variables from its original scope
- A function can break when you call it without a parameter if it depends on that parameter in a way that requires a real value.
- You can directly destructure in function parameter using ```const x = ({ category, title }) => {console.log(category, title)}```. This is nested destructuring in parameter ```const x({category: {id, title}}) => {console.log(id, title)}```.
- ```Try...,catch``` need async function. If using promise style you need to use .catch().
- In Higher-Order Functions (HOFs) like filter(), pass the callback function itself: `carts.filter(expensiveItem)`. Do not call the callback function directly: `carts.filter(expensiveItem())` `filter()` expects a function and will call it later for each item in the array. Using `()` executes the function immediately and passes its result instead of the function.
- `filter()` passes each array item into the callback's first parameter. `item` represents the current element being processed, not the entire array. That's why you often see parameter names like: `items.filter((item) => ...)` `users.map((user) => ...)` `products.find((product) => ...)`. The parameter represents one element from the array at a time.

## Syntax
**Part of Statement**
```js
var a = 7 + "2";
```
- `var` is a keyword
- `a` is a variable name (identifier)
- `=` is the assignment operator
- `7 + "2"` is an expression
- `var a = 7 + "2";` is a variable declaration statement


**Variables**
- Example 1:
```js
let x;      // declaration
x = 5;      // assignment
x = 10;     // reassignment
```
- Example 2:
```js
let x = 5;  // declaration + initialization
x = 10;     // reassignment
```
- In both Example 1 and 2 `let` can be declare like that
- `const` must be initialized when declared. `const` cannot be reassigned.


**Part of Object**
```js
const user = {
    name: "John"
    hobbies: ["coding", "reading", "gym"]
};
```
- `user` is a variable
- `{}` is an object 
- `name and hobbies` are keys
- `"John"` and `["coding", "reading", "gym"]` are values
- `name: "John"` the entire thing is call Property
- `name: "John"` is a property of the object stored in the `user` variable


**Accessing an Array Inside an Object**
```js
const user = {
    name: "John"
    hobbies: ["coding", "reading", "gym"]
};
```
- `console.log(user.hobbies[0]);` Dot notation calling. `user.hobbies` get the array and `[0]` get the first item of that array
- `console.log(user["hobbies"][0]);` Bracket notation calling. `user["hobbies"] get the array and `[0]` get the first item of that array


**Compound assignment operator**
```js
let pocketMoney = 100;
const orangePrice = 20;

pocketMoney -= orangePrice;
// pocketMoney = pocketMoney - orangePrice;
console.log(pocketMoney); // Output - 80
```
- Compound assignment operators are shorthand for updating a variable
- `pocketMoney -= orangePrice;` is the same as `pocketMoney = pocketMoney - orangePrice;`


**Function**
```js
function findAge(year){
    let currentYear = 2025
    let age = currentYear - year
    return age
}

console.log(findAge(2002))
```
- `function` defines (declares) a function.
- `findAge` is the function name.
- `year` is a parameter.
- `Parameters` are variables that receive values when the function is called.
- `Argument` is actual value passed when calling the function.
- `return` sends a value back to the caller.


**Function returning value notes**
```js
function findAge(year){
    let currentYear = 2025
    let age = currentYear - year
    console.log(age)
}

console.log(findAge(2002))

const result = findAge(2002)

console.log(result)
```
- In this case `console.log(age)` inside the function display the calculated value not the returned value even I `console.log(findAge(2002))` which pass argument
- If I `console.log(result)` it will return undefined since it has no returned value


**Action in function**
```js
function greet(name){
     console.log(`Hello ${name}`)
}

console.log(greet("John"))
```
- `return` is not needed because the function is only performing an action and not returning the values. For example: console.log(),  alert(), localStorage.setItem("x", "5")
- The action is displaying the name in the console
- No value needs to be sent back to the caller
- In TypeScript term this action type is called `void`


**Conditional Statements**
```js
if (condition) {
    // runs if condition is true
} else {
    // runs if condition is false
}
```
- `if` checks whether a condition is `true` or `false`
- If the condition is true, the `if` block runs
- Otherwise, the `else` block runs


**Looping**
```js
let i = 1;

while (i <= 100) {
  console.log(i);
  i++;
}
```
- `let i = 1` Creates a variable i with value 1.
- `while (i <= 100)` Checks if i is less than or equal to 100. If true, enters the loop body.
- `console.log(i)` Prints the current value of i.
- `i++` Increases i by 1.
- Goes back to `while (i <= 100)` Checks the condition again with the new value.


**Parts of a `for` looping**
```js
for(let i = 100; i>= 1; i--){
    console.log(i);
  }
```
- `let i = 100` Runs once before the loop starts. Sets the starting value. Start the loop at 100.
- `i>= 1`Checked before every iteration. If true, continue. If false, stop.
- `i --` Runs after each iteration. Changes the value for the next loop. `i++` `i--` `i*`
- Start (let i = 100;) → Check (i>= 1) → Run → Update (i--)
          ↑                                       ↓
          ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←   


**Meaning of a `of` in `for...of` loop**
```js
const markArr = [
  "math: 90",
  "english: 85",
  "science: 95"
];

for (x of markArr){
    console.log(x);
}
```
- `for...of` is used to loop through iterable values like arrays and strings.
- `x` represents the current item in the array.
- `of` means "take values from".
- On each loop, the next value from `markArr` is assigned to `x`.
- It is shorter and easier to read than a traditional for loop.


**Meaning of a `in` in a `for...in` loop**
```js
const markObj = {
  math: 90,
  english: 85,
  science: 95
};

for (x in markObj){
    console.log(x);
}
```
- `for...in` is used to loop through the keys (property names) of an object.
- `x` represents the key.
- `in` means "take keys from".
- On each loop, the next value from `markObj` is assigned to `x`.
- It is useful for iterating through an object's properties.


**Sparse arrays**
```js
const arr = [];

arr[2] = "hello";

console.log(arr[0]); // undefined
console.log(arr[1]); // undefined
console.log(arr[2]); // "hello"
```
- JavaScript arrays can be sparse
- You can assign a value to an index that does not yet exist
- Missing indexes become `empty slots` (holes)
- The array length becomes the highest index + 1


**Object Property Shorthand**
```js
const age = 24;

const user = {
    age    
}
```
- Same as:
```js
const age = 24;

const user = {
    age: age    
}
```
- Because the `key` and the `variable name` are the same (age), JavaScript lets you shorten it
- You can access the property normally: `console.log(user.age)`


**Object literal**
```js 
const user = {
  name: "Sithu",
  age: 23
};
```
- ``` { } ``` = object literal.
- Inside it → key/value pairs.


**``` { } ``` as a code block**
```js
if (true) {
  console.log("hello");
}
```
- When ``` { } ``` appears after a keyword such as:
- ``` if ```
- ``` for ```
- ``` while ```
- ``` function ```
- …it means a code block, NOT an object.


**Hoisting**
- Example with var:
```js
console.log(x);

var x = 10; // Output is undefined
``` 
- JavaScript behaves roughly like:
```js
var x;

console.log(x);

x = 10; // Output is undefined
```
- Example with functions
```js
sayHello();

function sayHello() {
  console.log("Hello");
} // Output is Hello
```
- JavaScript treats it roughly like:
```js
function sayHello() {
  console.log("Hello");
}

sayHello(); // Output is Hello
```
- Hoisting is JavaScript moving declarations to be processed before code execution, which can make some variables and functions accessible before their declaration appears in the code.
- Hoisting is a JavaScript behavior, but relying on it is generally considered bad practice. It's better to declare variables and functions before using them.


**``` { } ``` in arrow function**
- Example 1: 
```js
const add = (a, b) => {
  return a + b;
};
```
- Example 2:
```js
const makeUser = () => ({ name: "Sithu" });
```
- In Example 1, there is a return keyword, this ```{}``` is a block, not an object.
- In Example 2, the parentheses force JS to treat ```{}``` as an object, not a block.


**``` { } ``` in Destructuring**
```js
const user = { name: "Sithu", age: 23 };
const { name } = user;
```
- This ```{ name }``` is not creating an object. It’s selecting the ``` name ``` key.


**```e``` (event) controller**
```js
const handleClickSub = (e) => {
  e.preventDefault();
  console.log(e.target);
};
```
- ```e``` (event) is controller to read or control its default behavior. If there is no event to control don't need ```e``` in function.


**Arrow functions**
- Example 1: 
```js
setX((prev) => {
  return prev + 1;
});
```
- Example 2:
```js
setX((prev) => (prev + 1));
```
- In Example 1, ``` { } ``` creates a function body (code block), so you must use ```return``` to send a value back.
- In Example 2, there is no code block, so the arrow function uses an implicit return and the expression result is returned automatically.


**Fetching data using async**
```js
async function fetchData() {
  const res = await fetch("https://fakestoreapi.com/products/1");
  const data = await res.json();
  console.log(data);
}

fetchData();
```
- Fetching data from API.


**Basic try...catch**
```js
try {
  // code that may throw an error
} catch (error) {
  // code that runs if an error happens
}
```
- Basic ```try...catch```. 


**Async / Await try...catch**
```js
try {
  const res = await fetch(url)
  const data = await res.json()
} catch (error) {
  console.error(error)
}
```
- Async / Await try...catch.


**try...catch throw**
```js
try {
  if (!user) {
    throw new Error("User not found")
  }
} catch (error) {
  console.log(error.message)
}
```
- ```try...catch throw```. ```throw``` is like a stop sign and after fix it can be safely removed.


**try...catch finally**
```js
try {
  // risky code
} catch (error) {
  console.error(error)
} finally {
  // always runs (cleanup, reset state, etc.)
}
```
- ```try...catch finally```. ```finally``` is run no matter what, whether an error occurs or not.


**Fetch data from API**
```js
const baseUrl = "http://localhost:8000"
fetch(`${baseUrl}/fruits`)
  .then((res) => res.json())
  .then((json) => console.log(json));
```
- This code is used to fetch data from an API (JSON Server or backend) and log the response data to the console.
- It asks the server for fruit data and prints it in the browser console.


**map()**
```js
const numbers = [1, 2, 3];
const doubled = numbers.map((n) => {
  return n * 2;
});
// doubled → [2, 4, 6]
```
- numbers = [1, 2, 3]
- n represents each value inside numbers
- n will be 1, then 2, then 3


**JS Principle — Array Method Callback vs Normal Function Parameters**
Example 1:
```ts
array.map((value, index) => {})
```
Example 2:
```ts
function createUser(name: string, age: number, city: string) {}
```
- In Example 1: Array iteration methods like `.map()`, `.forEach()`, `.filter()` automatically pass:
- ```value``` → current item
- ```index``` → position in array
- (optional) ```array``` → original array
- In Example 2: Normal functions do NOT receive automatic `index`
- Normal functions can have any number of parameters defined manually
- Array methods control the arguments
- Normal functions are controlled by the developer


**Storing values in map()**
```js
const numbers = [1, 2, 3];
const doubled = numbers.map(el => {
  el = el * 2;
  return el;
});
```
- map() does not automatically store calculated values.
- map() only stores what you return.
- If you calculate something but don’t return it, the value is thrown away.
- If you want to return the calculated value, you must return the result of the calculation. Writing ```el * 2; return el;``` will return the original value because the calculated result was never returned. You can either assign and return it ```el = el * 2; return el;``` or simply return the calculation directly ```return el * 2;```.
- The original array is not modified.


**Destructuring using {}**
```js
printUser({
  name: "Sithu",
  address: {
    city: "Yangon",
    zip: 12345,
    postal: {
      zip: "001",
      suite: "A1"
    }
  }
});

function printUser({
  name,
  address: {
    city,
    zip,
    postal: { zip: postalZip, suite }
  }
}) {
  console.log(name, city, zip, postalZip, suite);
}
```
- Once you destructure you can use destructured value directly.


**Object Property Shorthand**
```json
const user = "John";
const age = 23;

const person = { user, age };

// Equivalent to
const person = {
  user: user,
  age: age
};
```
- It is like ```{ variable } → { variable: variable }```


**Nested Looping**
```js
skill.map((category) => (
          <Card key={category.title} className="p-4">
            <CardContent className="space-y-4">
              <h3 className="text-lg font-semibold">{category.title}</h3>

              <div className="flex flex-wrap gap-2">
                {category.skills.map((item) => (
                  <Badge key={item} variant="secondary">
                    {item}
                  </Badge>
                ))}
              </div>
            </CardContent>
          </Card>
        ))
```
- You can loop inside another loop when dealing with nested data
- First ```.map()``` → loops through outer array (skill)
- Second ```.map()``` → loops through inner array (category.skills)


**Higher-Order Function (HOF) and Callback Function**
```js
const isCheap = (cart) => cart.price < 4000; // Callback Function
const result = carts.filter(isCheap); // filter is a Higher-Order Function
```
- Callback Function and Higher-Order Function (HOF) are not the same
- A Callback Function is a function passed as an argument to another function
- A Higher-Order Function (HOF) is a function that accepts another function as an argument or returns a function
- Baby explanation: A callback function = the function you give. A higher-order function = the function that receives another function


**Outer Function and Inner Function (Closure)**
```js
const carts = [
    { id: 1, item: "apple", price: "4000" },
    { id: 2, item: "banana", price: "2000" },
    { id: 3, item: "mango", price: "1000" },
  ],

const getPriceGreaterThan = (minPrice) => {
  return (item) => item.price > minPrice;
};
const callback = getPriceGreaterThan(3000);
carts.filter(callback);
```
- Outer parameter: `minPrice` = setup/configuration value
- Inner parameter: `item` = actual item being processed
- The outer function runs first and returns a new function
- The returned function is stored in `callback`
- When `callback` is called, the inner function runs
- Think of it like a vending machine. First interaction: `const callback = getPriceGreaterThan(3000)` You insert a coin -> Machine prepares itself -> Returns a button. Then: `carts.filter(callback)`. You press the button -> Machine gives result. Two separate interactions
- `carts.filter(getPriceGreaterThan(3000));` You can write like this instead of defining and storing the Outer function first. It is just you do two things in one expression
- The outer function must run first to create and return the inner function
- `carts.filter()` calls the callback function for each item in the array. Each item is passed into the callback's parameter. In this example, the current item is received by the `item` parameter. You can think of `filter()` doing something like: `callback(carts[0]); // item = carts[0], callback(carts[1]); // item = carts[1], callback(carts[2]); // item = carts[2]`
- Inner function remembers outer variables through closure. Example: The inner function remembers the value of `minPrice` from the outer function `minPrice` even after the outer function has finished running.
- Without a closure, the inner function would not be able to access `minPrice` after the outer function has finished running. Because JavaScript supports closures, the inner function remembers `minPrice` and can still access it later
- Baby explanation: Think of it like the inner function looking up to the outer function's parameter and borrowing that value whenever it needs it. Even if the outer function has already finished running, the inner function still remembers where that value came from and can keep using it
- Another Baby explanation: Think of outer giving inner a piece of paper: secret = "I love apples". When outer leaves the room, inner keeps the paper in its pocket. Later, inner can still read the paper even though outer is gone.

## Terminal Commands
### Terminal hotkeys

**Stop Terminal → Stop Running Command**
```bash
Ctrl + C
```
- Stops the running command in the terminal.


### Curl

**Curl**
```bash
curl "https://fakestoreapi.com/products/1"
```
- Using ```curl``` to test an API on Windows.


### Json server

**Install json server**
```bash
npm install -g json-server
```
- This command install json server.


**Check json server version**
```bash
json-server --version
```
- This command check json server version.


**Run json server**
```bash
json-server --watch data.json --port 8000
```
- This command watches data.json and runs JSON Server on port 8000.

## Tools
- Notes
