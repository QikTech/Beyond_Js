# 1. Function Basics

### A function is a reusable block of code that performs a specific task.
    
    function greet() {
      console.log("Hello, world!");
    }
    greet(); // Output: Hello, world!

## 2. Function Parameters & Arguments

### You can pass values (arguments) to functions using parameters.
    
    function add(a, b) {
      return a + b;
    }
    console.log(add(5, 3)); // Output: 8


## Bonus: Function Constructor (Rarely used)
  
  const add = new Function('a', 'b', 'return a + b');
  console.log(add(2, 3)); // Output: 5

## 3. Function Expressions

### Assigning a function to a variable.

    const multiply = function (a, b) {
      return a * b;
    };
    console.log(multiply(4, 2)); // Output: 8

## 4. Arrow Functions (ES6)

### Shorter syntax for function expressions.
    
    const divide = (a, b) => a / b;
    console.log(divide(10, 2)); // Output: 5
    
#### Note: Arrow functions don't have their own this or arguments.

## 5. Return Values

### Functions can return values using return.
    
    function square(n) {
      return n * n;
    }
    let result = square(4);
    console.log(result); // Output: 16

## 6. Callback Functions

### Functions passed as arguments to other functions.
    
    function greet(name) {
      console.log(`Hello, ${name}`);
    }
    function processUser(callback) {
      const userName = "Prasad";
      callback(userName);
    }
    processUser(greet); // Output: Hello, Prasad


## 7. Higher-Order Functions

### A function that takes another function as an argument or returns another function.
    
    function operate(fn, a, b) {
      return fn(a, b);
    }
    console.log(operate((x, y) => x + y, 2, 3)); // Output: 5

## 8. IIFE (Immediately Invoked Function Expression)

### Executes immediately after being defined.
    
    (function () {
      console.log("IIFE running!");
    })(); // Output: IIFE running!

## 9. Function Scope & this Keyword

### this refers to the object that is calling the function.
    
    const user = {
      name: "Prasad",
      greet: function () {
        console.log(`Hi, I’m ${this.name}`);
      },
    };
    user.greet(); // Output: Hi, I’m Prasad

#### Arrow functions don’t bind this — they inherit it from the parent scope.
## 10. Default Parameters

### Allows setting default values for function parameters.

    function sayHello(name = "Guest") {
      console.log(`Hello, ${name}`);
    }
    sayHello(); // Output: Hello, Guest

## 11. Rest & Spread in Functions
    
    // Rest parameters
    function sum(...numbers) {
    return numbers.reduce((acc, val) => acc + val, 0);
    }
    console.log(sum(1, 2, 3)); // Output: 6

## 12. Named vs Anonymous Functions
    
    Named: function add() {}
    Anonymous: const add = function () {}
