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
