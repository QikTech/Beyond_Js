# Hoisting
## JavaScript hoisting means JavaScript moves variable and function declarations to the top before running the code.
### Hoisting is JavaScript’s behavior of moving variable and function declarations to the top of their scope before the code executes. This means you can use variables and functions before declaring them.

+ Hoisting moves declarations to the top – JavaScript moves variable and function declarations to the top of their scope before execution.
+ Only declarations are hoisted, not values – Variables declared with var are hoisted without their assigned values, while let and const are hoisted but remain in a "temporal dead zone" until assigned.
+ Function declarations are fully hoisted – You can call a function before its declaration in the code because JavaScript hoists the entire function.
+ let and const behave differently – Unlike var, they are hoisted but not initialized, meaning using them before declaration causes a ReferenceError.
+ Hoisting happens in the compilation phase – Before executing the code, JavaScript first scans and hoists declarations during the compilation phase.
+ Function expressions are not hoisted – If you assign a function to a variable (e.g., const myFunc = function() {}), it behaves like a variable and is not accessible before its declaration.
+ Arrow functions follow variable hoisting rules – An arrow function stored in var, let, or const behaves like a variable and is not available before declaration.
+ Avoid hoisting issues with let and const – To prevent unexpected behavior, prefer let and const over var, as they do not allow access before declaration.
+ Hoisting applies to both global and function scopes – Declarations are hoisted within their respective scopes, whether inside a function or in the global scope.
+ Use strict mode ("use strict") to avoid hoisting pitfalls – In strict mode, using a variable before declaring it throws an error, helping catch hoisting-related issues.
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

