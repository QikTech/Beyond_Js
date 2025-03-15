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


