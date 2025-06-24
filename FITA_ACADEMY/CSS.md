
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

## 🎯 **CSS Selectors** (To apply styles)

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

---

### ✅ Common Rule:

* `width` → use `%` (responsive)
* `height` → use `px` (fixed), or `vh` (responsive)

---

## 📐 Media Queries (for responsiveness)

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

## 🧭 CSS Positioning

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

## ✅ Summary Quick Table:

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

---

