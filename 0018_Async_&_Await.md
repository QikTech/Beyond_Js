# async & await in JavaScript

### In JavaScript, async and await are used to handle asynchronous operations in a cleaner, more readable way compared to using Promises with .then() and .catch().

## 🔹 async Function

+ The async keyword is used to define a function that always returns a Promise.
+ If the function returns a value, JavaScript automatically wraps it in a Promise.
   
      async function fetchData() {
        return "Hello, World!";
      }
      
      fetchData().then(console.log);  // Output: Hello, World!

## 🔹 await Keyword

+ await is used inside an async function to pause execution until the Promise is resolved.
+ It allows writing asynchronous code that looks synchronous.
      
      async function getData() {
          let response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
          let data = await response.json();
          console.log(data);  // Logs the fetched data
      }
      
      getData();

## Promise in JavaScript?
+ A Promise in JavaScript is a special object that waits for a task to finish and then either returns a result (resolve) or an error (reject).
+ A Promise in JavaScript is an object that represents the eventual completion (resolve) or failure (reject) of an asynchronous operation.

### Promise States <br>
A Promise can be in one of three states:

1. Pending – The initial state (not yet fulfilled or rejected).
2. Fulfilled – The operation was successful (resolve() was called).
3. Rejected – The operation failed (reject() was called).

## 🔹 Error Handling with try...catch

+ async/await allows handling errors using try...catch, making it easier than chaining .catch() in Promises.
      
      async function fetchUser() {
          try {
              let response = await fetch("https://invalid-url.com");
              let data = await response.json();
              console.log(data);
          } catch (error) {
              console.error("Error fetching data:", error);
          }
      }
      
      fetchUser();

## 🔹 Parallel Execution with Promise.all

+ If multiple independent async tasks need to be executed together, use Promise.all() for better performance.
      
      async function fetchAllData() {
          let [user, posts] = await Promise.all([
              fetch("https://jsonplaceholder.typicode.com/users/1").then(res => res.json()),
              fetch("https://jsonplaceholder.typicode.com/posts/1").then(res => res.json())
          ]);
      
          console.log(user, posts);
      }
      
      fetchAllData();

## 🔹 Using await Outside of async (Top-Level Await)

+ In modern JavaScript (ES2022+), await can be used outside async functions in modules.
      
      let response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
      let data = await response.json();
      console.log(data);
      
    📌 Note: This works only inside ES modules (type="module" in <script> tag or .mjs files).
