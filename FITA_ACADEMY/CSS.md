---

## 🎨 **CSS – Cascading Style Sheets**

CSS is used to **style HTML** — like colors, spacing, sizes, layouts, fonts, etc.

---

## ✅ **3 Ways to Use CSS**

| Type         | Example                                    | Use When…                              |
| ------------ | ------------------------------------------ | -------------------------------------- |
| **Inline**   | `<h1 style="color:red;">Title</h1>`        | For quick, one-time styling            |
| **Internal** | `<style> h1 { color:red; } </style>`       | For small websites or one-page styling |
| **External** | `<link rel="stylesheet" href="style.css">` | Best practice for larger projects      |

---

## 🌟 **CSS Selectors** (To apply styles)

### 1️⃣ **Tag Selector**

Targets all elements of a type

```css
p {
  color: blue;
}
```

### 2️⃣ **Class Selector**

Used for **multiple** elements

```css
.red-text {
  color: red;
}
```

HTML:

```html
<p class="red-text">Hello</p>
```

### 3️⃣ **ID Selector**

Used for **unique** elements only

```css
#main-title {
  color: green;
}
```

HTML:

```html
<h1 id="main-title">Hello</h1>
```

---

## 📌 **Selector Priority (Specificity)**

| Priority    | Type         | Example       |
| ----------- | ------------ | ------------- |
| 1️⃣ Highest | Inline Style | `style="..."` |
| 2️⃣         | ID           | `#id {}`      |
| 3️⃣         | Class        | `.class {}`   |
| 4️⃣ Lowest  | Tag          | `h1, p {}`    |

> 🔥 Use `!important` to override everything

```css
p {
  color: red !important;
}
```

---

## 📏 Units in CSS

| Unit | Means               | Example                                  |
| ---- | ------------------- | ---------------------------------------- |
| `px` | Pixels (fixed size) | `width: 300px;`                          |
| `vh` | Viewport height     | `height: 100vh;` (100% of screen height) |
| `%`  | Percentage          | `width: 80%;` (relative to parent)       |

### ✅ Common Rule:

* `width` → use `%` (responsive)
* `height` → use `px` (fixed), or `vh` (responsive)

---

## 📊 Media Queries (for responsiveness)

