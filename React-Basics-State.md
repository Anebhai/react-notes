# React Basics and State Jonas React Chapter 5 and Chapter 6

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

# <im> Most of the notes of 5th chapter is in One Note please use that.

---

## <qs> Drawsbacks of && conditional

1. If you are testing for array.length and if array is zero it will get rendered first as its falsy value.
2. If you test for empty array i.e without considering array.length than you get ul rendered on the dom which is not needed.
   3.So ternary operation is preferred.

---

## <qs> If and else conditional

1. If and else conditional are preferred when you want an entire big component to render instead of small piece of logic.

2. It is maily used for multiple returns.

---

## <qs> Ternary Conditionals for small logic but it is most often used.

---

# <im> From 6th Chapter

## <qs> `onClick` attribute in React:

**Explanation**:

- `onClick` is a React event handler that responds to user clicks on elements.
- You pass a function reference, not a function call, to ensure it's executed when the element is clicked.

**Code Snippet**:

```javascript
import React from "react";

function MyComponent() {
  const handleClick = () => {
    alert("Button clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
}

export default MyComponent;
```

In this example, when the button is clicked, the `handleClick` function is executed, displaying an alert message.

---

## <qs> **State in React**:

-Certainly, here are concise bullet-point notes on the concepts of "State" and "State Variables" in React:

**State in React**:

- Represents dynamic data that can change over time.
- Affects a component's behavior and rendering.
- Managed using a JavaScript object within a component.
- Enables dynamic and interactive components.
- Triggers component re-rendering when data changes.

**State Variables in React**:

- Individual pieces of data within a component's state.
- Specific aspects of the component's data.
- Declared using `useState` (functional components) or `this.state` (class components).
- Example: `count` representing a count value that can change.
- React automatically updates the UI when state variables change.

- **Example (Functional Component)**:

  ```javascript
  import React, { useState } from "react";

  function MyComponent() {
    const [count, setCount] = useState(0);

    const increment = () => {
      setCount(count + 1);
    };

    return (
      <div>
        <p>Count: {count}</p>
        <button onClick={increment}>Increment</button>
      </div>
    );
  }
  ```

- **Example (Class Component)**:

  ```javascript
  import React, { Component } from "react";

  class MyComponent extends Component {
    constructor(props) {
      super(props);
      this.state = {
        count: 0,
      };
    }

    increment = () => {
      this.setState({ count: this.state.count + 1 });
    };

    render() {
      return (
        <div>
          <p>Count: {this.state.count}</p>
          <button onClick={this.increment}>Increment</button>
        </div>
      );
    }
  }
  ```

In both examples, `count` is a state variable representing the count value, and it can change over time. React keeps track of these state variables and automatically updates the component's UI when they change.

## <as> In the code snippet provided, the term "state" refers to the concept of state management in React, which involves storing and managing data within a React component. "State" is not a variable or object itself but rather a concept or mechanism.

---

## <qs> Usestate Hook;

Here are 5 concise bullet points for your notes about `useState` in React:

- `useState` is a built-in React hook and also a function.
- It's used for managing state in functional components.
- When called, it returns an array with the current state and a state setter function.
- Array destructuring is commonly used to assign these values.
- React re-renders the component when the state is updated.

