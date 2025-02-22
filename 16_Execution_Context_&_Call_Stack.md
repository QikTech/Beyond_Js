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
