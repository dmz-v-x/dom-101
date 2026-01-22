## Properties vs Methods

### 1. First, what is an object? (tiny reminder)

In JavaScript, an **object** is a collection of:

- **Properties** → values (data)
- **Methods** → functions (actions)

Example:

    const person = {
      name: "Alex",
      age: 25,
      greet() {
        console.log("Hello");
      }
    };

- `name`, `age` → **properties**
- `greet()` → **method**

👉 **DOM elements work exactly the same way**.  
They are just JavaScript objects with properties and methods.

---

### 2. What is a Property?

**Simple definition:**

A **property** is a value that describes something.

Properties:

- Store data
- Do **NOT** use `()`

Example:

    document.title

This gives you:

- The current page title (a value)

Changing it:

    document.title = "My App";

👉 You are **updating a value**, not calling a function.

---

### 3. What is a Method?

**Simple definition:**

A **method** is a function that performs an action.

Methods:

- Do something
- Always use `()`

Example:

    document.getElementById("header")

This:

- Runs a function
- Searches the DOM
- Returns an element

👉 Methods **cause behavior**, properties **hold data**.

---

### 4. The easiest rule to remember 🧠

👉 If it **DOES** something → **method** → uses `()`  
👉 If it **IS** something → **property** → no `()`

| Code                          | Property / Method | Why                   |
|-------------------------------|-------------------|-----------------------|
| `document.title`              | Property          | It *is* a value       |
| `document.body`               | Property          | It *is* an element    |
| `document.getElementById()`   | Method            | It *does* a search    |
| `element.remove()`            | Method            | It *does* an action   |

---

### 5. Very common DOM example

Example:

    const heading = document.querySelector("h1");

Now observe:

    heading.textContent          // property
    heading.textContent = "Hi"   // property update

    heading.remove()             // method

Explanation:

- `textContent` → **holds text**
- `remove()` → **removes the element from the DOM**

---

### 6. Why methods need parentheses `()`

This is **very important**.

Without parentheses:

    document.getElementById

Means:

👉 “Give me the function itself”

With parentheses:

    document.getElementById("id")

Means:

👉 “Run the function now”

If you forget `()`:

- ❌ The function does not run
- ❌ Nothing happens
- ❌ Very common beginner bug

---

### 7. Properties can be READ or SET

Example:

    input.value        // read the value
    input.value = ""   // set the value

Properties:

- Represent **state**
- Can usually be **read and updated**

Methods usually:

- Do not store data
- Perform actions

---

### 8. DOM-specific examples

**Properties:**

- `element.id`
- `element.className`
- `element.innerHTML`
- `element.textContent`

**Methods:**

- `element.addEventListener()`
- `element.remove()`
- `element.append()`

Notice the pattern:
- Properties → no `()`
- Methods → always `()`

---

### 9. Common beginner mistakes

❌ Using `()` on properties:

    document.title()   // ❌ error

❌ Forgetting `()` on methods:

    element.remove     // ❌ nothing happens

Both mistakes come from confusing **state vs action**.

---

### 10. One-line summary (lock this in)

- **Properties describe state**
- **Methods perform actions**
- **Parentheses = action**
