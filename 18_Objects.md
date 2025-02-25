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
