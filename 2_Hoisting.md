# Hoisting
### Hoisting is JavaScript’s behavior of moving variable and function declarations to the top of their scope before the code executes. This means you can use variables and functions before declaring them.
___

### Summary
| Type                            | Hoisted?                |  Usable Before Declaration? |
| -------------                   | -------------           |               ------------- |
| var                             | ✅ Yes                  | 🚫 Yes, but undefined  |
| let                             | ✅ Yes                  | ❌ No (TDZ Error)  |
| const                           | ✅ Yes                  | ❌ No (TDZ Error)  |
| Function Declaration            | ✅ Yes                  | ✅ Yes  |
| Function Expression (var)       | ✅ Yes (only variable)  | ❌ No (TypeError)  |
| Function Expression (let/const) | ✅ Yes (only variable)  | ❌ No (TDZ Error)  |

---
# Explanation
### 1️⃣ Hoisting with var
### Variables declared with var are hoisted, but only the declaration is moved to the top. The value remains undefined until assigned. 
	console.log(a); // ❌ undefined (not an error, but no value assigned yet)
	var a = 10;
	console.log(a); // ✅ 10
### 👉 Internally, JavaScript treats this as:
      var a;  // Hoisted declaration
      console.log(a); // undefined
      a = 10;  // Assignment happens here
      console.log(a); // 10

---
### 2️⃣ Hoisting with let and const
### Variables declared with let and const are hoisted, but they are in a "temporal dead zone" (TDZ) until they are initialized.
      console.log(b); // ❌ ReferenceError: Cannot access 'b' before initialization
      let b = 20;
      console.log(c); // ❌ ReferenceError: Cannot access 'c' before initialization
      const c = 30;

---
### 3️⃣ Hoisting with Functions
### ✅ Function Declarations are Fully Hoisted, You can call a function before it is declared.
      greet(); // ✅ Works! "Hello, world!"

      function greet() {
        console.log("Hello, world!");
      }

---
### ❌ Function Expressions are NOT Hoisted
### If you store a function in a variable (var, let, or const), only the variable is hoisted, not the function.
      sayHello(); // ❌ TypeError: sayHello is not a function

      var sayHello = function() {
        console.log("Hello!");
      };
      👉 Only var sayHello; is hoisted, but not its function definition.

---

# 🔹 Best Practices
### ✔ Always declare variables before using them (use let or const for better scoping).
### ✔ Use function declarations when you want hoisting benefits.
### ✔ Avoid using var to prevent unexpected undefined values.

