# The Temporal Dead Zone (TDZ) is the period between when a variable is hoisted and when it is initialized. During this time, accessing the variable results in a ReferenceError.

# This applies to let and const, but not var.
### 1️⃣ Example of TDZ with let

    console.log(a); // ❌ ReferenceError: Cannot access 'a' before initialization
    let a = 10;
    console.log(a); // ✅ 10

### 👉 Why?

    a is hoisted but remains uninitialized in the TDZ.
    The TDZ ends when a = 10; is executed.
---
### 2️⃣ Example of TDZ with const

    console.log(b); // ❌ ReferenceError: Cannot access 'b' before initialization
    const b = 20;
    console.log(b); // ✅ 20

### 👉 Same as let, but const must be assigned during declaration.
---
### 3️⃣ var Does NOT Have a TDZ

    console.log(c); // ✅ undefined (no TDZ for `var`)
    var c = 30;
    console.log(c); // ✅ 30

### 👉 var is hoisted and initialized with undefined, so no TDZ.
---
### 4️⃣ TDZ with typeof (Surprising Behavior!)

    console.log(typeof x); // ❌ ReferenceError: Cannot access 'x' before initialization
    let x = 40;

### 👉 With var, typeof doesn't throw an error:

    console.log(typeof y); // ✅ "undefined"
    var y = 50;

### 👉 Key Difference:

    var → undefined (no TDZ)
    let / const → ReferenceError in TDZ

### 5️⃣ TDZ in Block Scope

    {
      console.log(num); // ❌ ReferenceError (TDZ inside block)
      let num = 60;
    }

### 👉 Each block has its own TDZ for let and const.

# 🚀 Best Practices

### ✔ Always declare variables at the top of their scope to avoid TDZ issues.
### ✔ Use let and const instead of var for better scoping and error prevention.
### ✔ Avoid accessing variables before declaring them!
