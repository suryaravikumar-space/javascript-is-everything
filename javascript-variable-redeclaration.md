## 📘 Understanding Variable Declarations and Redeclarations in JavaScript (`let` vs `var`)

### 🚫 The Problem with `let` Redeclaration

```javascript
let x = 10;
let x = 20;  // ❌ SyntaxError
console.log(x);
```

**Why this fails:**

- In JavaScript, `let` (and `const`) **cannot be redeclared** in the same block scope.
- Attempting to do so throws a `SyntaxError`:

```bash
Uncaught SyntaxError: Identifier 'x' has already been declared
```

**Correct way using `let`:**

```javascript
let x = 10;
x = 20;  // ✅ Reassignment is allowed
console.log(x);  // Output: 20
```

---

### ✅ Using `var` — With Caution

```javascript
var x = 10;
var x = 20;  // ✅ No SyntaxError in normal JS scripts
console.log(x);  // Output: 20
```

- `var` **does allow redeclaration** within the same scope.
- However, it's **function-scoped**, not block-scoped, which can lead to confusing bugs.
- Prefer using `let` and `const` for modern JavaScript development.

---

### ⚠️ Behavior in DevTools Console

When running code **line-by-line in the browser's DevTools console**, you may still get:

```bash
Uncaught SyntaxError: Identifier 'x' has already been declared
```

Even with `var`. This happens because:

- DevTools console retains variable declarations across inputs.
- It's like executing code in a persistent, strict-mode-like global context.

---

### 🔁 Workarounds

- **Reassign instead of redeclaring**:

```javascript
var x = 10;
// Later
x = 20;
```

- **Wrap in a function scope**:

```javascript
(function() {
  var x = 10;
  var x = 20;
  console.log(x);  // Output: 20
})();
```

- **Clear the DevTools context**:
  - Press `Ctrl+L` or
  - Right-click → `Clear console context`

---

### 📝 Summary Table

| Keyword   | Redeclaration | Scope         | Common in DevTools | Recommendation         |
|-----------|----------------|---------------|--------------------|------------------------|
| `var`     | ✅ Yes          | Function       | ⚠️ May throw error | Use sparingly          |
| `let`     | ❌ No           | Block          | ❌ Always errors    | ✅ Use in modern JS     |
| `const`   | ❌ No           | Block          | ❌ Always errors    | ✅ Use for constants    |
