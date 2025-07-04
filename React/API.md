
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

