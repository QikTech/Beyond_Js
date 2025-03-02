# What is a Callback?

### A callback is a function that is passed as an argument to another function and executed later. 
It is commonly used for handling asynchronous operations like API calls, file reading, or timers.

📌 Example of a Callback

    function fetchData(callback) {
      setTimeout(() => {
        console.log("Data fetched");
        callback();
      }, 2000);
    }
    
    function processData() {
      console.log("Processing data...");
    }
    
    fetchData(processData);

✔ Benefits: Helps in handling asynchronous operations.
❌ Problem: If callbacks are deeply nested, it leads to callback hell.

# What is Callback Hell?

### Callback Hell (also called "Pyramid of Doom") occurs when multiple asynchronous functions depend on each other, leading to deeply nested callbacks, making the code difficult to read and maintain.

📌 Example of Callback Hell

    setTimeout(() => {
      console.log("Step 1");
      setTimeout(() => {
        console.log("Step 2");
        setTimeout(() => {
          console.log("Step 3");
          setTimeout(() => {
            console.log("Step 4");
          }, 1000);
        }, 1000);
      }, 1000);
    }, 1000);
  
❌ Problems with Callback Hell:

+ Difficult to read and debug.
+ Hard to maintain.
+ Becomes complex when handling errors.

# How to Avoid Callback Hell?

### ✅ Solution 1: Use Promises

    function step1() {
      return new Promise((resolve) => {
        setTimeout(() => {
          console.log("Step 1");
          resolve();
        }, 1000);
      });
    }
    
    step1()
      .then(() => step1()) // Chaining Promises
      .then(() => step1());

### ✅ Solution 2: Use Async/Await (Best Approach)

    async function executeSteps() {
      await step1();
      await step1();
      await step1();
    }
    
    executeSteps();
    
    🚀 Async/Await makes the code look synchronous and avoids nesting issues!
