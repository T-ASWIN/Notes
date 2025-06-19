# 🔁 React: Refs & Portals (Simplified)

---

## 1️⃣ Fragments Refresher

In React, JSX must return **only one root element**.

❌ Invalid:

```jsx
return (
  <h2>Hello</h2>
  <p>World</p>
);
```

✅ Valid (Using Fragment):

```jsx
import { Fragment } from 'react';

return (
  <Fragment>
    <h2>Hello</h2>
    <p>World</p>
  </Fragment>
);

// Or shorter:
return (
  <>
    <h2>Hello</h2>
    <p>World</p>
  </>
);
```

---

## 2️⃣ `useState` vs `useRef` – Example Code

### A) Simple `useState` Example

```jsx
import { useState } from 'react';

export default function Player() {
  const [inputdata, setInputData] = useState();

  function playerData(e) {
    setInputData(e.target.value);
  }

  return (
    <section id="player">
      <h2>Welcome {inputdata}</h2>
      <p>
        <input type="text" value={inputdata} onChange={playerData} />
        <button onClick={playerData}>Set Name</button>
      </p>
    </section>
  );
}
```

---

### B) Conditional Greeting with Submit Button

```jsx
import { useState } from 'react';

export default function Player() {
  const [inputdata, setInputData] = useState();
  const [submitted, setSubmitted] = useState(false);

  function playerData(e) {
    setSubmitted(false);
    setInputData(e.target.value);
  }

  function handleClick() {
    setSubmitted(true);
  }

  return (
    <section id="player">
      <h2>Welcome {submitted ? inputdata : 'unknown entity'}</h2>
      <p>
        <input type="text" value={inputdata} onChange={playerData} />
        <button onClick={handleClick}>Set Name</button>
      </p>
    </section>
  );
}
```

---

### C) Using `useRef` Instead of State for Input

```jsx
import { useState, useRef } from 'react';

export default function Player() {
  const playerName = useRef();
  const [inputdata, setInputData] = useState();

  function handleClick() {
    setInputData(playerName.current.value);
  }

  return (
    <section id="player">
      <h2>Welcome {inputdata ?? 'unknown entity'}</h2>
      <p>
        <input type="text" ref={playerName} />
        <button onClick={handleClick}>Set Name</button>
      </p>
    </section>
  );
}
```

---

## 3️⃣ What is `useRef`?

- `useRef()` is a **React Hook** that returns a mutable object: `{ current: ... }`
- It does **not** cause re-renders when changed.
- Useful to **read values from DOM** or **persist data** without causing re-renders.

✅ Great for:
- Reading values from `<input>` fields
- Accessing DOM elements
- Storing interval IDs or timers

---

### 🧠 Key Differences: `useState` vs `useRef`

| Feature            | `useState`                           | `useRef`                              |
|--------------------|---------------------------------------|----------------------------------------|
| Triggers re-render | ✅ Yes                                | ❌ No                                  |
| DOM access         | ❌ No                                | ✅ Yes (via `.current`)               |
| Use case           | UI data                              | Non-UI data, DOM refs                 |
| Stores value?      | ✅ Yes                                | ✅ Yes                                 |
| Reactive?          | ✅ Yes (React updates UI)            | ❌ No (Only stores reference)         |

---

## 4️⃣ Example: Trigger File Input via Button

```jsx
import React from 'react';

function App() {
  const fileRef = React.useRef();

  function handleClick() {
    fileRef.current.click();
  }

  return (
    <div id="app">
      <p>Please select an image</p>
      <input type="file" accept="image/*" ref={fileRef} style={{ display: 'none' }} />
      <button onClick={handleClick}>Pick Image</button>
    </div>
  );
}

export default App;
```

---

Would you like to learn about **Portals** next?

