## Memory Leaks via Event Listeners

### 1. What is a memory leak?

Simple definition (memorize this):

A memory leak occurs when JavaScript keeps references to objects that should have been removed from memory.

Typical symptoms:

- Application becomes slower  
- UI feels laggy  
- Memory usage keeps increasing  
- CPU usage may rise  

---

### 2. Why DOM and events commonly cause leaks

JavaScript uses **garbage collection**.

An object is removed from memory only when:

Nothing references it.

Event listeners create references between:

- DOM nodes  
- JavaScript functions  

If these references are not released, memory cannot be reclaimed.

---

### 3. Most common leak scenario

Example:

    const button = document.getElementById("btn");

    button.addEventListener("click", () => {
      console.log("Clicked");
    });

Later:

    button.remove();

Problem:

- Node removed from DOM  
- Listener still exists  
- JavaScript retains reference  

Result:

Memory leak.

---

### 4. Why this happens

Removing an element from the DOM does not automatically guarantee cleanup.

If a listener still references the node:

Garbage collection cannot occur.

The object remains in memory.

---

### 5. Fix #1 — Explicit listener cleanup

Correct pattern:

    function handleClick() {
      console.log("Clicked");
    }

    button.addEventListener("click", handleClick);

    // Cleanup
    button.removeEventListener("click", handleClick);
    button.remove();

Important rule:

Cleanup requires the **same function reference**.

Anonymous functions cannot be removed easily.

---

### 6. Fix #2 — Event delegation (Preferred solution)

Instead of attaching listeners to many elements:

    items.forEach(item => {
      item.addEventListener("click", handle);
    });

Use delegation:

    list.addEventListener("click", (event) => {
      if (event.target.tagName === "LI") {
        handle(event.target);
      }
    });

Benefits:

- Fewer listeners  
- Automatic handling of dynamic elements  
- Reduced cleanup complexity  
- Lower leak risk  

---

### 7. Global listener leaks

Example:

    window.addEventListener("resize", () => {
      console.log("resize");
    });

If added inside:

- Modals  
- Components  
- Temporary UI  

And never removed:

Memory leak occurs.

---

### 8. Fixing global listener leaks

Safer pattern:

    function onResize() {
      console.log("resize");
    }

    window.addEventListener("resize", onResize);

    // Cleanup later
    window.removeEventListener("resize", onResize);

---

### 9. Timers can also leak

Example:

    const id = setInterval(() => {
      console.log("running");
    }, 1000);

If not cleared:

    clearInterval(id);

Problem:

- Timer continues running  
- CPU usage increases  
- Memory retained  

---

### 10. Leak prevention checklist

When writing event logic, always verify:

- Did I add an event listener?  
- Will this element be removed?  
- Is this listener global?  
- Do I need cleanup logic?  
- Can delegation simplify this?  

---

### 11. One-line mental model

If you add something, you must remove it — or delegate it
