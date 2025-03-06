# Event-Driven Programming (EDP)
## What is Event-Driven Programming?
Event-Driven Programming (EDP) is a programming paradigm where the flow of execution is determined by events like user actions, system signals, or messages from other programs.
- Node.js is inherently event-driven. It is built around an event-driven, non-blocking I/O model, making it highly efficient for handling asynchronous tasks like network requests, file I/O, and real-time applications.

## Key Concepts of Event-Driven Programming

1. Events
	- Actions or occurrences that the program responds to.
	- Example: Button clicks, mouse movements, API responses.

2. Event Handlers (Listeners)
	- Functions that are executed in response to events.
	- Example: A function that runs when a button is clicked.

3. Event Loop
	- A continuous loop that listens for and dispatches events.
	- Ensures the program keeps running and responding to events.

4. Event Emitter/Dispatcher
	- A mechanism to generate and propagate events.
	- Example: In Node.js, EventEmitter is used to trigger custom events.

5. Callbacks & Promises
	- Used to handle asynchronous operations triggered by events.

### Example in JavaScript (Browser)

		document.getElementById("myButton").addEventListener("click", function() {
		alert("Button clicked!");
		});
		
		Here, addEventListener listens for a click event, and when triggered, it executes the given function.
		Example in Node.js
		
		const EventEmitter = require('events');
		const eventEmitter = new EventEmitter();
		
		// Define an event handler
		eventEmitter.on('greet', (name) => {
		console.log(`Hello, ${name}!`);
		});
		
		// Trigger the event
		eventEmitter.emit('greet', 'Prasad');
		
		Output:
		
		Hello, Prasad!
		
		Here, emit triggers the event, and the corresponding handler executes.

### Advantages of Event-Driven Programming

✅ Better User Experience - Ideal for interactive applications like UI/UX-driven software. <br>
✅ Efficient Resource Usage - Events occur only when needed, reducing unnecessary computations. <br>
✅ Asynchronous Processing - Handles multiple events without blocking execution. <br>
✅ Modularity & Scalability - Components remain independent, making it easy to modify and scale.

### Common Use Cases

📌 Graphical User Interfaces (GUIs) - Web and mobile apps (React, Flutter, Android). <br>
📌 Game Development - Handling user inputs, collisions, animations. <br>
📌 IoT (Internet of Things) - Sensor-based event handling. <br>
📌 Networking & Servers - Node.js servers processing HTTP requests asynchronously. <br>
📌 Real-time Applications - Chat applications, stock price tracking, live notifications.

___

# Does Node.js Follow Event-Driven Programming (EDP)?

## Node.js is inherently event-driven. It is built around an event-driven, non-blocking I/O model, making it highly efficient for handling asynchronous tasks like network requests, file I/O, and real-time applications.

## How Node.js Uses Event-Driven Programming

1. Event Loop
	- Node.js runs on a single-threaded event loop that listens for events and executes corresponding callbacks.
	- It does not block execution, making it ideal for handling thousands of simultaneous connections.

2. EventEmitter Module
	- The events module in Node.js allows defining and handling custom events.

3. Asynchronous Callbacks & Promises
	- Functions execute when an event occurs, rather than following a linear execution flow.

## Example: EventEmitter in Node.js
		
	const EventEmitter = require('events');
	const eventEmitter = new EventEmitter();
	
	// Define an event listener
	eventEmitter.on('greet', (name) => {
	    console.log(`Hello, ${name}!`);
	});
	
	// Emit (trigger) the event
	eventEmitter.emit('greet', 'Prasad');
	
	Output:
	
	Hello, Prasad!

	// Here, Node.js listens for the "greet" event and executes the callback when it's triggered.

### Event-Driven Nature in Node.js APIs
## Many built-in Node.js modules work on an event-driven basis, such as:
### 1. Handling File System Events (fs module)
		
	const fs = require('fs');
	
	fs.watch('test.txt', (event, filename) => {
	    console.log(`File changed: ${filename}, Event: ${event}`);
	});
	
	// The fs.watch() function listens for changes in the file and runs the callback whenever a change occurs.

### 2. Handling HTTP Requests (http module)
			
	const http = require('http');
	
	const server = http.createServer((req, res) => {
	    res.writeHead(200, { 'Content-Type': 'text/plain' });
	    res.end('Hello, World!');
	});
	
	server.listen(3000, () => console.log('Server is running on port 3000'));
	
	// The server listens for incoming requests and responds when an event (HTTP request) occurs.

### 3. Handling Streams (Event-Driven I/O)
		
	const fs = require('fs');
	
	const readStream = fs.createReadStream('example.txt');
	
	readStream.on('data', (chunk) => {
	    console.log('Received data:', chunk.toString());
	});

	// Streams in Node.js use events like 'data', 'end', and 'error' for handling large amounts of data efficiently.

## Why is Node.js Event-Driven?

✅ Non-Blocking & Asynchronous - Handles multiple tasks without waiting for one to finish. <br>
✅ Efficient for I/O Operations - Great for real-time applications like chat apps, APIs, and streaming services. <br>
✅ Scalable - Supports thousands of concurrent connections without creating multiple threads.

## Use Cases of Event-Driven Programming in Node.js

📌 Web Servers - Handling HTTP requests asynchronously. <br>
📌 Chat Applications - Using WebSockets (e.g., socket.io). <br>
📌 Real-Time Streaming - Video or audio streaming services. <br>
📌 IoT Applications - Handling sensor events in real time. <br>
📌 Background Tasks & Job Queues - Processing delayed jobs efficiently.

## Conclusion
Node.js follows Event-Driven Programming as its core architecture. Its event loop, EventEmitter, and built-in modules like http, fs, and streams make it an ideal platform for handling asynchronous, real-time applications.
