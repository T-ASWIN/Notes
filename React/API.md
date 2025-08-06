
---

## ✅ What is an API?

### 🧠 Simple Meaning:

> An **API (Application Programming Interface)** is like a **waiter** in a restaurant.
> You ask for something (like movie info), and it brings it from the kitchen (the server) to you (your app).

---

## 🎬 In your case:

You're using the **TMDB (The Movie Database)** API — it gives you access to data like:

* Popular movies
* Search results
* Posters
* Descriptions, etc.

To access it, you need:

* A **URL** (where to ask)
* An **API key** (your ID to access it)

---

## 🔍 Your Code Breakdown

```js
const API_KEY = "182147589380cbb3388845fad6cb62ec";
const BASE_URL = "https://api.themoviedb.org/3";
```

* 🔑 `API_KEY` → your personal key to use the API
* 🌐 `BASE_URL` → main URL to access TMDB

---

### 📦 Function 1: `getPopularMovies`

```js
export const getPopularMovies = async () => {
  const response = await fetch(`${BASE_URL}/movie/popular?api_key=${API_KEY}`);
  const data = await response.json();
  return data.results;
};
```

🔁 What this does:

1. 📡 Makes a request to:
   `https://api.themoviedb.org/3/movie/popular?api_key=...`
2. 📥 Gets the data in JSON format
3. 📃 Returns only the `results` array (popular movies list)

---

### 🔎 Function 2: `searchMovies`

```js
export const searchMovies = async (query) => {
  const response = await fetch(
    `${BASE_URL}/search/movie?api_key=${API_KEY}&query=${encodeURIComponent(query)}`
  );
  const data = await response.json();
  return data.results;
};
```

🔁 What this does:

1. Takes your search word (example: `"avatar"`)
2. Adds it to the API URL:

   ```
   https://api.themoviedb.org/3/search/movie?api_key=...&query=avatar
   ```
3. Makes a request, gets the response
4. Returns only the search results

---

## ✅ Summary:

| Function              | Purpose                                 |
| --------------------- | --------------------------------------- |
| `getPopularMovies()`  | Gets a list of trending/popular movies  |
| `searchMovies(query)` | Searches for movies based on user input |
| `API_KEY`             | Required to access the TMDB API         |
| `fetch()`             | Sends the request to the API            |
| `await`               | Waits for the response before moving on |

---

## ✅ What is `await`?

### 🧠 Simple Meaning:

> `await` means **“wait here until I get the result.”**

You use it when doing something **slow** — like:

* Fetching data from the internet (API call)
* Reading a file
* Waiting for a timer

---

### 👀 Example (Real Life):

```js
const response = await fetch("https://api.example.com/movies");
```

💬 This means:

> "Go get the movies from the website.
> While you're doing that, wait here — don't run the next line yet."

---

### ⏱ Why Use `await`?

Without `await`, the code moves on **before** the data is ready — and causes bugs.

---

## 🧪 Without `await` (wrong):

```js
const response = fetch("https://..."); // doesn't wait
const data = response.json(); // ❌ error! response not ready yet
```

---

## ✅ With `await` (correct):

```js
const response = await fetch("https://...");
const data = await response.json(); // waits until it's ready
```

---

### 🔁 Only Works Inside `async` Functions

That’s why you see:

```js
export const getPopularMovies = async () => {
  const response = await fetch(...);
  const data = await response.json();
  return data.results;
};
```

Because:

* `async` allows you to use `await`
* `await` makes sure you get the data **before moving forward**

---

## 🧭 Summary

| Keyword | Meaning                                          |
| ------- | ------------------------------------------------ |
| `async` | Says "this function has something slow inside"   |
| `await` | Says "wait here for the result before moving on" |

---

## 🌐 What is HTTP?

**HTTP** stands for **HyperText Transfer Protocol**. It's the **language that web browsers and web servers use to communicate** with each other.

* It helps transfer **HTML pages, images, videos, or data** between a **client** (like your browser) and a **server** (where websites live).
* Though it was originally made for websites, HTTP is now also used for apps, APIs, and even **machine-to-machine communication**.

