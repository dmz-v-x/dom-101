## Selecting and Reading Elements - querySelectorAll

### 1. Why do we need `querySelectorAll`?

You already learned:

- `querySelector` → returns **only the first matching element**

But very often in real apps, we want:

- all buttons  
- all list items  
- all cards  

👉 That’s exactly why **`querySelectorAll`** exists.

---

### 2. What is `querySelectorAll`?

**Simple definition:**

`querySelectorAll` returns **ALL elements** that match a **CSS selector**.

Syntax:

    document.querySelectorAll("selector");

Think of it as:

👉 “Hey document, give me **every element** that matches this selector”

---

### 3. It also uses CSS selectors

Same power as `querySelector`.

Examples:

    document.querySelectorAll(".item");
    document.querySelectorAll("#menu li");
    document.querySelectorAll("input[type='text']");

👉 Anything valid in **CSS selectors** is valid here.

---

### 4. What does it return? (VERY IMPORTANT)

    const items = document.querySelectorAll(".item");

It returns:

- ✅ a **NodeList**
- ❌ NOT a single element
- ❌ NOT an array

But:

👉 It is **array-like** (has indexes and `length`).

---

### 5. What is a NodeList? (intro)

For now, remember this:

A **NodeList** is a **static list of nodes** returned by DOM queries.

Static means:

- It does **NOT auto-update**
- It is a **snapshot of the DOM at that moment**

This is a key difference from `HTMLCollection`.

---

### 6. How to use a NodeList

You can:

- Access elements by index
- Loop using `forEach`

Example:

    items.forEach((item) => {
      item.style.color = "green";
    });

👉 This works perfectly.

(An `HTMLCollection` cannot use `forEach` directly.)

---

### 7. Static behavior (important concept)

Example:

    const items = document.querySelectorAll(".item");
    console.log(items.length); // 3

    document.body.innerHTML += '<p class="item">New</p>';

    console.log(items.length); // still 3

👉 The NodeList does **NOT update automatically**.

That’s why it’s called **static**.

---

### 8. Common beginner mistakes

❌ Treating it like a single element:

    items.textContent = "Hi"; // ❌ error

❌ Expecting live updates:

    items.length // ❌ does not change after DOM updates

---

### 9. Important points about `querySelectorAll()`

#### What it returns

- `document.querySelectorAll()` returns a **static NodeList**
- It is **array-like** (index access + length)
- It is **not a real array**
- It does **not update** when the DOM changes

Example:

    const nodes = document.querySelectorAll(".item");

---

#### What you *can* change

You **can modify the DOM elements inside** the NodeList, because they are real element references:

    nodes.forEach(el => {
      el.style.color = "red";
      el.textContent = "Updated";
      el.classList.add("active");
      el.dataset.status = "done";
    });

All of these work because:

👉 You are modifying **elements**, not the NodeList itself.

---

#### What you *cannot* change

You **cannot**:

- Add items to the NodeList
- Remove items from it
- Change its length
- Reorder it

Examples:

    nodes.push(newElement); // ❌ error
    nodes.length = 0;       // ❌ no effect

👉 The NodeList itself is **read-only**.

---

#### If you need to modify the collection

Convert it to an array:

    const nodeArray = [...document.querySelectorAll(".item")];
    nodeArray.push(newElement); // ✅ works

Or:

    Array.from(document.querySelectorAll(".item"));

---

#### Live vs Static (very important)

- `querySelectorAll` → **static NodeList**
- `getElementsByClassName` → **live HTMLCollection**

Example:

    const live = document.getElementsByClassName("item");
    // updates automatically when DOM changes

---

### 10. When should you use `querySelectorAll`?

Use it when:

- You want **multiple elements**
- You want **CSS selector power**
- You want to use **forEach**

Avoid it when:

- You need **live updates**

---

### 11. One-line mental model

`querySelectorAll` returns a **STATIC NodeList** of matching elements.
