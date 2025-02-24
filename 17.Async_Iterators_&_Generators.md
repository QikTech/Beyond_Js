# Async Iterators & Generators in JavaScript

### Async Iterators and Generators are powerful tools in JavaScript for handling asynchronous data streams efficiently. 
They allow processing large datasets, handling infinite sequences, and working with streaming APIs in a memory-efficient manner

### Quick Summary

✅ Async Generators make handling asynchronous streaming data simple and efficient. <br>
✅ They help with API pagination, WebSockets, file processing, and real-time applications. <br>
✅ for-await-of loops simplify consumption, keeping code clean and readable. <br>

## Comparison Table: Iterators vs. Generators vs. Async Generators

Feature       | Iterators         |	Generators        | Async Generators
---           | ---               | ---               | --- 
Returns       |	Values            | Iterator Object   |	Async Iterator Object
Execution     |	Synchronous       |	Lazy Execution    |	Async Lazy Execution
Can Use await |	❌ No             |	❌ No             |	✅ Yes
Use Case      |	Static Collections |	Lazy Computation |	Streaming Data, API Requests

## 1. Understanding Iterators vs. Generators

## 1.1 Synchronous Iterators

#### An iterator is an object that adheres to the Iterator Protocol, meaning it has a next() method that returns { value, done }.
    Example: Manual Iterator
    
    const iterable = {
      data: [1, 2, 3],
      index: 0,
      next() {
        if (this.index < this.data.length) {
          return { value: this.data[this.index++], done: false };
        } else {
          return { value: undefined, done: true };
        }
      }
    };
    
    console.log(iterable.next()); // { value: 1, done: false }
    console.log(iterable.next()); // { value: 2, done: false }
    console.log(iterable.next()); // { value: 3, done: false }
    console.log(iterable.next()); // { value: undefined, done: true }
    
## 1.2 Synchronous Generators

#### A generator is a function that produces an iterator using the function* syntax and yield keyword.
    Example: Generator Function
    
    function* generateNumbers() {
      yield 1;
      yield 2;
      yield 3;
    }
    
    const generator = generateNumbers();
    
    console.log(generator.next()); // { value: 1, done: false }
    console.log(generator.next()); // { value: 2, done: false }
    console.log(generator.next()); // { value: 3, done: false }
    console.log(generator.next()); // { value: undefined, done: true }

### Why use Generators?

+ They are lazy: values are generated on demand.
+ They don’t store all values in memory, making them efficient.
+ They pause execution (yield) and resume when needed.

## 2. Async Iterators & Generators

### Async Iterators and Generators extend this concept to asynchronous operations, such as fetching data from an API, reading files, or processing streams.

## 2.1 Async Iterators (Symbol.asyncIterator)

#### An async iterator follows the same principle as an iterator, but it returns Promises instead of direct values.
    Example: Async Iterator
    
    const asyncIterable = {
      data: [10, 20, 30],
      index: 0,
      async next() {
        if (this.index < this.data.length) {
          return new Promise(resolve => {
            setTimeout(() => {
              resolve({ value: this.data[this.index++], done: false });
            }, 1000);
          });
        } else {
          return { value: undefined, done: true };
        }
      },
      [Symbol.asyncIterator]() {
        return this;
      }
    };
    
    // Usage
    (async function() {
      for await (const num of asyncIterable) {
        console.log(num); // Logs 10, 20, 30 with a delay of 1s each
      }
    })();

#### ✅ Key Benefits: Handles asynchronous data sources without blocking execution.


## 2.2 Async Generators (async function*)

### An async generator is a special function that returns an AsyncIterator. It uses await inside and yield to pause execution.
    Example: Async Generator
    
    async function* asyncNumberGenerator() {
      let i = 1;
      while (i <= 3) {
        await new Promise(resolve => setTimeout(resolve, 1000)); // Simulate async delay
        yield i++;
      }
    }
    
    (async function() {
      for await (const num of asyncNumberGenerator()) {
        console.log(num); // Logs 1, 2, 3 with a delay of 1s each
      }
    })();

### ✅ Use Cases:

+ Fetching paginated data
+ Processing real-time streaming data
+ Handling large datasets

# 3. Real-World Use Cases of Async Generators
## 3.1 Fetching Paginated API Data

### Many APIs return paginated responses, requiring multiple requests. Async generators make this process seamless.
    Example: Fetching Paginated Data
    
    async function* fetchPaginatedData() {
      let page = 1;
      while (page <= 3) {
        const response = await fetch(`https://api.example.com/data?page=${page}`);
        const data = await response.json();
        yield data; // Yield API response
        page++;
      }
    }
    
    (async function() {
      for await (const pageData of fetchPaginatedData()) {
        console.log("Received Page Data:", pageData);
      }
    })();

### ✅ Why Use Async Generators?

+ Fetches data on demand (lazy loading).
+ Handles API rate limits by pausing between requests.
+ Optimizes network usage instead of fetching everything at once.

## 3.2 Processing Streaming Data (WebSockets, Files)

### When working with WebSockets or file streams, you need to handle data continuously.
    Example: Async Generator for WebSocket Stream
    
    async function* streamWebSocket(url) {
      const socket = new WebSocket(url);
    
      socket.onmessage = event => socket.queue.push(event.data);
      socket.queue = [];
    
      while (true) {
        if (socket.queue.length > 0) {
          yield socket.queue.shift();
        } else {
          await new Promise(resolve => setTimeout(resolve, 100)); // Wait for data
        }
      }
    }
    
    // Usage
    (async function() {
      for await (const message of streamWebSocket("wss://example.com/socket")) {
        console.log("Received message:", message);
      }
    })();

### ✅ Why Use Async Generators for Streams?

+ Efficient data processing (only processes data when available).
+ Non-blocking execution (continues execution while waiting for data).
+ Reduces memory usage (doesn’t store all messages in memory).

## 4. When to Use Async Generators?

✅ Use Async Generators When: <br>
✔ You need to fetch paginated API data lazily. <br>
✔ You want to process large files or streams efficiently. <br>
✔ You’re dealing with real-time data like WebSockets. <br>
✔ You need to avoid blocking the event loop. <br>

❌ Avoid if: <br>

+ You don’t need async processing (use regular generators).
+ You don’t need streaming data (a simple for-await-of loop may be sufficient).

### Quick Summary

✅ Async Generators make handling asynchronous streaming data simple and efficient. <br>
✅ They help with API pagination, WebSockets, file processing, and real-time applications. <br>
✅ for-await-of loops simplify consumption, keeping code clean and readable. <br>
