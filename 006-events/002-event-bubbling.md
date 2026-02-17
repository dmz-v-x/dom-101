## Event Bubbling — How Events Travel in the DOM 

### 1. What is event bubbling?

**Simple definition (memorize this):**

Event bubbling means an event starts at the **target element** and then moves **upward through its parent elements**.

In short:

Bottom → Top

---

### 2. Why does bubbling exist?

Bubbling exists so that:

- Parent elements can react to child interactions  
- Event handling becomes flexible  
- The event system remains efficient  

Without bubbling:

- Event delegation would be impossible  
- Many separate listeners would be required  

---

### 3. Visual example (very important)

HTML:

    <div id="parent">
      <button id="child">Click</button>
    </div>

JavaScript:

    parent.addEventListener("click", () => {
      console.log("Parent clicked");
    });

    child.addEventListener("click", () => {
      console.log("Child clicked");
    });

---

### 4. What happens when you click the button?

Order of execution:

    Child clicked
    Parent clicked

Why this happens:

- The event starts at the button  
- Then bubbles up to the div  
- Then continues upward  

---

### 5. Bubbling path (mental model)

When clicking the button:

    button (target)
      ↑
    div
      ↑
    body
      ↑
    document
      ↑
    window

👉 The **same event** travels upward.

---

### 6. Important clarification

Bubbling does **NOT** mean:

- The parent triggers the child’s event

Bubbling means:

- The **same event moves upward**

This distinction is critical.

---

### 7. How `target` and `currentTarget` behave during bubbling

Example:

    parent.addEventListener("click", (e) => {
      console.log("target:", e.target);
      console.log("current:", e.currentTarget);
    });

If you click the button:

- `e.target` → button (where event started)  
- `e.currentTarget` → div (where listener exists)  

👉 `target` remains constant  
👉 `currentTarget` depends on the listener

---

### 8. Common beginner confusion

Typical reactions:

- “Why did the parent click handler run?”  
- “I only clicked the button!”  

Answer:

👉 Because of **event bubbling**

This is not a bug.  
This is intentional browser behavior.

---

### 9. Can bubbling be stopped? (preview)

Yes.

There is a method:

    event.stopPropagation();

This prevents the event from moving upward.

(Explored after capturing.)

---

### 10. One-line mental model

Events **bubble upward** from:

Target → Window
