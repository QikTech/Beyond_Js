# Object in JavaScript?

### An object is a collection of key-value pairs, where keys (also called properties) are strings (or Symbols), and values can be anything: strings, numbers, arrays, functions, even other objects.
    
    const person = {
      name: "Prasad",
      age: 30,
      isDeveloper: true
    };

## 1. Accessing Object Properties
    
    console.log(person.name);      // Dot notation → Prasad
    console.log(person["age"]);   // Bracket notation → 30

## 2. Adding / Updating Properties
    
    person.city = "Mumbai";         // Add
    person.age = 31;                // Update

## 3. Deleting Properties
    
    delete person.isDeveloper;

## 4. Looping through Objects
    
    for (let key in person) {
      console.log(key, person[key]);
    }

    You can also use:
    
    Object.keys(person);    // ['name', 'age', 'city']
    Object.values(person);  // ['Prasad', 31, 'Mumbai']
    Object.entries(person); // [['name', 'Prasad'], ['age', 31], ...]

## 5. Objects with Methods (Functions inside Objects)
    
    const user = {
      name: "Prasad",
      greet() {
        console.log(`Hi, I’m ${this.name}`);
      }
    };
    user.greet(); // Hi, I’m Prasad
    
    Note: this refers to the object calling the method.
##  6. Nested Objects

const student = {
  name: "Ravi",
  address: {
    city: "Pune",
    pincode: 411001
  }
};
console.log(student.address.city); // Pune

🆕 7. Object Destructuring (ES6)

const { name, age } = person;
console.log(name, age);

Nested destructuring:

const { address: { city } } = student;

📤 8. Spread & Rest with Objects

const newPerson = { ...person, country: "India" }; // Spread

const { city, ...rest } = person; // Rest

🧩 9. Object.freeze() and Object.seal()

    Object.freeze(obj) → Makes the object immutable.
    Object.seal(obj) → Allows value updates but prevents adding/removing properties.

🏗 10. Constructor Functions & Object.create()
➤ Constructor Function:

function Car(model, year) {
  this.model = model;
  this.year = year;
}
const car1 = new Car("Honda", 2022);

➤ Object.create():

const proto = {
  greet() {
    console.log("Hello!");
  }
};
const obj = Object.create(proto);
obj.greet(); // Hello!
