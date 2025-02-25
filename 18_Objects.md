# Objects in JavaScript: A Detailed Guide

### In JavaScript, An object is a collection of key-value pairs, where each key (also called a property) is a string and each value can be any data type, including other objects and functions. 
    const person = { name: "John", age: 30, isAdmin: true };

## 1. What is an Object?

#### An object is a collection of properties, where each property has a key (string) and a value (which can be any data type, including other objects and functions).
    Example of an Object
    
    const person = {
      name: "Prasad",
      age: 30,
      isDeveloper: true,
      skills: ["JavaScript", "Flutter", "AWS"],
      address: {
        city: "Mumbai",
        country: "India"
      },
      greet: function() {
        return `Hello, my name is ${this.name}`;
      }
    };
    
    console.log(person.name);         // Output: Prasad
    console.log(person.skills[1]);    // Output: Flutter
    console.log(person.address.city); // Output: Mumbai
    console.log(person.greet());      // Output: Hello, my name is Prasad

### 📌 Key Points:

+ Properties store data (name, age, skills, address).
+ Methods are functions inside objects (greet()).
+ Nested objects can store hierarchical data (address).

## 2. Creating Objects in JavaScript

### There are multiple ways to create objects in JavaScript:
### (A) Using Object Literals (Recommended)

        const car = {
          brand: "Tesla",
          model: "Model S",
          year: 2023
        };

#### ✅ Best for simple objects.

### (B) Using the new Object() Constructor
        
        const user = new Object();
        user.name = "John";
        user.age = 25;

#### ✅ Rarely used; object literals are preferred.

### (C) Using a Constructor Function
        
        function Person(name, age) {
          this.name = name;
          this.age = age;
          this.sayHello = function() {
            return `Hello, I'm ${this.name}`;
          };
        }
        
        const person1 = new Person("Alice", 28);
        console.log(person1.sayHello()); // Output: Hello, I'm Alice

#### ✅ Good for creating multiple objects of the same type.

### (D) Using Object.create() (Prototype-based)
        
        const animal = {
          type: "Mammal",
          sound: function() {
            return "Some generic sound";
          }
        };
        
        const dog = Object.create(animal);
        dog.breed = "Labrador";
        dog.sound = function() {
          return "Woof! Woof!";
        };
        
        console.log(dog.type);  // Output: Mammal (inherited)
        console.log(dog.sound()); // Output: Woof! Woof!

#### ✅ Good for prototypal inheritance.
### (E) Using Classes (ES6)
        
        class Car {
          constructor(brand, model) {
            this.brand = brand;
            this.model = model;
          }
          
          getDetails() {
            return `${this.brand} - ${this.model}`;
          }
        }
        
        const car1 = new Car("BMW", "X5");
        console.log(car1.getDetails()); // Output: BMW - X5

#### ✅ Best practice for object-oriented programming (OOP).

## 3. Accessing Object Properties
#### There are two ways to access object properties:
### (A) Dot Notation (.)
        
        console.log(person.name); // Output: Prasad

### (B) Bracket Notation ([])
    
        console.log(person["name"]); // Output: Prasad

### 📌 Use bracket notation when the key is dynamic or contains special characters:
        
        const dynamicKey = "age";
        console.log(person[dynamicKey]); // Output: 30

## 4. Adding, Modifying, and Deleting Properties
### (A) Adding New Properties

        person.country = "India";

### (B) Modifying Properties

        person.age = 31;

### (C) Deleting Properties

        delete person.age;

#### ✅ Note: delete only removes properties, but does not affect the object's prototype.

## 5. Checking for Property Existence
### (A) Using the in Operator
        
        console.log("name" in person); // Output: true
        console.log("salary" in person); // Output: false
        
### (B) Using hasOwnProperty()

        console.log(person.hasOwnProperty("name")); // Output: true

## 6. Iterating Over an Object
### (A) Using for...in Loop
        
        for (let key in person) {
          console.log(`${key}: ${person[key]}`);
        }

### (B) Using Object.keys()

        console.log(Object.keys(person)); // Output: ['name', 'isDeveloper', 'skills', 'address', 'greet']

### (C) Using Object.values()

        console.log(Object.values(person)); 
        // Output: ["Prasad", true, Array(3), {…}, ƒ greet()]

### (D) Using Object.entries()

        console.log(Object.entries(person));
        // Output: [['name', 'Prasad'], ['isDeveloper', true], ...]

## 7. Object Methods

### Objects can have functions as properties, known as methods.
        
        const user = {
          name: "Rahul",
          greet() {
            return `Hello, ${this.name}`;
          }
        };
        
        console.log(user.greet()); // Output: Hello, Rahul

#### 📌 Note: this refers to the object itself.

## 8. Object Spread (...) and Object.assign()
### (A) Using Spread Operator (...)
        
        const obj1 = { a: 1, b: 2 };
        const obj2 = { c: 3, d: 4 };
        
        const merged = { ...obj1, ...obj2 };
        console.log(merged); // Output: { a: 1, b: 2, c: 3, d: 4 }

### (B) Using Object.assign()
        
        const obj3 = Object.assign({}, obj1, obj2);
        console.log(obj3); // Output: { a: 1, b: 2, c: 3, d: 4 }

## 9. Deep vs Shallow Copy
### (A) Shallow Copy (Only One Level Deep)
        
        const objA = { x: 1, y: { z: 2 } };
        const objB = { ...objA };
        
        objB.y.z = 100;
        console.log(objA.y.z); // Output: 100 (Both objects reference the same nested object)

### (B) Deep Copy (Completely Separate Copy)
        
        const objDeep = JSON.parse(JSON.stringify(objA));
        objDeep.y.z = 200;
        console.log(objA.y.z); // Output: 100 (Original object remains unchanged)

#### ✅ Deep copying ensures nested objects are also cloned.

## 10. Object Freezing and Sealing
### (A) Object.freeze() (No Modification Allowed)
        
        const obj = { name: "Frozen" };
        Object.freeze(obj);
        obj.name = "New"; // ❌ Cannot modify
        console.log(obj.name); // Output: Frozen

### (B) Object.seal() (Modification Allowed, No New Properties)
        
        const obj2 = { name: "Sealed" };
        Object.seal(obj2);
        obj2.name = "Updated"; // ✅ Allowed
        obj2.age = 30; // ❌ Not allowed
        console.log(obj2); // Output: { name: 'Updated' }

### Conclusion
#### Objects are the backbone of JavaScript. They allow developers to store structured data efficiently and are used everywhere, from APIs to OOP concepts.
