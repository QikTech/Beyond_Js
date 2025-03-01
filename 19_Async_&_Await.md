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
