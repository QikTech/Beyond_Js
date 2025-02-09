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
### Explanation

### 1️⃣ Hoisting with var
Variables declared with var are hoisted, but only the declaration is moved to the top. The value remains undefined until assigned.
      console.log(a); // ❌ undefined (not an error, but no value assigned yet)
      var a = 10;
      console.log(a); // ✅ 10

---
### 2️⃣ Hoisting with let and const
---
### 3️⃣ Hoisting with Functions
---
### ❌ Function Expressions are NOT Hoisted
