## `location` Object 

### 1. What is `location`?

Simple definition (memorize this):

The `location` object represents the **current URL of the browser**.

It allows JavaScript to:

- Read the URL  
- Modify the URL  
- Redirect the user  
- Reload the page  

Accessed via:

    window.location

Or simply:

    location

Because it is globally available.

---

### 2. Important `location` properties

Assume the browser URL:

    https://example.com/products?id=10&page=2

---

#### `location.href`

    location.href

Returns:

    https://example.com/products?id=10&page=2

Meaning:

The full URL

---

#### `location.origin`

    location.origin

Returns:

    https://example.com

Meaning:

Protocol + domain

---

#### `location.pathname`

    location.pathname

Returns:

    /products

Meaning:

Path after the domain

---

#### `location.search` (Query string)

    location.search

Returns:

    ?id=10&page=2

Meaning:

Everything after `?`

Used for:

- Filters  
- Pagination  
- Search parameters  
- Dynamic state  

---

#### `location.hash`

    location.hash

Returns:

    #section1

Used for:

- Anchors  
- Basic SPA routing  
- Scroll targets  

---

### 3. Redirecting users (Very common)

#### Hard redirect (adds history entry)

    location.href = "/login";

Or:

    location.assign("/login");

Effect:

- Page reloads  
- User can press Back  

---

#### Replace current history entry

    location.replace("/dashboard");

Effect:

- Page reloads  
- No Back navigation  

Common use case:

After login or logout flows

---

### 4. Reloading the page

    location.reload();

Effect:

Forces page refresh

---

### 5. Common real-world uses

- Redirect after login  
- Logout flows  
- Reading filters from URL  
- Pagination state  
- SPA-style navigation (basic)  

---

### 6. Common beginner mistakes

- Changing the URL without expecting reload  
- Forgetting redirects refresh the page  
- Confusing `assign()` vs `replace()`  

Important rule:

URL changes usually trigger navigation.

---

### 7. One-line mental model

`location` = Read and control the browser URL
