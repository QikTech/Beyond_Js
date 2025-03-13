## Imperative Programming
### Type of programming paradigm that describes how the program executes. Developers are more concerned with how to get an answer step by step. It comprises the sequence of command imperatives

## 🛠 Imperative Programming

+ Focus: How to do something.
+ You write step-by-step instructions for the computer to follow.
+ You manage the control flow, like loops, conditions, and assignments.

    🔸 Example (in JavaScript):
    
    let numbers = [1, 2, 3, 4, 5];
    let squared = [];
    for (let i = 0; i < numbers.length; i++) {
      squared.push(numbers[i] * numbers[i]);
    }
    console.log(squared); // [1, 4, 9, 16, 25]

#### ✅ Pros:

+ More control over logic and flow.
+ Useful for performance optimization and low-level programming.

#### ❌ Cons:

+ More code and complexity.
+ Higher chance of bugs due to mutable state and manual flow control.

## Declarative Programming
### type of programming paradigm that describes what programs to be executed. Developers are more concerned with the answer that is received. It declares what kind of results we want and leave programming language aside focusing on simply figuring out how to produce them.

## ✨ Declarative Programming

+ Focus: What you want to achieve, not how to do it.
+ You describe the desired outcome, and let the language/library figure out the steps.

        🔸 Example (in JavaScript):
        
        let numbers = [1, 2, 3, 4, 5];
        let squared = numbers.map(n => n * n);
        console.log(squared); // [1, 4, 9, 16, 25]

## ✅ Pros:

+ Cleaner, shorter, and more readable code.
+ Easier to maintain and reason about.

## ❌ Cons:

+ Less control over internal operations.
+ May have performance limitations in some cases.

Imperative Programming | Declarative Programming  
---- | ----
In this, programs specify how it is to be done.  | In this, programs specify what is to be done.  
It simply describes the control flow of computation.  | It simply expresses the logic of computation.  
Its main goal is to describe how to get it or accomplish it.  | Its main goal is to describe the desired result without direct dictation on how to get it.  
Its advantages include ease to learn and read, the notional model is simple to understand, etc.  | Its advantages include effective code, which can be applied by using ways, easy extension, high level of abstraction, etc.  
Its type includes procedural programming, object-oriented programming, parallel processing approach.  | Its type includes logic programming and functional programming.  
In this, the user is allowed to make decisions and commands to the compiler. | In this, a compiler is allowed to make decisions.  
It has many side effects and includes mutable variables as compared to declarative programming. | It has no side effects and does not include any mutable variables as compared to imperative programming.  
It gives full control to developers that are very important in low-level programming. | It may automate repetitive flow along with simplifying code structure. 
In imperative programming, the programmer is responsible for optimizing the code for performance. | In declarative programming, the system optimizes the code based on the rules and constraints specified by the programmer.
In imperative programming, variables can be mutable. | In declarative programming, variables are typically immutable.

