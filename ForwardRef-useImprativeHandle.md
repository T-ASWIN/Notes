## 🔄 `forwardRef()` – Pass Ref to Child Component

If a parent wants to access something **inside** a child component (like an input), use `forwardRef`.

```jsx
import React, { forwardRef } from 'react';

const MyInput = forwardRef((props, ref) => {
  return <input ref={ref} />;
});
```

Now the parent can do:

```jsx
const inputRef = useRef();
<MyInput ref={inputRef} />
```

---

## 🔧 `useImperativeHandle()` – Control What the Parent Can Access

Normally, when you pass a `ref`, it points to a DOM node (like `<input>`).

But sometimes, you want the parent to call **custom functions** inside the child — like `open()`, `focus()`, `reset()`.

That’s where `useImperativeHandle()` comes in:

---

### ✍️ Syntax:

```jsx
useImperativeHandle(ref, () => {
  return {
    focusInput: () => {
      inputRef.current.focus();
    },
    clearInput: () => {
      inputRef.current.value = '';
    }
  };
});
```

---

### 🔍 Simple Use Case: Parent Focuses Input in Child

```jsx
// Child.jsx
import React, { useRef, forwardRef, useImperativeHandle } from 'react';

const CustomInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focusInput() {
      inputRef.current.focus();
    }
  }));

  return <input ref={inputRef} />;
});

export default CustomInput;
```

```jsx
// Parent.jsx
import React, { useRef } from 'react';
import CustomInput from './CustomInput';

function App() {
  const inputComponentRef = useRef();

  function handleClick() {
    inputComponentRef.current.focusInput(); // Calls method inside child
  }

  return (
    <>
      <CustomInput ref={inputComponentRef} />
      <button onClick={handleClick}>Focus the Input</button>
    </>
  );
}
```

---

## ✅ Summary

| Concept                 | Use It When You Want To...                             |
| ----------------------- | ------------------------------------------------------ |
| `useRef()`              | Store DOM refs or variables without causing re-renders |
| `forwardRef()`          | Allow parent to attach `ref` to a custom component     |
| `useImperativeHandle()` | Let parent call specific methods on the child          |


---

### 🧠 Simple Explanation:

| Concept                                  | When to Use                                                                             |
| ---------------------------------------- | --------------------------------------------------------------------------------------- |
| `useRef()`                               | To **access DOM elements** like input, dialog, video, etc. ✅ Must know                  |
| `forwardRef()` + `useImperativeHandle()` | Only when a **parent wants to control a child component's internal DOM** or **methods** |

---

### 📌 When *not* to use it:

If you're building:

* Basic apps
* Forms
* Buttons, cards, inputs
* Lists, counters, etc.

✅ You **do NOT need** `forwardRef` or `useImperativeHandle`.

---

### ✅ When you SHOULD learn it:

You’ll need it when:

* A parent wants to **control something inside a child** (like a modal, or focus a text box).
* You are building **reusable libraries or components**.
* You want to **expose custom methods** (like `.open()`, `.close()`, `.scrollTo()`) from child to parent.

---