```css
@media screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

| Property    | Meaning                                         |
| ----------- | ----------------------------------------------- |
| `min-width` | Style applies if screen is **wider** than 600px |
| `max-width` | Style applies if screen is **less** than 600px  |

---

## 🗭 CSS Positioning

| Property           | What It Does                                          |
| ------------------ | ----------------------------------------------------- |
| `static` (default) | Normal flow                                           |
| `relative`         | Move element relative to its normal position          |
| `absolute`         | Positioned inside closest relative/absolute container |
| `fixed`            | Stays fixed on screen (e.g., navbars)                 |
| `sticky`           | Sticks while scrolling                                |

```css
div {
  position: relative;
  top: 20px;
  left: 30px;
}
```

---

## 🖼️ Background Properties

| Property                       | Description                               |
| ------------------------------ | ----------------------------------------- |
| `background-repeat`            | Repeat image in x & y                     |
| `repeat`                       | Default — tile the image                  |
| `no-repeat`                    | Show the image only once                  |
| `repeat-x`                     | Repeat horizontally                       |
| `repeat-y`                     | Repeat vertically                         |
| `background-attachment: fixed` | Sticks background in place when scrolling |

```css
body {
  background-image: url('bg.jpg');
  background-repeat: no-repeat;
  background-attachment: fixed;
}
```

---

## 📄 Layout Properties & Display

| Property        | Use Case                              |
| --------------- | ------------------------------------- |
| `display: flex` | Align items horizontally / vertically |
| `display: grid` | Create grid layouts                   |
| `block`         | Default for div, takes full width     |
| `inline`        | Sits next to other inline elements    |
| `none`          | Hides the element completely          |

**Flexbox alignment:**

```css
.parent {
  display: flex;
  justify-content: space-between; /* horizontal */
  align-items: center;            /* vertical */
}
```

---

## 🚶 Box Model & Sizing

### ✅ `box-sizing: border-box;`

* Makes padding & border count **inside** the element's size.
* Easier to manage spacing.

```css
div {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid black;
}
```

> ✅ Total width = 300px (not 300 + 20 + 5)

---

## 🔍 Text Styling & Decorations

| Property          | Example                       |
| ----------------- | ----------------------------- |
| `font-weight`     | `font-weight: bold;`          |
| `text-align`      | `text-align: center;`         |
| `line-height`     | `line-height: 1.7;`           |
| `text-decoration` | `text-decoration: underline;` |
| `text-transform`  | `text-transform: uppercase;`  |

---
### ✅ What is `text-transform` in CSS?

`text-transform` is a **CSS property** used to **change the case of text** — like making it **uppercase**, **lowercase**, or **capitalized**.

---

### 🧪 Example Values and What They Do:

| Value        | What It Does                                | Example                       |
| ------------ | ------------------------------------------- | ----------------------------- |
| `uppercase`  | Converts **all letters to CAPITAL**         | `hello` → `HELLO`             |
| `lowercase`  | Converts **all letters to small**           | `HELLO` → `hello`             |
| `capitalize` | Makes **first letter of each word capital** | `hello world` → `Hello World` |
| `none`       | **No change** to the text                   | `Hello` → `Hello`             |

---

### 💡 Simple Example:

```css
h1 {
  text-transform: uppercase;
}
```

This will make any `<h1>` text **completely uppercase**.

---

### ✅ Use Cases:

| Use Case                        | Value to Use |
| ------------------------------- | ------------ |
| Navigation menus (ALL CAPS)     | `uppercase`  |
| Terms & Conditions or footnotes | `lowercase`  |
| Headlines or titles             | `capitalize` |

---

### 🔄 Combined with Tailwind CSS?

```html
<p class="uppercase">this will be UPPERCASE</p>
<p class="lowercase">THIS WILL be lowercase</p>
<p class="capitalize">this will be Capitalize</p>
```

---

## ✨ Summary Quick Table:

| Concept              | Shortcut / Tip                   |
| -------------------- | -------------------------------- |
| Inline CSS           | `style="..."` (Highest priority) |
| Class                | `.classname` (Reusable)          |
| ID                   | `#idname` (Unique only)          |
| Width                | `%` for responsive               |
| Height               | `px` or `vh`                     |
| `!important`         | Force style override             |
| `position: absolute` | Removes from normal flow         |
| `background-repeat`  | Control image tiling             |
| `attachment: fixed`  | Fix background while scrolling   |
| `box-sizing`         | Include padding/border in width  |
| `text-decoration`    | Underline, overline, none        |

---

### ✅ What is `grid-template-columns`?

`grid-template-columns` is a **CSS property** used **with `display: grid`** to define **how many columns** your grid should have — and **how wide** each column should be.

---

### 💡 Basic Example:

```css
.container {
  display: grid;
  grid-template-columns: 200px 100px;
}
```

**What it means:**
You are creating a grid with **2 columns**:

* First column is **200px** wide
* Second column is **100px** wide

---

