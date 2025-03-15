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
