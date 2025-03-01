# Promise
## A Promise in JavaScript is a special object that waits for a task to finish and then either returns a result (resolve) or an error (reject).
+ A JavaScript Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises help manage asynchronous code in a more readable and maintainable way compared to callbacks.

+ Promises prevent callback hell.
+ .then() handles success, .catch() handles errors, .finally() runs regardless.
+ async/await makes asynchronous code look synchronous.
+ Promises can be chained for sequential execution.

Creating a Promise
### A Promise is created using the Promise constructor, which takes a function with two parameters:
+ resolve: Call this function when the operation is successful.
+ reject: Call this function when the operation fails. 


    const myPromise = new Promise((resolve, reject) => {
      let success = true; // Change to false to test rejection
      setTimeout(() => {
        if (success) {
          resolve("Operation Successful");
        } else {
          reject("Operation Failed");
        }
      }, 2000);
    });

## Consuming a Promise

### To handle a Promise's result, use .then(), .catch(), and .finally():

    myPromise
      .then((result) => {
        console.log("Success:", result);
      })
      .catch((error) => {
        console.log("Error:", error);
      })
      .finally(() => {
        console.log("Promise completed.");
      });

## Chaining Promises

#### Promises can be chained to execute multiple asynchronous operations sequentially:

    function firstTask() {
      return new Promise((resolve) => setTimeout(() => resolve("First Task Done"), 1000));
    }
    
    function secondTask(previousResult) {
      return new Promise((resolve) => setTimeout(() => resolve(previousResult + " -> Second Task Done"), 1000));
    }
    
    firstTask()
      .then(secondTask)
      .then((finalResult) => console.log(finalResult))
      .catch((error) => console.log("Error:", error));

## Using async/await with Promises

### Instead of .then(), you can use async/await for cleaner syntax:

    async function runTasks() {
      try {
        const first = await firstTask();
        const second = await secondTask(first);
        console.log(second);
      } catch (error) {
        console.log("Error:", error);
      }
    }
    
    runTasks();
    
## What are the main rules of promise?

### A promise must follow a specific set of rules:

+ A promise is an object that supplies a standard-compliant .then() method
+ A pending promise may transition into either fulfilled or rejected state
+ A fulfilled or rejected promise is settled and it must not transition into any other state.
+ Once a promise is settled, the value must not change.

## What is promise chaining

### The process of executing a sequence of asynchronous tasks one after another using promises is known as Promise chaining. Let's take an example of promise chaining for calculating the final result,

        new Promise(function (resolve, reject) {
          setTimeout(() => resolve(1), 1000);
        })
          .then(function (result) {
            console.log(result); // 1
            return result * 2;
          })
          .then(function (result) {
            console.log(result); // 2
            return result * 3;
          })
          .then(function (result) {
            console.log(result); // 6
            return result * 4;
          });
        
        In the above handlers, the result is passed to the chain of .then() handlers with the below work flow,
        
        i. The initial promise resolves in 1 second,
        ii. After that .then handler is called by logging the result(1) and then return a promise with the value of result * 2.
        iii. After that the value passed to the next .then handler by logging the result(2) and return a promise with result * 3.
        iv. Finally the value passed to the last .then handler by logging the result(6) and return a promise with result * 4.

## What is promise.all

### Promise.all is a promise that takes an array of promises as an input (an iterable), and it gets resolved when all the promises get resolved or any one of them gets rejected. For example, the syntax of promise.all method is below,

        Promise.all([Promise1, Promise2, Promise3]) .then(result) => {   console.log(result) }) .catch(error => console.log(`Error in promises ${error}`))
        
        Note: Remember that the order of the promises(output the result) is maintained as per input order.