```javascript
import React, { useState } from "react";

function Counter() {
  // Array destructuring on the left-hand side (LHS) of '='
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

---

## <qs> When using `useState` in React, there are a few things that are not allowed or are discouraged:

1. **Calling `useState` conditionally**: You should always call `useState` at the top level of your functional component, not inside conditional statements or loops. This ensures that the order of hooks remains consistent between renders.

   ```javascript
   // Allowed
   function MyComponent() {
     const [count, setCount] = useState(0);
     // ...
   }

   // Not allowed (conditionally calling useState)
   function MyComponent() {
     if (someCondition) {
       const [count, setCount] = useState(0); // Causes issues
     }
     // ...
   }
   ```

2. **Using `useState` in nested functions**: You should not use `useState` inside nested functions or closures within your component. Instead, you can pass the state and state updater function as props to child components or use the `useEffect` hook for side effects.

   ```javascript
   // Allowed (passing state as props)
   function MyComponent() {
     const [count, setCount] = useState(0);

     const handleIncrement = () => {
       setCount(count + 1);
     };

     return <ChildComponent count={count} onIncrement={handleIncrement} />;
   }

   // Not recommended (using useState in a nested function)
   function MyComponent() {
     const [count, setCount] = useState(0);

     useEffect(() => {
       // Using state inside a useEffect callback is allowed
       setCount(count + 1); // Allowed but often not the intended behavior
     }, []);
     // ...
   }
   ```

3. **Mutating state directly**: You should not mutate the state variable directly. Instead, always use the state updater function provided by `useState` to update the state. Mutating state directly can lead to unexpected behavior.

   ```javascript
   // Not allowed (mutating state directly)
   function MyComponent() {
     const [count, setCount] = useState(0);

     const increment = () => {
       count++; // Mutating state directly is not allowed
     };

     return (
       <div>
         <p>Count: {count}</p>
         <button onClick={increment}>Increment</button>
       </div>
     );
   }
   ```

Following these guidelines helps ensure that state management with `useState` in React works correctly and predictably.

In the below picture dont mutate the state directly i.e without setter function for object also.

![object bad practice](/essential-react-imgs/object-bad.png)

### <im> Remember always use useState() fucntion or hook at top of the component.

---

### For simple onClick funtion we can do in inline only as shown below.

```js
// function handleClose() {
// setIsOPen(!isOpen);
// }
return (
<>
<button className="close" onClick={() => setIsOPen(!isOpen)}>
&times;
</button>


```

---

## <qs> Updating State, Direct updating and updating with callback function(recommende)

Certainly, here are the updated notes with code snippets that include direct updating examples for comparison, as well as the note about not calling functions directly in `onClick`:

1. **Updating State Based on Current State in React**:

   - It's common to update state variables based on their current values.
   - Directly updating state without considering current values can lead to issues.

2. **Using Callback Functions**:

   - Best practice is to employ callback functions when updating state based on its current value.
   - Callback functions receive the current state value as an argument.

3. **Example - Updating `step` State**:

   - Instead of directly setting `setStep(s + 1)`, use a callback function `(s) => s + 1`.
   - This ensures the new state depends on the current state value.
   - Comparison: Direct update example with potential issues:

   ```javascript
   // Direct update (not recommended)
   setStep(step + 1);
   function handleNext() {
     if (step < 3) {
       // setStep((s+1)
       // setStep((s+1) ...This will  work once second function call it will not work. so not a good option when we need tto update in future or work with teams.

       setStep((s) => s + 1);
       // setStep((s) => s + 1);
       // This is the better option for collaboration and maintainability if future.
     }
   }
   ```

4. **Benefits of Callbacks**:

   - Callbacks offer safer and more reliable state updates.
   - Particularly useful for complex applications or collaborative projects.

5. **Applying the Concept to `isOpen` State**:

   - Similar approach applied to updating the `isOpen` state using a callback.
   - Comparison: Direct update example with potential issues:

   ```javascript
   // Direct update (not recommended)
    <button className="close" onClick={() => setIsOpen(!isOpen)}>
   ;
   ```

6. **Sample Code**:

   - Example of using a callback function when updating state in a button click event:

   ```javascript
   {/* Using callback function */}
   <button className="close" onClick={() => setIsOpen((is) => !is)}>
   ```

   ```javascript
   {
     /* Using callback function */
   }
   function handleNext() {
     if (step < 3) {
       setStep((s) => s + 1);
     }
   }
   ```

7. **Note on `onClick` and Function Calls**:

   - It's recommended not to call functions directly in `onClick`, such as `alert()`.
   - Use callback functions to maintain consistency and best practices.

8. **Summary**:
   - Utilizing callback functions for state updates in React ensures correctness and maintainability.
   - Recommended practice, especially for larger projects and collaborative development.
   - <im> It's advisable not to directly invoke functions like alert() or handleNext() within onClick attributes.
     - <im> Instead, provide the function reference or use callback functions within another function for a more consistent approach.

---

## <qs> "one component, one state"

"one component, one state" encourages a modular and maintainable approach to building React applications. It promotes the idea that components should be self-contained and manage their own data, leading to cleaner, more organized code. However, for sharing state between distant or unrelated components, global state management solutions are available.

---

### <qs> Counter logic for small counter app

<im> Logic for getttng dates.

```javascript
const date = new Date();
date.setDate(date.getDate() + count);
const dateString = date.toDateString();
```

<im> Nested Ternary Operation.

```jsx
<p>
  <span>
    {count === 0
      ? "Today is "
      : count < 0
      ? `${Math.abs(count)} days ago was `
      : `${count} days from Today is`}
  </span>
  <span>{dateString}</span>
</p>
```

```jsx
<span>
  {count === 0 && `Today is `}
  {count > 0 && `${count} days from today is `}
  {count < 0 && `${Math.abs(count)} days ago was `}
</span>
```

---

<as>The below logic also works with && logical operation.
so remember for quick logic you can use,

1. Ternary operations. Nested can also be done for checking three conditions.
2. If else to return a full component also if else for multiple returns.
3. && can also be used for multiple small logic return

## <qs> Contditonal styling with style prop notice 3 brackets 1 for for ternary, 1 each for pseudo if and pseudo else

```js
<div style={packed ? { textDecoration: "line-through" } : {}}>

```

## <im>If pseudo else bracket is not included you get mapping error.

The below one is for class name styling.One Js Mode and Template literal js mode.

![ClassName Styling](/essential-react-imgs/className.png)

---

## <qs> Array.from technique to get number of array items.

```js
<select>
  {Array.from({ length: 20 }, (_, i) => i + 1).map((op) => (
    <option value={op} key={op}>
      {op}
    </option>
  ))}
</select>
```

---

## <qs>In single page application like react we can submit the form without reloading.

---

### <im> onClick works only on click while onSubmit works on both ciick and submit. So instead of listening on the add button we listen at form itself.

---

## <qs> Controlled Element and working with forms

<as>Input elements like select and input have their own state.

Creating a controlled element in React involves three key steps:

1. **Initialize a State Variable**: You need to initialize a state variable in your component's state to store the value of the controlled input element. This state variable will be used to track and update the input's value.

2. **Set the Value Attribute**: You should set the `value` attribute of the input element to the corresponding state variable from step 1. This makes the input element controlled, meaning its value is always derived from the component's state.

3. **Handle Input Changes**: Implement an event handler function that listens for changes in the input element (e.g., `onChange` for text input). When the input value changes, update the state variable initialized in step 1 with the new value.

Here's an example of these three steps in a React component:

```jsx
function Form() {
  const [description, setDescription] = useState("");
  const [quantity, setQuantity] = useState(1);

  function handleSubmit(e) {
    e.preventDefault();
    const newItem = { description, quantity, packed: false, id: new Date() };
    console.log(newItem);
    setDescription("");
    setQuantity(1);
  }
  return (
    <form className="add-form" onSubmit={handleSubmit}>
      <h3>What do you need for your 😎 Trip??</h3>
      <select
        value={quantity}
        onChange={(e) => setQuantity(Number(e.target.value))}
      >
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>
      <input
        type="text"
        placeholder="item..."
        value={description}
        onChange={(e) => {
          console.log(e.target);
          setDescription(e.target.value);
        }}
      />
      <button>Add</button>
    </form>
  );
}
```

---

### <as> // Console logging in attritubes of jsx put brackets after arrow

Also on every key stroke the value of input state changes this can be noticed in chrome console tool.

```js
<input
  type="text"
  placeholder="item..."
  value={description}
  onChange={(e) => {
    // console logging in attritubes of jsx put brackets after arrow
    console.log(e.target);
    setDescription(e.target.value);
  }}
/>
```

## <qs> After Control three steps i.e creating state variable, value, onchange.

4. The fourth step is to make object using `handlesubmit`
5. From this you can push object as an item of an arraylist.

---

## <qs>Flashcard Logic

```js
function FlashCards() {
  const [selectedId, setSelectedId] = useState(null);

  function handleclick(id) {
    setSelectedId(id !== selectedId ? id : null);
  }

  return (
    <>
      <div>
        <h1>flashcards</h1>{" "}
        <div className="flashcards">
          {questions.map((question) => (
            <div
              key={question.id}
              className={question.id === selectedId ? "selected" : ""}
              onClick={() => handleclick(question.id)}
            >
              <p>
                {question.id === selectedId
                  ? question.answer
                  : question.question}
              </p>
            </div>
          ))}
        </div>
      </div>
    </>
  );
}
```

---

## <qs> Comparison of call back funtions for onchange attributes, onclick attributes, for reset function and function which has id.

```js
// Separate function coz of complex logic i.e not so much complex but neither simple to code in online.
function handleclick(id) {
  setSelectedId(id !== selectedId ? id : null);
}

// see how we use the callback function for onclick with id
onClick={() => handleclick(question.id)}
```

```js
// Here check on change and onclick
<button onClick={() => setCount((s) => s - step)}>-</button>
          <input
            type="number"
            value={count}
            onChange={(e) => {
              setCount(Number(e.target.value));
            }}
```

```js
// Here check on change and onclick
<button onClick={() => setCount((s) => s - step)}>-</button>
          <input
            type="number"
            value={count}
            onChange={(e) => {
              setCount(Number(e.target.value));
            }}
```

```js
// Here check for reset.
// Separate function because we need two pieces of state.
function handleReset() {
  setStep(1);
  setCount(0);
}

<button onClick={handleReset}>Reset</button>;
```

## <qs> What i learnt with faraway app is that

1. List Sate should be in parent component.
2. Form state should in form component itself where you can do inverse data flow by calling the additem function inside submit function.
   3.OnSubmit i.e with handle submit will capture your all pieces of state which you can transfer to the parent component using additem function call.

---

