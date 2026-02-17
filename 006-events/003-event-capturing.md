## Event Capturing — The Other Direction of Events 

### 1. What is event capturing?

**Simple definition:**

Event capturing means the event travels from the **top of the DOM tree down to the target element**.

Direction:

Top → Bottom

---

### 2. Full event flow (IMPORTANT)

Every browser event actually moves through **three phases**:

#### Capturing Phase

    window → document → body → target

The event travels downward.

---

#### Target Phase

The event reaches the actual target element.

---

#### Bubbling Phase

    target → body → document → window

The event travels upward.

---

Important:

👉 By default, most event listeners run during the **bubbling phase**.

---

### 3. Why don’t we see capturing normally?

Because:

- Event listeners default to bubbling  
- Capturing must be explicitly enabled  

---

### 4. How to listen during capturing

Syntax options:

    element.addEventListener("click", handler, true);

or

    element.addEventListener("click", handler, { capture: true });

That `true` means:

👉 “Run this listener during the capturing phase”

---

### 5. Capturing example

HTML:

    <div id="parent">
      <button id="child">Click</button>
    </div>

JavaScript:

    parent.addEventListener("click", () => {
      console.log("Parent capture");
    }, true);

    child.addEventListener("click", () => {
      console.log("Child bubble");
    });

Clicking the button produces:

    Parent capture
    Child bubble

Why this happens:

- Event moves downward first  
- Capturing listener runs  
- Event reaches target  
- Bubbling listener runs  

---

### 6. Why does capturing exist?

Capturing has valid but less common use cases:

- Intercepting events early  
- Logging / analytics systems  
- Security mechanisms  
- Framework internals  

Important reality:

👉 Most applications do not require capturing.

---

### 7. Bubbling vs Capturing

| Phase       | Direction        | Default Behavior |
|------------|------------------|------------------|
| Capturing  | Top → Bottom     | No               |
| Bubbling   | Bottom → Top     | Yes              |

---

### 8. Should beginners use capturing?

General guidance:

- Know that it exists  
- Know how to recognize it  
- Know how to debug it  

But for most code:

👉 Prefer bubbling.

---

### 9. Common beginner mistake

Accidentally enabling capturing:

    addEventListener("click", handler, true);

Then being confused by execution order.

Always verify the third parameter.

---

### 10. One-line mental model

Capturing = moving down the tree  
Bubbling = moving up the tree
