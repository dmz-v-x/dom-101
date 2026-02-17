## The Event Object

### 1. What is an event? (quick reminder)

An **event** is something that happens in the browser.

Examples:

- Click  
- Key press  
- Mouse movement  
- Form submission  

When an event occurs, the browser:

👉 Creates an object describing what happened

That object is called the **event object**.

---

### 2. Where does the event object come from?

Example:

    button.addEventListener("click", function (event) {
      console.log(event);
    });

Important details:

- You did **NOT** create `event`
- The browser creates it
- The browser passes it into your function

👉 This object contains all information about the event.

---

### 3. What does the event object contain?

The event object answers questions like:

- What type of event occurred?  
- Which element triggered it?  
- Where did it happen?  
- Was a key pressed?  
- Can default behavior be prevented?  

You do not need everything — only the commonly used properties.

---

### 4. `event.target` (VERY IMPORTANT)

**Simple definition:**

`event.target` is the **actual element that triggered the event**.

Example:

HTML:

    <button>
      <span>Click me</span>
    </button>

JavaScript:

    button.addEventListener("click", (event) => {
      console.log(event.target);
    });

Behavior:

- Click the `<span>` → target = `<span>`
- Click the `<button>` → target = `<button>`

👉 `target` = where the event **started**

---

### 5. Why `event.target` matters

Users do not always click exactly what you expect.

Critical for:

- Lists  
- Nested elements  
- Buttons inside cards  
- Event delegation  

---

### 6. `event.currentTarget` (VERY IMPORTANT)

**Simple definition:**

`event.currentTarget` is the element **where the event listener is attached**.

Example:

    button.addEventListener("click", (event) => {
      console.log(event.currentTarget);
    });

No matter where you click inside the button:

👉 `currentTarget` is always the button.

---

### 7. `target` vs `currentTarget` (KEY DIFFERENCE)

| Property               | Meaning                     |
|------------------------|-----------------------------|
| `event.target`         | Where the event **started** |
| `event.currentTarget`  | Where the listener **lives** |

---

### 8. Visual example

HTML:

    <ul id="list">
      <li>One</li>
      <li>Two</li>
    </ul>

JavaScript:

    list.addEventListener("click", (e) => {
      console.log("target:", e.target);
      console.log("current:", e.currentTarget);
    });

If you click on `<li>`:

- `target` → `<li>`
- `currentTarget` → `<ul>`

👉 The event starts at the clicked element  
👉 The listener runs on the parent

---

### 9. Common beginner mistakes

- Assuming `target === listener element`
- Writing logic on the wrong node

This leads to:

- Incorrect deletions  
- Broken UI updates  
- Bugs in lists  

---

### 10. One-line mental model

- `target` = what the user interacted with  
- `currentTarget` = where your listener is attached
