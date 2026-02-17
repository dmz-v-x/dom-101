## Manipulating HTML Through the DOM

### 1. What does “manipulating HTML” mean?

Manipulating HTML means:

- Changing text  
- Changing markup  
- Updating content dynamically  

All of this is done through **JavaScript interacting with the DOM**, not by rewriting the HTML file.

Important idea:

HTML file → static  
DOM → live and editable  

---

### 2. The three main ways to change content

There are three extremely important properties:

- `textContent`
- `innerText`
- `innerHTML`

Each behaves differently.

---

### 3. `textContent` (MOST IMPORTANT)

**Simple definition:**

`textContent` gets or sets **only text**, ignoring HTML markup.

Example:

HTML:

    <h1 id="title">Hello</h1>

JavaScript:

    const title = document.getElementById("title");
    title.textContent = "Welcome";

Result:

👉 The text changes to **Welcome**

---

#### Why `textContent` is recommended

- Very fast  
- Safe  
- No HTML parsing  
- Helps prevent XSS vulnerabilities  

Example:

    title.textContent = "<b>Hello</b>";

What the user sees:

    <b>Hello</b>

👉 The browser treats it as plain text, not HTML.

---

### 4. `innerText` (visible text only)

**Simple definition:**

`innerText` returns **only visible text**.

Key differences from `textContent`:

- Respects CSS (`display: none`)  
- Triggers layout calculations (slower)  

Example:

    element.innerText;

Use cases:

👉 Only when you specifically need **visible text**.

In most cases, prefer `textContent`.

---

### 5. `innerHTML` (powerful but dangerous)

**Simple definition:**

`innerHTML` gets or sets **HTML markup** inside an element.

Example:

    container.innerHTML = "<p>Hello <strong>World</strong></p>";

Result:

👉 New HTML is parsed and rendered.

---

#### Risks of `innerHTML`

- Parses HTML  
- Can introduce security vulnerabilities  
- Overwrites existing DOM nodes  

Critical rule:

❌ Never use with untrusted user input:

    container.innerHTML = userInput; // Security risk

Because malicious scripts could be injected.

---

### 6. Comparison table

| Property        | Handles HTML | Safe | Recommended Usage |
|-----------------|--------------|------|-------------------|
| textContent     | ❌ No        | ✅ Yes | ✅ Default choice |
| innerText       | ❌ No        | ⚠️ Slower | ⚠️ Rare cases |
| innerHTML       | ✅ Yes       | ❌ Risky | ⚠️ Use carefully |

---

### 7. Practical rule

Default to **`textContent`**.

Use **`innerHTML`** only when:

- You fully control the content  
- You intentionally want to render HTML  

---

# Final Mental Model

- `textContent` → text only → safe and fast  
- `innerText` → visible text only → slower  
- `innerHTML` → HTML markup → powerful but risky  
