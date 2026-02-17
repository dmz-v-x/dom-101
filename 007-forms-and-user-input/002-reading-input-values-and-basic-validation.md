## Reading Input Values and Basic Validation

### 1. How do we read input values?

Every form control (`input`, `textarea`, `select`) has a **`value` property**.

HTML:

    <input type="text" id="username" />

JavaScript:

    const input = document.getElementById("username");
    console.log(input.value);

👉 `value` always contains what the user has entered.

---

### 2. Reading values on form submit (MOST COMMON)

HTML:

    <form id="loginForm">
      <input type="email" id="email" />
      <input type="password" id="password" />
      <button type="submit">Login</button>
    </form>

JavaScript:

    const form = document.getElementById("loginForm");

    form.addEventListener("submit", (event) => {
      event.preventDefault();

      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      console.log(email, password);
    });

👉 This is how login, signup, and search forms work.

---

### 3. Common beginner mistake

Incorrect approach:

    const email = document.getElementById("email").value;

Why this is problematic:

- Runs before user interaction  
- Captures an empty value  

Correct approach:

👉 Always read values **inside the event handler**.

---

### 4. What is validation?

**Validation** means:

Checking whether user input is acceptable before processing it.

Common validation checks:

- Empty fields  
- Length constraints  
- Format constraints  

---

### 5. Required field validation (simplest form)

    if (email === "" || password === "") {
      alert("All fields are required");
      return;
    }

👉 `return` stops further execution.

---

### 6. Length validation

    if (password.length < 6) {
      alert("Password must be at least 6 characters");
      return;
    }

👉 Useful for passwords, usernames, etc.

---

### 7. Basic email format validation

Simple example:

    if (!email.includes("@")) {
      alert("Invalid email");
      return;
    }

Important:

👉 This is not perfect validation, but sufficient for learning fundamentals.

Advanced validation is typically handled using libraries.

---

### 8. Showing errors in the UI (better UX)

Instead of alerts, display errors in the interface.

HTML:

    <p id="error"></p>

JavaScript:

    const error = document.getElementById("error");

    if (email === "") {
      error.textContent = "Email is required";
      return;
    }

👉 This produces a cleaner user experience.

---

### 9. Clearing errors on input (improved UX)

    emailInput.addEventListener("input", () => {
      error.textContent = "";
    });

👉 Prevents stale error messages.

---

### 10. One-line mental model

Read values on submit.  
Validate before processing.  
Stop execution when invalid.
