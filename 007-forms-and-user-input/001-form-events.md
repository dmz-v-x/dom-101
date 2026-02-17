## Form Events — submit, input, change

### 1. Why forms are special

Forms are different from buttons because:

- The browser has default behavior  
- It automatically attempts to submit data  
- It reloads the page by default  

If you do nothing, the browser takes control.

---

### 2. Basic form structure (baseline)

Example:

    <form id="loginForm">
      <input type="email" id="email" />
      <input type="password" id="password" />
      <button type="submit">Login</button>
    </form>

Important detail:

👉 `type="submit"` triggers form submission.

---

### 3. The `submit` event (MOST IMPORTANT)

**Simple definition:**

The `submit` event fires when a form is submitted.

Submission can be triggered by:

- Clicking the submit button  
- Pressing Enter inside an input  

Example:

    const form = document.getElementById("loginForm");

    form.addEventListener("submit", (event) => {
      console.log("Form submitted");
    });

---

### 4. The default behavior problem

Without intervention:

- The browser submits the form  
- The page reloads  
- JavaScript state is lost  

This is undesirable in modern applications.

---

### 5. `preventDefault()` (GAME CHANGER)

**Simple definition:**

`preventDefault()` stops the browser’s default action.

Correct usage:

    form.addEventListener("submit", (event) => {
      event.preventDefault();
      console.log("Handled by JavaScript");
    });

Result:

- No page reload  
- Full control in JavaScript  

---

### 6. The `input` event (REAL-TIME)

**Simple definition:**

The `input` event fires every time the value changes.

Example:

    emailInput.addEventListener("input", () => {
      console.log(emailInput.value);
    });

Triggered by:

- Typing  
- Pasting  
- Deleting  

Common uses:

- Live validation  
- Search suggestions  
- Dynamic filtering  

---

### 7. The `change` event (AFTER COMMIT)

**Simple definition:**

The `change` event fires after the value is finalized.

Key difference:

- `input` → Fires on every change  
- `change` → Fires when editing is complete  

Typically triggered when:

- Focus leaves the input  
- Selection changes  

Best suited for:

- Select dropdowns  
- Checkboxes  
- Radio buttons  

---

### 8. Quick comparison table

| Event   | When it fires                  |
|---------|--------------------------------|
| submit  | Form submission                |
| input   | Every value change             |
| change  | After value is finalized       |

---

### Final Mental Model

- `submit` → Form action  
- `input` → Real-time updates  
- `change` → Finalized updates  
