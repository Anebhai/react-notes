# Essential Js for React

<style>
qs{ color: #ff1493 }
as{ color: #66C1BB }
sy{ color: #ffff00 }
im{ color: #2CDD0D }
od{ color: #FF7F50 }
st{ color: #3EB489 }
ar{ color: #9A8873}
cg{ color: #D3A121}
at{ color: #D3D3D3}
</style>

### <qs>Remember custom html tags for notetaking for Markdown Format:</qs>

- <qs>Question? and new topic:</qs>
- <as>Answer\*:</as>
- <sy>Syntax^</sy>
- <im>Important!</im>
- <od> Old method$</od>
- <st>story&</st>
- <ar>any other%</ar>
- <cg>Chatgpt+:</cg>
- <at>Newsection@</at>

## <qs> React Router Link.

https://blog.webdevsimplified.com/2022-07/react-router/

---

## <qs> Destructuring in Js

### <im> Just remember {}, and [] for on LHS of equals sign. This new destructuring makes easy and less lines of code.

## ![old way](/essential-react-imgs/obj%20.png)

<as> **Destructuring in Arrays:**

- Destructuring allows you to extract values from arrays and assign them to variables in a concise way.
- It uses square brackets `[...]` to match the structure of the array.

**Example:**

```javascript
const [first, second, third] = [1, 2, 3];
console.log(first); // Outputs 1
console.log(second); // Outputs 2
console.log(third); // Outputs 3
```

<as> **Destructuring in Objects:**

- Destructuring can also be used with objects to extract values and assign them to variables.
- It uses curly braces `{...}` to match the structure of the object.

**Example:**

```javascript
const { name, age } = { name: "Alice", age: 30 };
console.log(name); // Outputs "Alice"
console.log(age); // Outputs 30
```

<as> **Destructuring with Default Values:**

- You can set default values in case the extracted value is `undefined`.
- Useful for handling optional properties.

**Example:**

```javascript
const { name = "Anonymous", age = 25 } = {};
console.log(name); // Outputs "Anonymous"
console.log(age); // Outputs 25
```

<as> **Nested Destructuring:**

- You can destructure nested objects or arrays by nesting the destructuring patterns.

**Example:**

```javascript
const {
  data: { name, age },
} = { data: { name: "Bob", age: 35 } };
console.log(name); // Outputs "Bob"
console.log(age); // Outputs 35
```

Destructuring is a powerful feature in JavaScript that simplifies the process of extracting values from data structures, making your code more concise and readable. It's commonly used in ES6 and later versions of the language.

---

## <qs> Rest and Spread Operator in Js

<as> **Rest in Function Calls (Collecting Arguments):**

- Rest operator (`...`) in function calls collects multiple arguments into a single array.
- It gathers or "rests" the arguments.
- Useful for handling variable numbers of function arguments.

**Example:**

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

sum(1, 2, 3, 4); // Returns 10
```

<as> **Rest for Collecting Last Elements of Arrays:**

- Rest operator (`...`) in array destructuring collects the remaining elements of an array into a new array.
- It allows you to separate or "rest" elements from the source array.

**Example:**

```javascript
const sourceArray = [1, 2, 3, 4, 5];
const [first, ...rest] = sourceArray;

console.log(first); // Outputs 1
console.log(rest); // Outputs [2, 3, 4, 5]
```

<as> **Spread (Spreading Out Elements):**

- Spread operator (`...`) in array literals or function calls spreads elements from an array or object into another array or object.
- It separates or "spreads out" elements.
- Useful for combining arrays, objects, or cloning.

**Example:**

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

console.log(arr2); // Outputs [1, 2, 3, 4, 5]
```

<as> **Spread in Function Calls (Passing Arguments):**

- Spread operator (`...`) in function calls spreads array elements as individual arguments to the function.
- It separates or "spreads out" the elements when calling a function.
- Useful for passing elements of an array as function arguments.

**Example:**

```javascript
function add(a, b, c) {
  return a + b + c;
}

const numbers = [1, 2, 3];
const result = add(...numbers); // Equivalent to add(1, 2, 3)

console.log(result); // Outputs 6
```

## <im> In summary, the rest operator collects multiple arguments or the remaining elements into an array, while the spread operator spreads elements from an array or object into another, allowing for versatile handling of data in JavaScript.

---

## <qs> Optional chaining and nullish coalescing operator in JavaScript:

<as> **Optional Chaining (?.):**

- **Purpose:** Optional chaining is used to safely access properties or methods of an object without causing an error if the property or method is undefined or null.
- **Syntax:** It's denoted by the `?.` operator.
- **Usage:** Useful for navigating deeply nested objects or when dealing with potentially missing properties.
- **Example:**

```javascript
const person = {
  name: "Alice",
  address: {
    city: "New York",
  },
};

const city = person?.address?.city; // Safely accesses 'city'
```

<as> **Nullish Coalescing Operator (??):**

- **Purpose:** The nullish coalescing operator is used to provide a default value when a variable is null or undefined, not when it's falsy (<im>e.g., empty string or zero).
- **Syntax:** It's denoted by the `??` operator.
- **Usage:** Helpful for setting default values or handling cases where missing values should be replaced with a predefined alternative.
- **Example:**

```javascript
const userCount = 0; // Could be 0, null, or undefined
const defaultCount = userCount ?? 10; // Assigns 10 as the default when userCount is null or undefined
```

In summary, optional chaining helps avoid errors when accessing nested properties or methods, while the nullish coalescing operator provides a way to specify default values for variables that might be null or undefined, without affecting other falsy values. These operators enhance JavaScript's ability to handle complex data structures and default value assignments.

<im> Below we have used both optional chaining and Nullish Coalescing operator, Nullish operator helps us to give default values.

![Null and optional chaining ](/essential-react-imgs/Null.png)

---

## <qs> Return an object from the `map` method without using an explicit `return` statement

In JavaScript, you can return an object from the `map` method without using an explicit `return` statement by using concise arrow functions and wrapping the object literal in parentheses. Here's an example:

```javascript
const array = [1, 2, 3, 4, 5];

const newArray = array.map((item) => ({
  value: item,
  doubled: item * 2,
}));

console.log(newArray);
```

In this example, we use an arrow function `(item) => ({ ... })` to implicitly return an object literal with properties `value` and `doubled` for each element in the `array`. The parentheses around the object literal are necessary to ensure it's treated as a block and not confused with a function body.

The resulting `newArray` will contain objects with the specified properties based on the elements of the original array:

```javascript
[
  { value: 1, doubled: 2 },
  { value: 2, doubled: 4 },
  { value: 3, doubled: 6 },
  { value: 4, doubled: 8 },
  { value: 5, doubled: 10 },
];
```

This approach allows you to create and return objects from the `map` method without explicitly using the `return` keyword.

---

## <qs> `Slice` before the `sort` method to not mutate the original array.

In React, We use `slice` before the `sort` method. However, I can provide an explanation for when this might be done and how to make notes about it:

**Using `slice` before `sort` in React:**

- **Example**:

  ```javascript
  // Suppose you have an array of numbers in React state
  const originalArray = [3, 1, 2, 4, 5];

  // Create a sorted copy of the array
  const sortedArray = originalArray.slice().sort((a, b) => a - b);

  // Now 'sortedArray' contains [1, 2, 3, 4, 5], while 'originalArray' remains unchanged
  ```

By using `slice` before `sort`, you adhere to React's principles of immutability and avoid unintended changes to your state or props, ensuring that your application behaves predictably.

---

## <qs> Array methods that mutate the original array

In JavaScript, several array methods can mutate the original array. It's important to be aware of these methods when working with arrays, especially if you want to maintain immutability. Here are some commonly used array methods that modify the original array:

1. **`push()`**: Adds one or more elements to the end of an array.

   ```javascript
   const arr = [1, 2, 3];
   arr.push(4); // Modifies 'arr' to [1, 2, 3, 4]
   ```

2. **`pop()`**: Removes the last element from an array.

   ```javascript
   const arr = [1, 2, 3];
   arr.pop(); // Modifies 'arr' to [1, 2]
   ```

3. **`shift()`**: Removes the first element from an array.

   ```javascript
   const arr = [1, 2, 3];
   arr.shift(); // Modifies 'arr' to [2, 3]
   ```

4. **`unshift()`**: Adds one or more elements to the beginning of an array.

   ```javascript
   const arr = [1, 2, 3];
   arr.unshift(0); // Modifies 'arr' to [0, 1, 2, 3]
   ```

5. **`splice()`**: Adds or removes elements from an array at a specified index.

   ```javascript
   const arr = [1, 2, 3, 4];
   arr.splice(1, 2); // Modifies 'arr' to [1, 4]
   ```

6. **`reverse()`**: Reverses the order of elements in an array in place.

   ```javascript
   const arr = [1, 2, 3];
   arr.reverse(); // Modifies 'arr' to [3, 2, 1]
   ```

7. **`sort()`**: Sorts the elements of an array in place, by default in ascending order.

   ```javascript
   const arr = [3, 1, 2];
   arr.sort(); // Modifies 'arr' to [1, 2, 3]
   ```

8. **`fill()`**: Changes all elements in an array to a static value.

   ```javascript
   const arr = [1, 2, 3];
   arr.fill(0); // Modifies 'arr' to [0, 0, 0]
   ```

9. **`copyWithin()`**: Copies a sequence of elements within the array to a new position in the same array.

   ```javascript
   const arr = [1, 2, 3, 4];
   arr.copyWithin(0, 2); // Modifies 'arr' to [3, 4, 3, 4]
   ```

When working with arrays and striving for immutability, you should avoid using these methods to modify the original array. Instead, consider creating new arrays with the desired changes to maintain the integrity of the original data.

---

## <qs> Immutable Map, Filter, Reduce.

Certainly, here's a table summarizing the purpose, immutability, and code snippets for `map`, `filter`, and `reduce`. I've also included information about the initial value parameter for `reduce`:

| Method     | Purpose                                    | Immutability               | Code Snippet                                                                                                                                                       | Initial Value for `reduce` |
| ---------- | ------------------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------- |
| `map()`    | Transform array elements to a new array.   | Does not mutate the array. | `javascript const numbers = [1, 2, 3]; const doubled = numbers.map((num) => num * 2); // 'doubled' contains [2, 4, 6], 'numbers' remains [1, 2, 3] `               | N/A                        |
| `filter()` | Create a new array with filtered elements. | Does not mutate the array. | `javascript const numbers = [1, 2, 3, 4, 5]; const evens = numbers.filter((num) => num % 2 === 0); // 'evens' contains [2, 4], 'numbers' remains [1, 2, 3, 4, 5] ` | N/A                        |
| `reduce()` | Accumulate array elements into a result.   | Does not mutate the array. | `javascript const numbers = [1, 2, 3, 4, 5]; const sum = numbers.reduce((total, num) => total + num, 0); // 'sum' is 15, 'numbers' remains [1, 2, 3, 4, 5] `       | `0` (initial sum value)    |

<im> Note: The `reduce` method takes an optional initial value as its second parameter. This initial value is used as the starting value for the accumulator (`total` in the example), and it can be any value you choose. In the provided example, `0` is used as the initial sum value. If the initial value is not provided, the first element of the array is used as the initial accumulator value.

Certainly, here are concise notes about `map`, `filter`, and `reduce` in JavaScript, emphasizing that they do not mutate the original array:

1. **`map()`**:

   ```javascript
   const numbers = [1, 2, 3];
   const doubled = numbers.map((num) => num * 2);
   // 'doubled' contains [2, 4, 6], while 'numbers' remains [1, 2, 3]
   ```

2. **`filter()`**:

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const evens = numbers.filter((num) => num % 2 === 0);
   // 'evens' contains [2, 4], while 'numbers' remains [1, 2, 3, 4, 5]
   ```

3. **`reduce()`**:

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const sum = numbers.reduce((total, num) => total + num, 0);
   // 'sum' is 15, 'numbers' remains [1, 2, 3, 4, 5]
   ```

These array methods are powerful tools for working with arrays while preserving the immutability of the original data. They are essential in functional programming and make code more predictable and maintainable.

<im> In summary, while map allows you to <as> transform or alter elements</as> and return a new array, filter and find are primarily focused on returning specific elements from the original array that meet certain conditions. All three methods are valuable for different use cases and provide different levels of control over the data you extract or transform.

---

## <qs> Working with immutable arrays, Add, delete, update(alter) the arrays.

```js
// ?New Book.

const newBook = {
  id: 7,
  title: "Sacred Games",
  publicationDate: "2007-08-01",
  author: "Nawaz",
  genres: ["fantasy", "high-fantasy", "novel", "fantasy fiction"],
  hasMovieAdaptation: true,
  pages: 1501,
};

// ?Adding new book object to the books array.

const booksAfterAdd = [...books, newBook];
console.log(booksAfterAdd);
// console.log(books);

// ?Deleting book object from the books array.

const booksAfterDelete = books.filter((book) => book.id !== 3);
console.log(booksAfterDelete);

// ?Updating the books object.

const booksAfterUpdate = books.map((book) =>
  // ?The elements in which the `id` is equal to 2 are fully transformed by spreading and altering all of their properties, while the elements with `id` values other than 2 remain unchanged and are returned as-is.
  book.id === 2 ? { ...book, pages: 2005 } : book
);

console.log(booksAfterUpdate);
```

---

## <qs> Fetch, Asynchronous javascript and promises.

JavaScript is inherently synchronous, executing code sequentially. However, it supports asynchronous programming to handle tasks like network requests without blocking the main thread with promises, callbacks and Async/ Await.

- **Promises**: Promises are a structured way to manage asynchrony. They represent a future value, and you can chain `.then()` to handle success and `.catch()` for errors. `.then` is itself a Promise method.

- **Callbacks**: Functions passed as callbacks execute when asynchronous tasks finish. While functional, they can lead to callback hell when nested deeply.

- **Async/Await**: Introduced in ES2017, async/await simplifies async code, making it appear synchronous. `async` functions return Promises, and `await` pauses execution until Promises resolve.

```js
fetch("https://jsonplaceholder.typicode.com/todos/")
  .then((res) => res.json())
  .then((data) => console.log(data));
```

In the above provided code, `fetch` initiates a network request, returning a Promise. `.then` chains process responses asynchronously. Remember, `.then` is also a <im> Promise method </im>, making it versatile for handling async operations.

### <as> In the async/await method, you can directly assign the values within the parentheses of the fetch function as variables using the const statement for improved code organization."

```js
async function getTodos() {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos/");
  const data = res.json();
  console.log(data);
  return data;
}
```

#### <as> To remember fetch function with then statement : ''Fat rabbit jockeys in den.''

---

## <qs> Async await comparison with try and catch.

The provided code demonstrates the use of both `async/await` and the `fetch` technique to make an asynchronous network request and log the data. Here's the difference between the two techniques:

1. **Async/Await**:

   - **Usage**: `async/await` is a modern JavaScript syntax for working with asynchronous code. It allows you to write asynchronous code in a more synchronous-like fashion, making it easier to read and maintain.

   - **Syntax**: You define an `async` function and use the `await` keyword inside the function to pause execution until a Promise is resolved. This makes it appear as if the code is executing sequentially.

   - **Error Handling**: You can use `try/catch` blocks to handle errors gracefully when using `async/await`.

   - **Example**:

     ```javascript
     async function getTodos() {
       try {
         const res = await fetch("https://jsonplaceholder.typicode.com/todos/");
         const data = await res.json();
         console.log(data);
         return data;
       } catch (error) {
         console.error("An error occurred:", error);
       }
     }

     getTodos();
     ```

2. **Fetch**:

   - **Usage**: `fetch` is an API for making network requests in JavaScript. It returns a Promise that resolves to the response from the server. It's a lower-level API compared to `async/await`.

   - **Syntax**: You use the `fetch` function to initiate a network request and then chain `.then()` to handle the response asynchronously. It's a more explicit way to work with Promises.

   - **Error Handling**: You can use `.catch()` to handle errors when using `fetch`.

   - **Example**:

     ```javascript
     function getTodos() {
       fetch("https://jsonplaceholder.typicode.com/todos/")
         .then((res) => res.json())
         .then((data) => {
           console.log(data);
         })
         .catch((error) => {
           console.error("An error occurred:", error);
         });
     }

     getTodos();
     ```

In summary, `async/await` provides a more concise and readable way to work with Promises, making asynchronous code appear similar to synchronous code. On the other hand, the `fetch` technique is a lower-level API for making network requests and handling Promises using explicit `.then()` and `.catch()` chains. Both techniques have their use cases, with `async/await` often being preferred for readability and maintainability.
