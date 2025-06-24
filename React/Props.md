
## 🔹 What Are Props?

Props (short for "properties") are **inputs to React components** — like function parameters. They allow **data to be passed from parent to child components**.

---

## 📋 Important Features & Rules About Props

### 1. ✅ **Props are Read-Only**

You **can’t modify props** directly in the child component.

```js
props.name = 'Aswin'; ❌ // This will cause an error
```

> If you need to change data, use `useState`.

---

### 2. ✅ **Props Can Be Any Data Type**

You can pass:

* **Strings** → `name="Aswin"`
* **Numbers** → `age={20}`
* **Booleans** → `isLoggedIn={true}`
* **Objects** → `user={{ name: 'Aswin', age: 20 }}`
* **Functions** → `onClick={handleClick}`
* **JSX/Components** → `children={<Component />} `

---

### 3. ✅ **Destructuring Props (Cleaner Way)**

Instead of using `props.name`, you can **destructure**:

```js
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

---

### 4. ✅ **Props Are Passed One-Way (Top to Bottom)**

Data flows **from parent to child** — not the other way.

```js
<App>
  <ChildComponent someProp="Hi" />
</App>
```

If a child needs to update the parent’s state → you **pass a function** as a prop.

---

### 5. ✅ **Default Props (Optional Values)**

You can define **default values** in case props are not passed:

```js
function Greet({ name = "Guest" }) {
  return <h1>Welcome, {name}</h1>;
}
```

---

### 6. ✅ **Using `props.children`**

You can wrap content inside components and access it using `children`.

```js
function Card(props) {
  return <div className="card">{props.children}</div>;
}

// Usage:
<Card><p>This is inside the card</p></Card>
```

---

### 7. ✅ **Prop Names Must Match**

As you asked earlier — if you write:

```jsx
<Component data={info} />
```

Then you **must use** `props.data` (or `({ data })`) in the child.

---

## 🧠 Summary Table

| Rule/Feature       | Explanation                             |
| ------------------ | --------------------------------------- |
| Read-only          | Props can't be changed in child         |
| One-way data flow  | Parent → Child only                     |
| Can pass any data  | Strings, numbers, objects, functions... |
| Must match names   | Prop names must be the same in child    |
| Default values     | Use `= value` to set defaults           |
| Use props.children | To pass nested JSX/components           |
| Destructuring      | Clean and simple way to use props       |

---


---

# 🔧 React Props 

---

## 1️⃣ What are Props?

* Props (short for **properties**) are **read-only** values passed from a **parent** to a **child** component.
* Props allow components to be **dynamic** and **reusable**.

---

## 2️⃣ Sending Props from Parent to Child

### ✅ Parent Component

```jsx
<Child name="Sam" age={23} />
```

### ✅ Child Component

```jsx
function Child(props) {
  return (
    <>
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
    </>
  );
}
```

✅ The `props` object contains all values passed from the parent.

---

## 3️⃣ Props Syntax

| Data Type | How to Pass in JSX            |
| --------- | ----------------------------- |
| String    | `name="Sam"`                  |
| Number    | `age={23}`                    |
| Boolean   | `isLoggedIn={true}`           |
| Object    | `user={{ id: 1, name: "A" }}` |
| Array     | `items={[1, 2, 3]}`           |
| Function  | `onClick={handleClick}`       |

---

## 🧠 Key Points

* Props are **immutable** – they **cannot be changed** by the child component.
* Used to **customize child components**.
* Always passed **top-down** (from parent to child).

---



Let's walk through multiple **parent-child props examples** — each one step-by-step — in **very simple terms**.

---

## 🔰 Example 1: Passing a **String** from Parent to Child

### ✅ Parent (`App.jsx`)

```jsx
import Welcome from './Welcome';

function App() {
  return <Welcome name="Aswin" />;
}

export default App;
```

### ✅ Child (`Welcome.jsx`)

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Welcome;
```

⏳ **Output** → `Hello, Aswin!`

---

## 🔰 Example 2: Passing a **Number and Boolean**

### ✅ Parent

```jsx
<Details age={21} isStudent={true} />
```

### ✅ Child

```jsx
function Details(props) {
  return (
    <p>
      Age: {props.age}, Status: {props.isStudent ? "Student" : "Not a Student"}
    </p>
  );
}
```

⏳ **Output** → `Age: 21, Status: Student`

---

## 🔰 Example 3: Passing a **Function as a Prop** (Callback)

### ✅ Parent

```jsx
function App() {
  function handleClick() {
    alert('Button clicked!');
  }

  return <Button onClick={handleClick} />;
}
```

### ✅ Child

```jsx
function Button({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}
```

⏳ **Output** → Shows alert when button is clicked.

---

## 🔰 Example 4: Passing an **Object**

### ✅ Parent

```jsx
const user = { name: 'Aswin', role: 'Developer' };

<UserCard user={user} />
```

### ✅ Child

