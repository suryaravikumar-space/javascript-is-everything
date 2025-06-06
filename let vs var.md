# JavaScript Variable Redeclaration Error

## The Error
```
Uncaught SyntaxError: Identifier 'x' has already been declared
    at <anonymous>:1:1
```

## Code That Causes the Error
```javascript
var x = 23;
var x = 43;
```

## Why This Happens

The error occurs because you are trying to declare the same variable `x` twice using `var` in the same scope in strict mode, such as in modern browsers' JavaScript consoles (like Chrome DevTools).

### Explanation:
- In **non-strict mode**, JavaScript allows redeclaring `var` variables in the same scope, and the second declaration would just overwrite the first one without error.
- But in **strict mode** (which many environments use implicitly—especially the browser console), redeclaring a `var` variable in the same scope can throw a `SyntaxError`.

## How to Fix It

### Option 1: Assign a new value instead of redeclaring
```javascript
var x = 23;
x = 43; // no error
```

### Option 2: Use modern variable declarations
```javascript
let x = 23;
x = 43; // reassignment is allowed

// or

const x = 23;
// const x = 43; // This would throw an error as const cannot be reassigned
```

