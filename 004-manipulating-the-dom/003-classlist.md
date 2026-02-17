## classList (add, remove, toggle)

### 1. Why `classList` exists

Before `classList`, developers often wrote code like this:

    element.className = "active";

This approach causes several problems:

- Overwrites existing classes  
- Removes unrelated styles  
- Hard to manage dynamically  
- Bug-prone  

👉 `classList` solves these problems cleanly.

---

### 2. What is `classList`?

**Simple definition:**

`classList` is a special object that allows you to safely manage CSS classes on an element.

It provides useful methods:

- `add()`
- `remove()`
- `toggle()`
- `contains()`

Important idea:

👉 Instead of replacing classes, you **modify them safely**.

---

### 3. `classList.add()`

Adds a class **without affecting existing classes**.

    element.classList.add("active");

If the class already exists:

- No error  
- No duplicates  
- Nothing breaks  

---

### 4. `classList.remove()`

Removes a class safely.

    element.classList.remove("active");

If the class does not exist:

- No error  
- No crash  

---

### 5. `classList.toggle()` (VERY COMMON)

Toggles a class:

- Adds it if missing  
- Removes it if present  

    element.classList.toggle("active");

Perfect for:

- Menus  
- Modals  
- Accordions  
- Dropdowns  
- Dark mode  

👉 This is the most frequently used method.

---

### 6. `classList.contains()`

Checks whether an element has a class.

    if (element.classList.contains("active")) {
      // do something
    }

Useful for conditional UI logic.

---

### 7. Real-world example

HTML:

    <button id="btn">Toggle</button>
    <div id="box" class="box"></div>

JavaScript:

    const btn = document.getElementById("btn");
    const box = document.getElementById("box");

    btn.addEventListener("click", () => {
      box.classList.toggle("active");
    });

CSS:

    .active {
      background: red;
    }

Result:

👉 Clicking the button toggles the visual state.

---

### 8. Why this is the best approach

Using `classList` gives you:

- Clean code  
- Maintainable logic  
- Proper separation of concerns  
- Predictable styling behavior  
- Compatibility with modern frameworks  

---

### 9. Common beginner mistakes

Using `.style` instead of classes:

    box.style.display = "none"; // ❌ not ideal

Overwriting classes:

    box.className = "active"; // ❌ removes other classes

👉 Prefer `classList` for UI state changes.

---

### 10. One-line mental model

`classList` = the correct way to change UI state
