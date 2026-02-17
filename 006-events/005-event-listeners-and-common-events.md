## Event Listeners & Common Events

### 1. What is an event listener?

**Simple definition (memorize this):**

An **event listener** is a function that waits for an event and runs code when that event occurs.

In plain terms:

When X happens → Do Y

---

### 2. Basic syntax (no shortcuts)

    element.addEventListener("eventName", handlerFunction);

Example:

    button.addEventListener("click", () => {
      console.log("Button clicked");
    });

---

### 3. Why `addEventListener` exists

Older approach (not recommended):

    <button onclick="doSomething()">Click</button>

Problems:

- Mixes HTML and JavaScript  
- Hard to maintain  
- Cannot attach multiple listeners  
- Limited flexibility  

---

### 4. Advantages of `addEventListener`

- Clean separation of concerns  
- Multiple listeners allowed  
- Works with bubbling and capturing  
- Required for event delegation  
- More maintainable and scalable  

---

### 5. Very important rule

Incorrect usage:

    button.addEventListener("click", handleClick());

Why this is wrong:

- The function runs immediately  
- The listener receives the return value  

Correct usage:

    button.addEventListener("click", handleClick);

👉 Pass the function reference, not the result.

---

### 6. Removing an event listener (awareness)

    element.removeEventListener("click", handlerFunction);

Important constraint:

👉 Removal works only if the **same function reference** is used.

---

### 7. One-line mental model

Event listener = Wait → React

---

### 8. Mouse events (most frequently used)

- `click`  
- `dblclick`  
- `mouseover`  
- `mouseout`  
- `mouseenter`  
- `mouseleave`  

Important distinction:

- `mouseover` → Bubbles  
- `mouseenter` → Does NOT bubble  

👉 Use `mouseenter` when bubbling causes unwanted behavior.

---

### 9. Keyboard events

- `keydown`  
- `keyup`  
- `keypress` (deprecated)

Example:

    input.addEventListener("keydown", (e) => {
      console.log(e.key);
    });

Common uses:

- Keyboard shortcuts  
- Input validation  
- Search interactions  

---

### 10. Form events (preview)

- `submit`  
- `input`  
- `change`  
- `focus`  
- `blur`  

These events are central to user interaction and form handling.

---

### 11. Window and document events

- `load`  
- `DOMContentLoaded`  
- `scroll`  
- `resize`  

Example:

    window.addEventListener("scroll", () => {
      console.log("Scrolling");
    });

---

### 12. Which events should you remember?

Avoid memorizing everything.

Focus on core events:

- `click`  
- `input`  
- `submit`  
- `keydown`  
- `mouseenter` / `mouseleave`  

Everything else can be referenced when needed.

---

### 13. Common beginner mistakes

- Using deprecated events (`keypress`)  
- Choosing incorrect mouse events  
- Listening on the wrong element  
- Confusing event behavior  

---

### 14. Final mental model

Events describe **what happened**.  
Listeners decide **what to do**.
