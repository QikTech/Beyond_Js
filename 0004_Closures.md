# Closures in JavaScript

### A closure is a function that remembers the variables from its outer scope even after the outer function has finished executing. It allows functions to maintain access to their lexical scope.

## How Closures Work

### When a function is defined inside another function, it forms a closure by capturing the surrounding (lexical) variables. Even if the outer function returns, the inner function can still access these variables.
### Example 1: Basic Closure

    function outerFunction() {
        let count = 0; // This variable is enclosed in the closure
    
        return function innerFunction() {
            count++; // Inner function remembers 'count'
            console.log(count);
        };
    }

    const increment = outerFunction();
    increment(); // Output: 1
    increment(); // Output: 2
    increment(); // Output: 3
    
    Here, increment still has access to count, even though outerFunction has finished execution.

## Example 2: Closures with Parameters

    function multiplier(factor) {
        return function (number) {
            return number * factor;
        };
    }
    
    const double = multiplier(2);
    console.log(double(5)); // Output: 10
    
    const triple = multiplier(3);
    console.log(triple(5)); // Output: 15
    
    Each call to multiplier creates a separate closure, storing different values of factor.

    
## Example 3: Closures in Loops (Using let)
    
    for (let i = 1; i <= 3; i++) {
        setTimeout(() => {
            console.log(i);
        }, i * 1000);
    }
    // Output (with 1-second gaps): 1, 2, 3
    
    Here, let creates a block-scoped variable, so each iteration has a new i.

## Example 4: Closures in Loops (Using var - Fix with IIFE)

    for (var i = 1; i <= 3; i++) {
        (function (j) {
            setTimeout(() => {
                console.log(j);
            }, j * 1000);
        })(i);
    }
    // Output: 1, 2, 3 (correct)
    
    Since var is function-scoped, wrapping the logic inside an Immediately Invoked Function Expression (IIFE) ensures each iteration gets a new value.

# Practical Uses of Closures

## 1. Data Encapsulation (Private Variables)

    function counter() {
        let count = 0;
    
        return {
            increment: () => ++count,
            decrement: () => --count,
            getCount: () => count
        };
    }
    
    const myCounter = counter();
    console.log(myCounter.increment()); // 1
    console.log(myCounter.getCount());  // 1
    console.log(myCounter.decrement()); // 0
    
    The count variable is private and only accessible via the returned methods.

## 2. Event Listeners

    function addClickListener() {
        let count = 0;
        document.getElementById("myButton").addEventListener("click", function () {
            count++;
            console.log(`Button clicked ${count} times`);
        });
    }
    
    addClickListener();
    
    Here, count remains accessible in the event listener even after addClickListener has executed.

## 3. Memoization (Caching results)

    function memoize(fn) {
        let cache = {};
        return function (num) {
            if (cache[num]) {
                console.log("Fetching from cache...");
                return cache[num];
            }
            console.log("Calculating...");
            let result = fn(num);
            cache[num] = result;
            return result;
        };
    }

    function square(n) {
        return n * n;
    }

    const memoizedSquare = memoize(square);
    console.log(memoizedSquare(4)); // Calculating... 16
    console.log(memoizedSquare(4)); // Fetching from cache... 16

    The memoize function creates a closure to store results and avoid redundant calculations.

# Summary

+ Closures allow functions to "remember" their lexical scope.
+ They are useful for data encapsulation, event handlers, loops, and memoization.
+ Can be used to create private variables in JavaScript.
+ Used heavily in functional programming and frameworks like React.
