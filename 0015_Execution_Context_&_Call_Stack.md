# Execution Context & Call Stack in JavaScript

#### Quick Summary
✅ Execution Context manages variable & function execution. <br>
✅ Call Stack follows LIFO (Last In, First Out). <br>
✅ Every function call creates a new Execution Context. <br>
✅ Stack Overflow occurs with infinite recursion. <br>
✅ Async tasks are handled outside the stack.

## 1️⃣ Execution Context (EC)

### An Execution Context is the environment where JavaScript code is executed. It consists of:

+ Variable Environment (Memory allocation for variables, functions)
+ Lexical Environment (Scope chain)
+ This Binding (Value of this in that context)

### There are three types of Execution Contexts:

+ Global Execution Context (GEC) – Created when JavaScript starts execution.
+ Function Execution Context (FEC) – Created every time a function is called.
+ Eval Execution Context – Created when eval() is used.

## 2️⃣ Execution Context Creation Phases

### When a function is invoked, the Execution Context goes through two phases:

#### 🔹 Creation Phase (Memory Allocation)

+ Allocates memory for variables and functions.
+ Functions are stored entirely, while variables get undefined (Hoisting).

#### 🔹 Execution Phase

+ Executes line by line.
+ Assigns values to variables and executes functions.

## 3️⃣ Call Stack

### The Call Stack manages function execution in a Last In, First Out (LIFO) order.
    // Example
    
    function first() {
      console.log("First Function");
    }
    
    function second() {
      first();
      console.log("Second Function");
    }
    
    second();
    console.log("Global Execution");

#### Execution Process:

1️⃣ Global Execution Context is created. <br>
2️⃣ second() is called → New Function Execution Context (FEC) is created. <br>
3️⃣ Inside second(), first() is called → Another FEC is created. <br>
4️⃣ first() executes and pops off the stack. <br>
5️⃣ second() executes and pops off the stack. <br>
6️⃣ console.log("Global Execution") executes.

#### Call Stack Flow

    1. Global Execution Context → Push
    2. second() → Push
    3. first() → Push
    4. first() → Pop
    5. second() → Pop
    6. Global Execution → Pop (Execution Ends)

    // Output:
    
    First Function
    Second Function
    Global Execution

## 4️⃣ Call Stack Overflow

### If a function calls itself indefinitely, it causes a stack overflow error.

    function recurse() {
      recurse(); // Infinite Recursion
    }
    recurse(); // ❌ Uncaught RangeError: Maximum call stack size exceeded

## 5️⃣ Relation to Asynchronous Code

+ JavaScript is single-threaded, meaning only one function executes at a time.
+ Async tasks (e.g., setTimeout(), Promises, API calls) are handled outside the stack using Event Loop and Callback Queue.