### 🧠 Responsive Version:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
```

* `fr` stands for **fraction** of available space.
* So `1fr 1fr` splits the space **equally into 2 columns**.

---

### 🧱 You can create any number of columns:

```css
grid-template-columns: 100px 100px 100px;
```

➡️ This will create **3 columns**, each **100px** wide.

Or use repeat:

```css
grid-template-columns: repeat(3, 100px);
```

➡️ Same as above — but shorter!

---

### 🔧 Use Cases:

* 🖼️ Image galleries
* 📦 Product cards
* 📊 Dashboard layouts
* 📁 File/folder view

---

### ✅ Summary:

| Value            | What It Does                    |
| ---------------- | ------------------------------- |
| `100px 200px`    | Fixed widths for each column    |
| `1fr 2fr`        | Flexible: ⅓ and ⅔ of space      |
| `repeat(3, 1fr)` | 3 equal-width columns           |
| `auto auto`      | Columns adjust to content width |


---

### ✅ `1. static` (Default)

**📌 What it means:**
Every element is in the normal flow of the page. No special positioning.

**🧠 Use case:**
Default for most elements like `<p>`, `<div>`, etc., unless you want to move them.

```css
position: static;
```

**📋 Example:** A paragraph that appears in order with other elements.

---

### ✅ `2. relative`

**📌 What it means:**
Element stays in the normal flow, **but you can move it** using `top`, `left`, `right`, `bottom`.

**🧠 Use case:**
You want to shift an element slightly without breaking the layout.

```css
position: relative;
top: 10px; left: 20px;
```

**📋 Example:** Nudging a button or icon without affecting nearby items.

---

### ✅ `3. absolute`

**📌 What it means:**
**Removed from normal flow**. Positioned **relative to the nearest positioned (non-static) ancestor**, or `body` if none.

**🧠 Use case:**
Placing tooltips, popups, dropdowns, badges, or elements exactly where you want.

```css
position: absolute;
top: 10px; left: 20px;
```

**📋 Example:** A dropdown menu under a button.

---

### ✅ `4. fixed`

**📌 What it means:**
Fixed **to the browser window**. Doesn't move when scrolling.

**🧠 Use case:**
Sticky headers, floating buttons, or back-to-top arrows.

```css
position: fixed;
bottom: 20px; right: 20px;
```

**📋 Example:** A chat button that stays at the bottom-right corner always.

---

### ✅ `5. sticky`

**📌 What it means:**
**Behaves like `relative`**, but becomes `fixed` when you scroll past a point.

**🧠 Use case:**
Sticky headers or section titles that stick while scrolling.

```css
position: sticky;
top: 0;
```

**📋 Example:** A navbar that stays at the top **only while scrolling** past it.

---

### 🔁 Summary Table

| Value    | Stays in flow? | Moves on scroll? | Positioned relative to      |
| -------- | -------------- | ---------------- | --------------------------- |
| static   | ✅ Yes          | ✅ Yes            | Normal flow                 |
| relative | ✅ Yes          | ✅ Yes            | Itself                      |
| absolute | ❌ No           | ✅ Yes            | Nearest positioned parent   |
| fixed    | ❌ No           | ❌ No             | Viewport (browser window)   |
| sticky   | ✅ Yes          | 👇 Switches      | Itself until sticky trigger |


---

### ✅ **Code:**

```css
@media screen and (max-width: 750px) {
  /* CSS rules go here */
}
```

---

### ✅ **In Simple Terms:**

* **`@media`** = "Only apply the CSS inside this block **in certain conditions**"
* **`screen`** = Apply it when viewing on a **screen** (like a phone, tablet, laptop)
* **`max-width: 750px`** = Apply when the screen size is **750 pixels wide or smaller**

---

### 🧠 Think of it like this:

> "**If the screen is small (like a mobile or tablet), then use this CSS instead of the default styling.**"

---

### ✅ **Use Case Example:**

Imagine a website has a wide navigation bar for desktop. But on phones, it looks messy.
So, we use media query to:

* **Hide desktop navbar**
* **Show mobile menu icon** (hamburger menu)

```css
@media screen and (max-width: 750px) {
  .desktop-navbar {
    display: none;
  }

  .mobile-navbar {
    display: block;
  }
}
```

---

### ✅ Common Use Cases:

| Scenario                        | Why Use `@media screen and (max-width)`    |
| ------------------------------- | ------------------------------------------ |
| 💻 Desktop vs 📱 Mobile layouts | Adjust layout to fit small screens         |
| 📷 Image scaling                | Resize or hide large images                |
| 🧭 Navigation                   | Replace horizontal menu with hamburger     |
| ✍️ Font resizing                | Make fonts more readable on phones         |
| 🎨 Hide or stack columns        | Convert 2- or 3-column layouts to 1-column |

---

### 🔁 1. **transform + transition**

```css
box {
  transform: translateX(100%);
  transition: transform 1s;
}
```

* `transform: translateX(100%)`: Moves the element 100% to the right (based on its width).
* `transition: transform 1s`: When the transform value changes, it smoothly moves over 1 second.

👉 **Use this when the movement is triggered by something**, like a hover or class change.

---

### 🎬 2. **@keyframes animation (from → to)**

```css
@keyframes slideDown {
  from {
    transform: translateY(-300%);
  }
  to {
    transform: translateY(0%);
  }
}