---

## 🔄 How HTTP Works

HTTP follows a **client-server model**:

1. A **client** (like Chrome, Firefox, or a mobile app) sends a **request** to a **server** (where the data lives).
2. The **server responds** with the requested information (like a webpage, image, or data).

### Example:

When you type `www.google.com` and press enter:

* Your browser sends an HTTP **GET request** to Google’s server.
* The server replies with the **Google homepage**.

---

## ⚙️ Key Features of HTTP

* **Stateless**: Every HTTP request is independent. The server doesn’t remember anything about previous requests.
  ➤ However, **cookies** were introduced later to **store small data** like login sessions.

---

## 📬 HTTP Requests & Responses

### 🔹 Request

When the browser asks the server for something.

Main parts:

* **Method** (e.g. GET, POST)
* **URL**
* **Headers** (info like browser type, language)
* **Body** (for sending data in POST)

### 🔹 Response

The server sends back:

* **Status code** (e.g. 200 OK, 404 Not Found)
* **Headers**
* **Body** (the actual webpage or data)

---

## 📌 Important HTTP Concepts

### ✅ Request Methods:

Tell the server what the client wants to do.

* `GET` – Retrieve data
* `POST` – Send data (like forms)
* `PUT` – Update data
* `DELETE` – Remove data

### ✅ Status Codes:

Tell whether the request was successful:

* `200` – OK
* `301` – Redirect
* `404` – Not Found
* `500` – Server Error

---

## 📄 HTTP Headers

Headers are extra info sent with the request or response.

Examples:

* `Content-Type`: What kind of file is being sent (`text/html`, `application/json`)
* `Authorization`: Used for login/authentication
* `User-Agent`: Info about the browser

---

## 🧠 Advanced Features of HTTP

### 🍪 Cookies:

Used to **store data** (like login sessions). Set by the server and sent back by the browser in future requests.

### 🛠 Caching:

Helps **store copies of files** so websites load faster without making repeated server requests.

### 🔐 Authentication:

Used to check if the user is allowed to access a certain resource.

### 🔄 Redirects:

If a resource has moved, the server sends a new location (URL), and the browser follows it.

---

## 🔐 HTTP Security

### 🔸 CSP (Content Security Policy):

Limits what types of content (scripts, images) a page can load. Prevents **XSS attacks**.

### 🔸 CORS (Cross-Origin Resource Sharing):

Controls which websites can request resources from your site. Important for **web APIs**.

### 🔸 Permissions Policy:

Lets the site control **which browser features** (like camera, location) are allowed.

---

## 🌍 HTTP Versions

HTTP has improved over time:

* **HTTP/1.0** – Basic version
* **HTTP/1.1** – Persistent connections (don’t close after each request)
* **HTTP/2** – Faster with parallel requests
* **HTTP/3** – Uses a newer protocol (QUIC) for speed and security

---

## 🔍 Developer Tools

Here are some tools to help developers debug or test HTTP:

* **Browser DevTools → Network tab** (to see requests/responses)
* **curl** – Command-line tool to make HTTP requests
* **RedBot** – Tests your caching settings
* **nghttp2** – HTTP/2 testing tool
* **HTTP Observatory** – Tests website security

---

## ✨ Summary

| Feature                | What it Does                                          |
| ---------------------- | ----------------------------------------------------- |
| HTTP                   | Protocol for client-server communication              |
| Stateless              | Doesn’t remember previous requests                    |
| Request Methods        | `GET`, `POST`, `PUT`, `DELETE`, etc.                  |
| Response Codes         | `200`, `404`, `500`, etc.                             |
| Headers                | Extra data about the request/response                 |
| Cookies                | Add state to stateless protocol                       |
| CORS, CSP, Permissions | Control security and cross-origin behavior            |
| Caching                | Speeds up repeated visits                             |
| HTTP Versions          | 1.0 → 1.1 → 2 → 3 (each version improves performance) |
| Developer Tools        | curl, browser devtools, RedBot, etc.                  |

---



