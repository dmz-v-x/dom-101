## Window Object

### 1. First, a very simple question

❓ When JavaScript runs in the browser…  
where does it run?

👉 It runs **inside the browser environment**.

The browser gives JavaScript a **global object** to work with.

That global object is called **window**.

---

### 2. What is the Window Object?

**Simple definition (memorize this):**

The **Window object** represents the browser window/tab and provides JavaScript access to browser features.

In even simpler words:

- `window` = the browser
- It is the **top-level object**
- Everything else lives inside it

---

### 3. Window is the GLOBAL object

In the browser:

    window

is the **global object**, which means:

- All global variables  
- All global functions  
- All browser APIs  

are attached to `window`.

Example:

    var x = 10;

Behind the scenes, this becomes:

    window.x = 10;

---

### 4. Why we don’t write `window` all the time

You often write:

    alert("Hello");

But what actually runs is:

    window.alert("Hello");

Same for:

    console.log("Hi");

Which is really:

    window.console.log("Hi");

👉 JavaScript **automatically assumes `window`** if you don’t write it explicitly.

---

### 5. What lives inside the Window object?

Very important idea 👇  
`window` contains many useful things.

Some important ones:

- `document` → the DOM  
- `console`  
- `alert`, `prompt`, `confirm`  
- `setTimeout`, `setInterval`  
- `location`  
- `history`  
- `navigator`  

Mental picture:

    window
     ├── document
     ├── console
     ├── alert()
     ├── location
     ├── history
     └── navigator

👉 **DOM lives inside `window`**

---

### 6. Relationship between Window and DOM

This is a key mental model

- `window` = browser tab  
- `document` = the loaded HTML page  
- DOM = structure inside `document`  

So JavaScript accesses the DOM like this:

    window.document

But we usually write just:

    document

Because:

- `document` already exists on `window`

---

### 7. Window is NOT the DOM

Very common confusion ❌

- ❌ Window = DOM  
- ❌ Document = Browser  

Correct understanding ✅

| Thing        | What it represents          |
|-------------|-----------------------------|
| `window`    | Browser tab                 |
| `document`  | HTML page                   |
| DOM         | Tree structure of HTML      |

---

### 8. A tiny experiment (mental)

If you type this in DevTools console:

    window.document === document

Result:

    true

Because `document` lives **inside** `window`.

---

### 9. One-line summary (lock this in)

- Window is the **global browser object**  
- Document lives **inside window**  
- DOM lives **inside document**