box {
  animation: slideDown 1s;
}
```

* This automatically moves the element **from `translateY(-300%)` (off screen above)**
  **to `translateY(0%)` (its original place)**.
* It runs once over 1 second.

👉 **Use this when you want the animation to start automatically**, like when the page loads.

---

### ✅ Quick analogy:

Think of `transform` as *where to move*,
`transition` as *how smoothly to move*,
and `@keyframes` as *a custom animation path with start (from) and end (to)*.

---

### ✅ 1. `.box` Animation (`@keyframes box`)

```css
animation-name: box;
animation-duration: 10s;
```

* You’ve defined steps at `24%`, `25%`, `50%`, and `75%`.
* Animates **position**, **rotation**, **size**, and **shape**:

  * Moves right (via `padding-left`)
  * Rotates 90 degrees
  * Changes width to 15%
  * Turns into a circle using `border-radius: 50%`

---

### ✅ 2. `.boll .inner` Animation (`@keyframes planet`)

```css
animation-name: planet;
animation-duration: 8s;
```

* Rotates the planet image inside the outer red circle:

  * Rotates 360° halfway
  * Snaps back to 0° at 51%
  * Then rotates 360° again by end

🌀 **Effect:** Makes it look like the planet is spinning.

---

### ✅ 3. `.ballcolor` Animation (`@keyframes rotate`)

```css
animation-name: rotate;
animation-duration: 8s;
```

* Rotates the whole border (outer ring) on the Y-axis halfway:

  * `rotateY(360deg)` makes it flip horizontally.

🌀 **Effect:** Creates a 3D spinning illusion of the circle.

---

### ✅ 4. `.slide` Animation (`@keyframes slideright`)

```css
animation-name: slideright;
animation-duration: 4s;
```

```css
from {
  transform: translateX(900%);
}
to {
  transform: translateY(0%);
}
```

* Starts off-screen to the right (900% to the right)
* Then slides into its original position

🟪 **Effect:** Slide-in effect from right to center.

---

### ✅ 5. `.rotate` Animation (`@keyframes rotate`)

```css
transform: rotateX(360deg);
```

* Rotates the element around the X-axis halfway (like flipping forward)
* Affects just the inner content

🌀 **Effect:** A 3D vertical spin (like flipping a coin forward).

---

### ✅ 6. `.glow` Animation (`@keyframes glow`)

```css
transform: scale(0.5, 0.5);
```

* Shrinks the element to half size at 50%
* No `from` or `to`, so it bounces back automatically

✨ **Effect:** A glowing/pulsing shrink animation.

---

### ✅ 7. `.fade` Animation (`@keyframes fade`)

```css
opacity: 0;
```

* Makes the element invisible (opacity 0) at 50%
* Will return to full visibility by default

🌫️ **Effect:** Quick blink/fade-out-and-in effect.

---

### ✅ 8. `.box_glow` Animation (`@keyframes box_glow`)

```css
box-shadow: 0px 0px 50px black;
```

* Adds a glowing shadow at 50%
* `animation-iteration-count: infinite;` means it repeats forever

🌟 **Effect:** Constant glowing or blinking box

---


## 🧠 What Is `animation-timing-function`?

It controls **how the speed of an animation changes over time** — whether it moves steadily, starts slow and gets fast, or bounces.

### Imagine a car 🚗 going from point A to B:

* Does it move at the **same speed**?
* Does it **start slow**, then **go fast**?
* Does it **slow down** before stopping?

That's what `animation-timing-function` does!

---

## 🎯 Common Values (with Examples):

| Value          | Meaning                                                           | Animation Style              |
| -------------- | ----------------------------------------------------------------- | ---------------------------- |
| `linear`       | Moves at a constant speed (like a train 🚄)                       | Even motion, no acceleration |
| `ease`         | Starts slow → speeds up → ends slow (default)                     | Smooth and natural           |
| `ease-in`      | Starts slow, then speeds up (like taking off ✈️)                  | Accelerates at the beginning |
| `ease-out`     | Starts fast, then slows down (like braking 🚗)                    | Decelerates at the end       |
| `ease-in-out`  | Slow at start & end, fast in the middle (like a rollercoaster 🎢) | Natural start and stop       |
| `cubic-bezier` | Custom curve for advanced timing (control exactly how it moves)   | Advanced control             |
| `steps(n)`     | Jumps in `n` steps (used in sprite animations or counters)        | Jerky, step-by-step effect   |

---

## 🔧 Example:

```css
@keyframes slide {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(500px);
  }
}

.box {
  width: 100px;
  height: 100px;
  background: red;
  animation: slide 2s ease-in-out;
}
```

🟢 `ease-in-out` makes it:

* Start slow,
* Speed up in the middle,
* Slow down at the end.

---

## 🔍 Visual Analogy:

* `linear` → ———— (same speed)
* `ease-in` → \_\_/—— (slow start)
* `ease-out` → ——\_\_ (slow end)
* `ease-in-out` → \_*/——\_* (slow → fast → slow)

---


