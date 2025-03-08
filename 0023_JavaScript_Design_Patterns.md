# JavaScript Design Patterns

Design patterns are reusable solutions to common software design problems. In JavaScript, they help organize code, improve maintainability, and enhance scalability.
Key Points to Speak in an Interview:

## ✅ 1. Types of Design Patterns in JavaScript:

+ Creational Patterns (Singleton, Factory, Builder)
+ Structural Patterns (Module, Decorator, Proxy)
+ Behavioral Patterns (Observer, Strategy, Command)

## ✅ 2. Commonly Used Patterns:

+ Module Pattern: Encapsulates private and public methods using closures.
+ Singleton Pattern: Ensures only one instance of an object exists.
+ Factory Pattern: Creates objects without specifying exact classes.
+ Observer Pattern: Used in event-driven programming (e.g., EventEmitter in Node.js).

## ✅ 3. Why Use Design Patterns?

+ Improves code reusability and scalability.
+ Makes code maintainable and structured.
+ Helps in writing efficient and optimized applications.

## ✅ 4. Real-World Examples:

+ React Hooks use the Observer Pattern (e.g., useEffect watching state changes).
+ Redux follows the Flux/Observer Pattern for state management.
+ Express Middleware follows the Chain of Responsibility Pattern.

## In JavaScript, we use design patterns to manage object creation, code structure, and interactions between components effectively.

### 📌 Categories of JavaScript Design Patterns

### JavaScript design patterns can be broadly classified into three main categories:
## 1️⃣ Creational Patterns (Object Creation)

#### These patterns help create objects in a flexible and efficient way.

Pattern	|| Purpose ||	Example
|| ---- || ---- || ---- ||
Singleton	|| Ensures a class has only one instance and provides a global access point. ||	Database connection, Logging system.
Factory ||	Creates objects without specifying the exact class. ||	Creating different types of user objects (Admin, Guest, Member).
Builder ||	Constructs complex objects step by step. ||	Configuring a car with custom features.

## 2️⃣ Structural Patterns (Code Organization)

These patterns define the structure and composition of code components.

Pattern ||	Purpose ||	Example
Module ||	Encapsulates related functions, making them reusable and maintainable. ||	ES6 Modules (import/export).
Decorator ||	Dynamically adds behavior to objects without modifying them. ||	Middleware in Express.js.
Proxy	|| Controls access to an object, adding extra functionality. ||	API request caching, Virtual DOM in React.

## 3️⃣ Behavioral Patterns (Communication & Interaction)

These patterns focus on how objects interact and behave.

Pattern ||	Purpose ||	Example
Observer ||	Establishes a one-to-many relationship, where one object updates multiple dependent objects. ||	Event handling (addEventListener), Redux store updates.
Strategy ||	Defines a family of algorithms and makes them interchangeable. ||	Payment processing (PayPal, Stripe, Razorpay).
Command ||	Encapsulates a request as an object, allowing delayed execution. ||	Undo/Redo functionality.


# 🛠️ Commonly Used JavaScript Design Patterns (With Examples)
## 1️⃣ Module Pattern (Encapsulation & Privacy)

Encapsulates functions and variables inside a self-contained unit, preventing global scope pollution.
    
    const Counter = (function () {
        let count = 0;  // Private variable
    
        return {
            increment: function () { count++; },
            decrement: function () { count--; },
            getCount: function () { return count; }
        };
    })();
    
    Counter.increment();
    console.log(Counter.getCount());  // Output: 1
    
📌 Why use this?
+ Prevents direct modification of variables.
+ Encapsulates logic inside a function (Encapsulation).

## 2️⃣ Singleton Pattern (Ensuring a Single Instance)

Ensures that a class has only one instance and provides a global point of access.

    
    class Database {
        constructor() {
            if (!Database.instance) {
                this.connection = "Connected to DB";
                Database.instance = this;
            }
            return Database.instance;
        }
    }
    
    const db1 = new Database();
    const db2 = new Database();
    console.log(db1 === db2); // Output: true (same instance)

📌 Where is it used?
+ Database connections
+ Logging systems

## 3️⃣ Factory Pattern (Flexible Object Creation)

A function that returns an object without using new keyword, making object creation more flexible.
    
    function UserFactory(role) {
        if (role === "admin") return { role: "Admin", permissions: ["read", "write", "delete"] };
        if (role === "guest") return { role: "Guest", permissions: ["read"] };
    }
    
    const admin = UserFactory("admin");
    const guest = UserFactory("guest");
    
    console.log(admin); // { role: "Admin", permissions: ["read", "write", "delete"] }

📌 Where is it used?
+ Creating user roles
+ Generating different UI components dynamically

## 4️⃣ Observer Pattern (Event-Based Communication)

Defines a one-to-many relationship, where multiple objects listen for state changes in one object.
    
    
    class Subject {
        constructor() {
            this.observers = [];
        }
        
        subscribe(observer) {
            this.observers.push(observer);
        }
        
        notify(data) {
            this.observers.forEach(observer => observer(data));
        }
    }
    
    const newsChannel = new Subject();
    
    // Subscriber 1
    newsChannel.subscribe(data => console.log("Subscriber 1 received:", data));
    
    // Subscriber 2
    newsChannel.subscribe(data => console.log("Subscriber 2 received:", data));
    
    newsChannel.notify("Breaking News: JavaScript is awesome!");

📌 Where is it used?

+ Event handling (addEventListener)
+ Redux store updates (React state management)

## 5️⃣ Decorator Pattern (Adding Extra Features Dynamically)

    // Allows adding new functionality to an object dynamically without modifying its structure.
    🔹 Example:
    
    function addLogging(originalFunction) {
        return function (...args) {
            console.log("Logging: ", args);
            return originalFunction.apply(this, args);
        };
    }
    
    function greet(name) {
        return `Hello, ${name}!`;
    }
    
    const enhancedGreet = addLogging(greet);
    console.log(enhancedGreet("Alice")); // Logs: Logging: ["Alice"], then returns "Hello, Alice!"

📌 Where is it used?

+ Express Middleware (logging, authentication, error handling)

## 🔹 Why Are Design Patterns Important?

✅ Improves code reusability and scalability. <br>
✅ Makes code maintainable and structured. <br>
✅ Helps in writing efficient and optimized applications. <br>
✅ Promotes best practices for solving recurring problems. <br>

## 🔥 Real-World Applications of Design Patterns in JavaScript 

🚀 React.js → Uses Observer Pattern in state management (Redux) <br>
🚀 Express.js → Uses Middleware (Decorator Pattern) for request handling <br>
🚀 Node.js EventEmitter → Implements Observer Pattern for event-driven programming <br>
🚀 Database Connections → Implemented using Singleton Pattern <br>
🚀 Payment Systems (Stripe, Razorpay) → Use Strategy Pattern for different payment gateways
