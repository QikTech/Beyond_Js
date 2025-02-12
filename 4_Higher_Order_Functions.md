# Higher-Order Functions in JavaScript 🚀

### What is a Higher-Order Function?
A Higher-Order Function (HOF) is a function that takes another function as an argument or returns a function.
+ Improves code reusability and modularity
+ Simplifies complex logic
+ Helps with functional programming concepts
+ Code Reusability – Makes code more modular and reusable.
+ Readability – Expressive and easier to understand.
+ Functional Programming – Enables declarative programming patterns.
+ ✅ Cleaner and Reusable Code
+ ✅ Encapsulates Logic (reduces redundancy)
+ ✅ Better Readability & Maintainability

#### Examples:
    map()	          Transforms array elements
    filter()	      Filters elements based on a condition
    reduce()	      Reduces an array to a single value
    forEach()	      Iterates over an array
    sort()	        Sorts an array

# 🔹 Examples of Higher-Order Functions
## 1️⃣ Function that Takes Another Function as an Argument

    function greet(name, callback) {
      console.log("Hello, " + name);
    callback();
    }

    function sayGoodbye() {
    console.log("Goodbye!");
    }

    greet("Prasad", sayGoodbye);
    
    ✅ Explanation: greet() takes another function (sayGoodbye()) as an argument and calls it.

## 2️⃣ Function that Returns Another Function

    function multiplyBy(factor) {
      return function (num) {
        return num * factor;
      };
    }
    
    const double = multiplyBy(2);
    console.log(double(5)); // Output: 10
    
    ✅ Explanation: multiplyBy(2) returns a function that multiplies a number by 2.

## 🔹 Common Higher-Order Functions in JavaScript
### 1️⃣ map() – Transforms Each Array Element

    const numbers = [1, 2, 3, 4];
    const doubled = numbers.map(num => num * 2);
    console.log(doubled); // Output: [2, 4, 6, 8]

## ✅ Explanation: map() applies the function (num * 2) to each element and returns a new array.
### 2️⃣ filter() – Filters Elements Based on a Condition

    const numbers = [10, 15, 20, 25];
    const greaterThan15 = numbers.filter(num => num > 15);
    console.log(greaterThan15); // Output: [20, 25]

## ✅ Explanation: filter() keeps only elements greater than 15.
### 3️⃣ reduce() – Reduces Array to a Single Value

    const numbers = [1, 2, 3, 4];
    const sum = numbers.reduce((acc, num) => acc + num, 0);
    console.log(sum); // Output: 10

## ✅ Explanation: reduce() accumulates values by summing them up.
### 4️⃣ forEach() – Iterates Over an Array (No Return)

    const fruits = ["apple", "banana", "cherry"];
    fruits.forEach(fruit => console.log(fruit.toUpperCase()));
    // Output:
    // APPLE
    // BANANA
    // CHERRY

## ✅ Explanation: forEach() executes a function for each array element but does not return a new array.
### 5️⃣ sort() – Sorts an Array

    const numbers = [4, 2, 10, 5];
    numbers.sort((a, b) => a - b);
    console.log(numbers); // Output: [2, 4, 5, 10]

## ✅ Explanation: Sorts numbers in ascending order.
### 🔹 Custom Higher-Order Function Example
    Function that Executes Another Function Multiple Times
    
    function repeat(times, callback) {
      for (let i = 0; i < times; i++) {
        callback(i);
      }
    }
    
    repeat(3, i => console.log(`Execution ${i + 1}`));
    
    ✅ Output:

    
    Execution 1
    Execution 2
    Execution 3
    
    ✅ Explanation: repeat(3, callback) calls callback(i) 3 times.