```jsx
function UserCard({ user }) {
  return <p>{user.name} is a {user.role}</p>;
}
```

⏳ **Output** → `Aswin is a Developer`

---

## 🔰 Example 5: Passing JSX using `props.children`

### ✅ Parent

```jsx
<Card>
  <h2>Welcome!</h2>
  <p>This is inside the card</p>
</Card>
```

### ✅ Child

```jsx
function Card(props) {
  return <div className="card">{props.children}</div>;
}
```

⏳ **Output** → A card with a heading and paragraph inside

---

## 🔰 Example 6: Controlled Form Inputs

### ✅ Parent

```jsx
function App() {
  const [name, setName] = useState("");

  function updateName(newName) {
    setName(newName);
  }

  return (
    <>
      <FormInput name={name} onNameChange={updateName} />
      <p>Your name is: {name}</p>
    </>
  );
}
```

### ✅ Child

```jsx
function FormInput({ name, onNameChange }) {
  return (
    <input
      type="text"
      value={name}
      onChange={(e) => onNameChange(e.target.value)}
    />
  );
}
```

⏳ **Output** → Whatever you type will update the parent state.

---

## 🧠 Summary

| Data Type | What’s Passed From Parent      | How It’s Used in Child |
| --------- | ------------------------------ | ---------------------- |
| String    | `"Aswin"`                      | `props.name`           |
| Number    | `21`                           | `props.age`            |
| Boolean   | `true`                         | `props.isStudent`      |
| Function  | `() => alert()`                | `props.onClick()`      |
| Object    | `{ name: "A", age: 20 }`       | `props.user.name`      |
| Children  | `<Component>stuff</Component>` | `props.children`       |

---

### lifting state up

In **React**, if a **child component needs to update or communicate data to the parent**, the parent passes **a callback function** as a **prop** to the child. The child can then **call that function** and pass the desired data back to the parent.

---

### 🔄 How It Works:

* **Parent defines a function** (e.g., `handleChildData`)
* That function **updates the parent’s state**
* The parent **passes this function to the child** as a prop
* The **child calls the function**, sending data back "up"

---

### ✅ Example:

#### Parent Component

```jsx
import React, { useState } from 'react';
import Child from './Child';

function Parent() {
  const [dataFromChild, setDataFromChild] = useState('');

  const handleChildData = (value) => {
    setDataFromChild(value);
  };

  return (
    <div>
      <h2>Data from child: {dataFromChild}</h2>
      <Child onSendData={handleChildData} />
    </div>
  );
}
```

#### Child Component

```jsx
import React from 'react';

function Child({ onSendData }) {
  const sendData = () => {
    onSendData('Hello from Child!');
  };

  return <button onClick={sendData}>Send Data to Parent</button>;
}

export default Child;
```

---

### 💡 Summary:

* Yes, **you need to use a function in the parent and pass it to the child**.
* This is called **“lifting state up”**, a common React pattern to share data between child and parent.






---

### ✅ **General Rule:**

> **We don’t use props to get data *from* a child component.**
>
> Instead, we pass a **function as a prop to the child**, and the child calls it to send data back.

---

### 🔄 How data flows in React:

| Direction      | How It Works                                                                        |
| -------------- | ----------------------------------------------------------------------------------- |
| Parent ➝ Child | **Use props** to send data or functions                                             |
| Child ➝ Parent | **Use a function (callback) passed as a prop**, and the child calls it to send data |

---

### ✅ Example: Child sends data to parent

```jsx
// Parent
function Parent() {
  function handleDataFromChild(data) {
    console.log("Got data:", data);
  }

  return <Child onSendData={handleDataFromChild} />;
}
```

```jsx
// Child
function Child({ onSendData }) {
  return (
    <button onClick={() => onSendData("Hello from Child")}>
      Send Data
    </button>
  );
}
```

* ❌ You’re **not** using `props` to receive anything from the child.
* ✅ You're using a **function** passed from the parent to let the child report back.


---

### ✅ In the Parent Component, You Typically Pass:

1. **State values**

   * Example: current count, selected option, user input
2. **Functions (handlers)**

   * Example: `onClick`, `onChange`, custom callbacks to update parent state

You pass these as **props** to the child.

---

### 👇 Example

```jsx
// ✅ Parent
function Parent() {
  const [message, setMessage] = useState("");

  function updateMessage(newMessage) {
    setMessage(newMessage);
  }

  return <Child text={message} onUpdate={updateMessage} />;
}
```

```jsx
// ✅ Child
function Child({ text, onUpdate }) {
  return (
    <>
      <p>{text}</p>
      <button onClick={() => onUpdate("Hello from child")}>
        Send Back
      </button>
    </>
  );
}
```

---

### 💡 Key Takeaway

✅ In Parent ➝ Pass:

* ✅ State variables (to **show** something in child)
* ✅ Functions (to **control** or **update** from child)

❌ You **don't** get values *from* child using props directly.

Instead:

* ✅ You let the **child trigger a function** to send data **up**.

---
