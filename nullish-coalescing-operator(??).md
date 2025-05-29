markdown
# Understanding the Nullish Coalescing Operator (`??`) in JavaScript  

The **nullish coalescing operator (`??`)** is a logical operator in JavaScript that returns the right-hand side operand only if the left-hand side is `null` or `undefined`.  

## Syntax  
```javascript
leftOperand ?? rightOperand
How It Works
If leftOperand is null or undefined, it returns rightOperand.

If leftOperand is any other value (including falsy values like 0, "", false), it returns leftOperand.

Examples
javascript
let x = 10;
let y = 20;

x ?? y;  // 10 (x is neither null nor undefined)

let a = null;
let b = 20;

a ?? b;  // 20 (a is null)

let c = undefined;
let d = "default";

c ?? d;  // "default" (c is undefined)
Difference Between ?? and ||
The logical OR (||) operator returns the first truthy value, while ?? only checks for null or undefined.

| Value of x | x ?? "default" | x || "default" |
|-------------|------------------|------------------|
| null | "default" | "default" |
| undefined | "default" | "default" |
| 0 | 0 | "default" |
| "" | "" | "default" |
| false | false | "default" |

When to Use ??
When you want to provide a fallback only for null/undefined (not for other falsy values).

Example: Setting default values in function parameters or configurations.

javascript
function greet(name) {
  name = name ?? "Guest";
  console.log(`Hello, ${name}!`);
}

greet(null);      // "Hello, Guest!"
greet("Alice");   // "Hello, Alice!"
greet(0);         // "Hello, 0!" (unlike `||`, which would return "Guest")
Browser & Node.js Support
Supported in modern browsers (ES2020+) and Node.js 14+.

Not supported in older environments (use Babel for transpilation if needed).

Conclusion
The ?? operator is a safer alternative to || when you want to handle null/undefined without accidentally excluding valid falsy values like 0 or "".

