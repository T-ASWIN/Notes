In your code:

```jsx
<label htmlFor="email">Email</label>
<input id="email" type="email" name="email" />
```

`htmlFor` is the **React version of the HTML attribute `for`** in `<label>`.

* In plain HTML, you’d write:

  ```html
  <label for="email">Email</label>
  ```
* In React (JSX), `for` is a reserved JavaScript keyword, so React renamed it to `htmlFor`.

**Purpose:**
It links the `<label>` to a specific form input using the `id` of that input.
When linked:

* Clicking the label will focus or activate the associated input.
* Helps accessibility tools like screen readers correctly read the label for that field.

So in your example:

* `<label htmlFor="email">` is tied to `<input id="email">`.
* If a user clicks **"Email"**, the cursor will jump into the email text box.


---

### In your code:

```js
setEnteredValues((prevValues) => ({
  ...prevValues,
  [identifier]: value,
}));
```

* `identifier` is **not** literally `"identifier"` — it’s a variable that contains a string like `"email"` or `"password"`.
* `[identifier]` tells JavaScript:

  > “Use the value stored in the variable `identifier` as the property name.”

So if:

```js
identifier = "email";
value = "test@example.com";
```

The object will become:

```js
{
  email: "test@example.com"
}
```

---

### Without square brackets

If you wrote:

```js
{ identifier: value }
```

It would literally create:

```js
{ identifier: "test@example.com" }
```

…which is **wrong** because the property would be `"identifier"`, not `"email"`.

---

### Why it’s important for your form

This allows one single `handleInputChange` function to update **any field** in the form without hardcoding `setEmail` or `setPassword` separately.

---


## **What is FormData?**

Think of `FormData` as a **special JavaScript object** designed for working with `<form>`s.
It:

* Reads all the inputs inside a form.
* Pairs each **name** with its **value**.
* Works well for sending form data to a server (especially in `fetch` or AJAX).

---

## **How to create FormData**

You can create it like this:

```js
const fd = new FormData(formElement);
```

* `formElement` → a reference to the `<form>` DOM node.
* In your case: `event.target` **is the form** inside `onSubmit`.

---

## **Getting a single value**

```js
fd.get("email");
```

Returns the **first** value for the `name="email"` field.

Example:

```html
<input name="email" value="john@example.com">
```

`fd.get("email")` → `"john@example.com"`

---

## **Getting multiple values**

If a field can have **multiple selections** (like checkboxes or multi-select), use:

```js
fd.getAll("acquisition");
```

Example:

```html
<input type="checkbox" name="acquisition" value="google" checked>
<input type="checkbox" name="acquisition" value="friend" checked>
```

`fd.getAll("acquisition")` → `["google", "friend"]`

---

## **Converting all data into an object**

By default, `FormData` isn’t a plain object, so to get a nice `{ key: value }` object, you can do:

```js
const data = Object.fromEntries(fd.entries());
```

Example:
If your form has:

```html
<input name="email" value="john@example.com">
<input name="role" value="student">
```

You get:

```js
{
  email: "john@example.com",
  role: "student"
}
```

---

## **Your code explained**

```js
const fd = new FormData(event.target); // Creates FormData from the submitted form

const acquisitionChannel = fd.getAll("acquisition"); // Gets all selected checkboxes for "acquisition"

const data = Object.fromEntries(fd.entries()); // Turns all form fields into a JS object

data.acquisition = acquisitionChannel; // Replaces acquisition field with array instead of single value

console.log(data);
```

So if you filled:

* Email: `"abc@gmail.com"`
* Role: `"student"`
* Acquisition: `"google"` and `"friend"`

You’d see:

```js
{
  email: "abc@gmail.com",
  password: "123456",
  "confirm-password": "123456",
  "first-name": "John",
  "last-name": "Doe",
  role: "student",
  acquisition: ["google", "friend"],
  terms: "on"
}
```

---
`onBlur` is an event that **runs when an input loses focus** — meaning the user clicks or tabs away from it.

---

### Example:

1. You click in the **Email** input → it’s **focused**.
2. You type something.
3. You click somewhere else (or press Tab) → the input **loses focus** → **`onBlur` fires**.

---

### Why use it?

* Good for **validation after user finishes typing** (so you don’t show errors while they’re still typing).
* Can be used to save data when leaving a field.

---

### In your code:

```jsx
onBlur={() => handleInputBlur("email")}
```

When the user leaves the Email field:

* `handleInputBlur("email")` runs.
* This sets `didEdit.email` to `true`, meaning *"Yes, the user interacted with this field"*.
* Then your validation (`emailIsValid`) checks:

```js
didEdit.email && !enteredValues.email.includes("@")
```

So the **"Please enter valid email"** message only appears **after** the user leaves the field without typing a valid email.

---

Here’s a list of the **most commonly used built-in HTML5 form validation attributes** that work in **all major web browsers** (Chrome, Edge, Firefox, Safari, etc.):

---

### **Basic Validation**

| Attribute   | What it does                               | Example                                   |
| ----------- | ------------------------------------------ | ----------------------------------------- |
| `required`  | Field must not be empty.                   | `<input type="text" required>`            |
| `minlength` | Minimum number of characters allowed.      | `<input type="text" minlength="5">`       |
| `maxlength` | Maximum number of characters allowed.      | `<input type="text" maxlength="10">`      |
| `pattern`   | Custom regex pattern the value must match. | `<input type="text" pattern="[A-Za-z]+">` |

---

### **Number Validation**

| Attribute | What it does                                 | Example                            |
| --------- | -------------------------------------------- | ---------------------------------- |
| `min`     | Minimum numeric value allowed.               | `<input type="number" min="1">`    |
| `max`     | Maximum numeric value allowed.               | `<input type="number" max="100">`  |
| `step`    | Step interval allowed (useful for decimals). | `<input type="number" step="0.5">` |

---

### **Type-Specific Validation**

| Input Type                                 | Built-in validation                         | Example                                  |
| ------------------------------------------ | ------------------------------------------- | ---------------------------------------- |
| `type="email"`                             | Must be a valid email format.               | `<input type="email">`                   |
| `type="url"`                               | Must be a valid URL format.                 | `<input type="url">`                     |
| `type="tel"`                               | No fixed validation, but can use `pattern`. | `<input type="tel" pattern="[0-9]{10}">` |
| `type="date"` / `datetime-local` / `month` | Valid date/time only.                       | `<input type="date">`                    |

---

### **Other Useful Attributes**

| Attribute  | What it does                                           | Example                                |
| ---------- | ------------------------------------------------------ | -------------------------------------- |
| `multiple` | Allows multiple values (e.g., multiple files, emails). | `<input type="file" multiple>`         |
| `accept`   | Restricts file types in file inputs.                   | `<input type="file" accept="image/*">` |
| `size`     | Visible width of the field (not a limit).              | `<input type="text" size="30">`        |
| `readonly` | Makes the field uneditable but still submitted.        | `<input type="text" readonly>`         |
| `disabled` | Makes the field uneditable and **not** submitted.      | `<input type="text" disabled>`         |

---

💡 **Browser behavior:**

* These validations work **before** the form is submitted.
* If a field fails validation, the browser shows a built-in error message (which you can customize with JavaScript).

---



