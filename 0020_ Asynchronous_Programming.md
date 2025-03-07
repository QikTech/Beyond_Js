# Asynchronous Programming in JavaScript

### Asynchronous programming allows JavaScript to execute tasks without blocking the main thread, enabling smooth execution of time-consuming operations like API calls, file reading, or database queries.

### 1️⃣ Synchronous vs. Asynchronous
### Synchronous 	→ Code executes line by line, waiting for each operation to complete.
### Asynchronous 	→ Tasks like API calls, file reading, or database queries happen in the background, allowing other code to run.


## 1.1 Synchronous Code (Executes line by line, blocking the next task until the current one is done)
      
      console.log("Task 1");
      console.log("Task 2");
      console.log("Task 3");
      
      📌 Output:
      
      Task 1  
      Task 2  
      Task 3  

## 1.2 Asynchronous Code (Doesn't block execution, allowing other tasks to run in parallel)
      
      console.log("Task 1");
      setTimeout(() => console.log("Task 2"), 2000); // Runs after 2 seconds
      console.log("Task 3");
      
      📌 Output:
      
      Task 1  
      Task 3  
      Task 2 (after 2 seconds)

## 2️⃣ Methods for Handling Asynchronous Code
## 2.1 Callbacks (Old Approach, Causes Callback Hell)
      
      function fetchData(callback) {
          setTimeout(() => {
              callback("Data received");
          }, 2000);
      }
      
      fetchData(data => {
          console.log(data);
      });

#### Problem: Nesting multiple callbacks leads to callback hell.

## 2.2 Promises (Better Approach)

#### A Promise is an object that represents a future value (success or failure).
      
      function fetchData() {
          return new Promise((resolve, reject) => {
              setTimeout(() => {
                  resolve("Data received");
              }, 2000);
          });
      }
      
      fetchData().then(console.log).catch(console.error);

#### 📌 No nesting, but .then() chaining can still get complex.

## 2.3 Async/Await (Modern Approach)

#### async and await make asynchronous code look synchronous & readable.
      
      async function fetchData() {
          let result = await new Promise(resolve => setTimeout(() => resolve("Data received"), 2000));
          console.log(result);
      }
      
      fetchData();

### 📌 Best practice for handling async operations.

## 3️⃣ Asynchronous API Call Example
      
      async function getUser() {
          try {
              let response = await fetch("https://jsonplaceholder.typicode.com/users/1");
              let user = await response.json();
              console.log(user);
          } catch (error) {
              console.error("Error fetching data:", error);
          }
      }
      
      getUser();

### 🔹 When to Use Asynchronous Programming?

✅ Fetching API data <br>
✅ Reading/writing files <br>
✅ Database queries <br>
✅ Timer functions (setTimeout, setInterval)
