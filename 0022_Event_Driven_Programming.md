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
