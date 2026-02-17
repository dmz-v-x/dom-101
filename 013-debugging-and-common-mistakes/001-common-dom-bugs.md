## Common DOM Bugs

### 1. Why DOM bugs are so common

DOM bugs occur frequently because:

- The DOM is dynamic  
- Timing affects execution  
- Elements appear and disappear  
- Events propagate  
- UI state constantly changes  

Most issues stem from:

Logic errors and lifecycle mistakes.

---

### 2. Bug #1 — "Cannot read properties of null"

Example:

    document.getElementById("btn").addEventListener("click", () => {});

Error:

    Cannot read properties of null

Why it happens:

- Element does not exist  
- DOM not loaded yet  
- Incorrect selector  
- Script running on wrong page  

Safer pattern:

    const btn = document.getElementById("btn");

    if (!btn) return;

    btn.addEventListener("click", () => {});

---

### 3. Bug #2 — Event listener not firing

Example:

    button.addEventListener("click", handleClick);

But nothing happens.

Common causes:

- Element covered by another element  
- Listener attached to wrong node  
- Wrong event type  
- Element disabled  
- Element replaced dynamically  

Debug tip:

    console.log(button);

Verify:

- Correct element selected  
- Element exists  
- Element visible and interactive  

---

### 4. Bug #3 — Listener works once, then stops

Typical scenario:

- Click works initially  
- Stops after DOM update  

Common cause:

Element replacement.

Example:

    container.innerHTML = "<button>Click</button>";

Effect:

- Old button destroyed  
- Event listeners removed  

Solutions:

- Reattach listeners  
- Avoid destructive DOM updates  
- Use event delegation  

---

### 5. Bug #4 — Multiple clicks firing unexpectedly

Symptom:

One click triggers multiple executions.

Common cause:

Listener attached repeatedly.

Example (Problematic):

    button.addEventListener("click", () => {
      button.addEventListener("click", doSomething);
    });

Each click adds another listener.

Correct approach:

Attach listeners once.

Or remove before reattaching.

---

### 6. Bug #5 — Wrong element responding

Example:

    list.addEventListener("click", (event) => {
      console.log(event.target);
    });

Unexpected elements appear.

Cause:

Event bubbling.

The user clicked a nested child.

Safer pattern:

    if (event.target.tagName !== "LI") return;

---

### 7. Bug #6 — CSS changes not applying

Example:

    element.style.color = "red";

But nothing visually changes.

Common causes:

- CSS specificity override  
- Incorrect element targeted  
- Element hidden  
- Style immediately overwritten  

Debug strategy:

- Inspect element in DevTools  
- Check computed styles  
- Verify CSS cascade  

---

### 8. Universal DOM bug checklist

When debugging DOM issues, verify:

- Does the element exist?  
- Is the DOM fully loaded?  
- Is the selector correct?  
- Was the element replaced?  
- Was the element removed?  
- Is event propagation involved?  
- Was the listener attached multiple times?  
- Is CSS overriding styles?  

Systematic checks prevent guesswork.

---

### 9. One-line mental model

Most DOM bugs occur because:

The element does not exist at the time of interaction  
or  
The event logic is attached incorrectly
