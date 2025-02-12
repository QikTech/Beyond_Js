# IIFE (Immediately Invoked Function Expression) in JavaScript

### An IIFE (Immediately Invoked Function Expression) is a function that runs immediately after being defined.

+ It is useful for avoiding global scope pollution and creating private variables.
+ IIFE is a function that runs immediately after being defined.
+ Used to avoid polluting the global scope.
+ Great for private variables and encapsulation.
+ Can be used in loops to fix scope issues.


## Syntax of an IIFE

### An IIFE is wrapped in parentheses ( ) to ensure JavaScript treats it as an expression and executes it immediately.
    
    (function() {
        console.log("This runs immediately!");
    })();
    
    Output:
    
    This runs immediately!
    
    Alternatively, you can use the arrow function syntax:
    
    (() => {
        console.log("IIFE using arrow function");
    })();

## Why Use an IIFE?

1. Avoid polluting the global scope
2. Encapsulate private variables
3. Execute code immediately
4. Useful in loops & event handlers

## Example 1: Prevent Global Variable Pollution

    let message = "Global Scope";
    
    (function() {
        let message = "IIFE Scope";
        console.log(message); // Output: IIFE Scope
    })();
    
    console.log(message); // Output: Global Scope
    
    Here, message inside the IIFE does not affect the global message.

## Example 2: Private Variables and Encapsulation
    
    const counter = (function() {
        let count = 0; // Private variable
    
        return {
            increment: () => ++count,
            decrement: () => --count,
            getCount: () => count
        };
    })();
    
    console.log(counter.increment()); // 1
    console.log(counter.getCount());  // 1
    console.log(counter.decrement()); // 0
    
    Since count is inside the IIFE, it cannot be accessed directly from outside.

## Example 3: IIFE with Parameters

    You can pass arguments into an IIFE.
    
    (function(name) {
        console.log(`Hello, ${name}!`);
    })("Prasad");
    
    Output:
    
    Hello, Prasad!

## Example 4: IIFE in Loops (Fix var Scope Issue)

    When using var inside loops, all iterations share the same variable. An IIFE ensures each iteration has a new scope.
    
    for (var i = 1; i <= 3; i++) {
        (function(j) {
            setTimeout(() => {
                console.log(j);
            }, j * 1000);
        })(i);
    }
    
    Output (1-second intervals):
    
    1
    2
    3
    
    Without the IIFE, all setTimeout calls would use the final value of i (3), printing 3 three times.


## Example 5: IIFE for Initialization Code

    IIFEs are often used for setting up configurations or running startup logic.
    
    const app = (function() {
        let config = { version: "1.0.0", theme: "dark" };
        console.log("App initialized");
        return config;
    })();
    console.log(app.version); // 1.0.0

Key Takeaways

✅ IIFE is a function that runs immediately after being defined.
✅ Used to avoid polluting the global scope.
✅ Great for private variables and encapsulation.
✅ Can be used in loops to fix scope issues.
