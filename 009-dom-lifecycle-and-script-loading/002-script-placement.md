## Script Placement — head vs body

### 1. Why script placement matters

Key rule:

JavaScript executes **immediately when the browser encounters the `<script>` tag**.

Critical question:

Has the DOM been built when the script runs?

If not:

- Elements do not exist  
- DOM queries return `null`  
- Errors occur  

---

### 2. Script inside `<head>` (Common source of bugs)

HTML:

    <head>
      <script src="app.js"></script>
    </head>
    <body>
      <button id="btn">Click</button>
    </body>

What actually happens:

1. Browser begins parsing HTML  
2. Encounters `<script>`  
3. Pauses HTML parsing  
4. Executes JavaScript  
5. DOM is incomplete  

Result:

    document.getElementById("btn"); // null

Why?

👉 The button has not been parsed yet.

---

### 3. Fix for head scripts — DOMContentLoaded

Safe pattern:

    document.addEventListener("DOMContentLoaded", () => {
      const btn = document.getElementById("btn");

      btn.addEventListener("click", () => {
        console.log("Clicked");
      });
    });

This guarantees:

- DOM is fully built  
- Elements exist  
- No timing errors  

---

### 4. Script at the END of `<body>` (Classic best practice)

HTML:

    <body>
      <button id="btn">Click</button>

      <script src="app.js"></script>
    </body>

What happens:

1. HTML is parsed first  
2. DOM tree is built  
3. Script executes last  

Result:

- Elements exist  
- No DOMContentLoaded required  

This has historically been the safest placement strategy.

---

### 5. Modern solution — `defer` attribute

HTML:

    <head>
      <script src="app.js" defer></script>
    </head>

What `defer` does:

- Script downloads in parallel  
- Execution is delayed  
- Runs after DOM is ready  

Effectively equivalent to:

👉 Script at bottom of `<body>`

Advantages:

- Cleaner HTML structure  
- Predictable execution timing  
- Modern best practice  

---

### 6. Quick comparison table

| Placement            | Safe? | Notes |
|----------------------|--------|--------|
| `<head>` (no defer)  | No     | Causes null errors |
| `<head defer>`       | Yes    | Modern best choice |
| End of `<body>`      | Yes    | Classic safe option |

---

### 7. Common beginner mistakes

- Placing scripts in `<head>` without `defer`  
- Accessing DOM before it exists  
- Inconsistent script placement  

Most DOM timing bugs originate here.

---

### 8. One-line mental model

JavaScript must execute **after the DOM is built**.
