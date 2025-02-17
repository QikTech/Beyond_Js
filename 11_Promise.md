# Promise
## A JavaScript Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises help manage asynchronous code in a more readable and maintainable way compared to callbacks.

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
