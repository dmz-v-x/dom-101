## Selecting and Reading Elements - getElementsByClassName

### 1. What is a class in HTML? (tiny reminder)

In HTML:

    <p class="item">Apple</p>
    <p class="item">Banana</p>
    <p class="item">Mango</p>

Rules of `class`:

- Can be used on **multiple elements**
- Used for **grouping elements**
- Commonly used for **styling** and **JavaScript selection**

👉 Unlike `id`, a class is **not unique**.

---

### 2. What is `getElementsByClassName`?

**Simple definition:**

`getElementsByClassName` finds **ALL elements** that have a given class name.

Syntax:

    document.getElementsByClassName("item");

Read it like English:

👉 “Hey document, give me all elements with class `item`”

---

### 3. What does it return? (VERY IMPORTANT)

    const items = document.getElementsByClassName("item");

It returns:

- ✅ an **HTMLCollection**
- ❌ NOT a single element
- ❌ NOT an array

👉 This is our **first multi-element selector**.

---

### 4. What is an HTMLCollection? (intro only)

For now, remember this:

An **HTMLCollection** is a **live collection of elements**.

That means:

- It updates **automatically** when the DOM changes
- If elements are added or removed → the collection updates itself

We’ll compare this deeply with **NodeList** later.

---

### 5. How do you access elements inside it?

You must use **indexing**:

    items[0]; // first element
    items[1]; // second element

Example:

    items[0].textContent = "Orange";

Each index gives you a **real DOM element**.

---

### 6. Looping over an HTMLCollection

An HTMLCollection:

- Has a `length` property
- Does **NOT** have array methods like `map`, `filter`, etc.

Correct way to loop:

    for (let i = 0; i < items.length; i++) {
      items[i].style.color = "red";
    }

👉 Traditional `for` loop is the safest approach.

---

### 7. Live behavior (very important concept)

Example:

    const items = document.getElementsByClassName("item");
    console.log(items.length); // 3

    // later
    document.body.innerHTML += '<p class="item">Grapes</p>';

    console.log(items.length); // 4

👉 The collection updates **automatically**.

This behavior is called **live behavior**.

---

### 8. Common beginner mistakes ⚠️

❌ Treating it like a single element:

    items.textContent = "Hi"; // ❌ error

❌ Using array methods:

    items.map(...) // ❌ not allowed

👉 Remember: it is **collection**, not an element, not an array.

---

### 9. When should you use it?

Good use cases:

- Lists
- Groups of buttons
- Repeated UI elements

Avoid it when:

- You need array methods
- You want a **static snapshot** of elements

---

### 10. One-line mental model (lock this in)

`getElementsByClassName` returns a **LIVE HTMLCollection** of matching elements.
