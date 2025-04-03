# Function Parameters Destructuring in JavaScript

### Function parameters destructuring allows you to extract values from objects or arrays directly within the function signature, making your code more concise and readable.
## 1️⃣ Destructuring Object Parameters

Instead of accessing object properties inside a function, you can destructure them in the function parameters.
🔹 Without Destructuring

function greet(user) {
  console.log(`Hello, ${user.name}! Your age is ${user.age}`);
}

const user = { name: "Prasad", age: 30 };
greet(user);

✅ With Destructuring

function greet({ name, age }) {
  console.log(`Hello, ${name}! Your age is ${age}`);
}

greet({ name: "Prasad", age: 30 });

Why is this better?

    Reduces repetitive code (user.name → name, user.age → age).

    Improves readability.

## 2️⃣ Setting Default Values in Destructured Parameters

If a property is missing, you can assign a default value.

function greet({ name = "Guest", age = 25 }) {
  console.log(`Hello, ${name}! Your age is ${age}`);
}

greet({ name: "Prasad" }); // Output: Hello, Prasad! Your age is 25
greet({}); // Output: Hello, Guest! Your age is 25

When is this useful?

    When working with optional properties.

    Avoids undefined errors.

## 3️⃣ Destructuring Nested Objects

You can extract nested properties inside function parameters.

const user = {
  name: "Prasad",
  address: {
    city: "Mumbai",
    pin: 400001,
  },
};

function showAddress({ address: { city, pin } }) {
  console.log(`City: ${city}, PIN: ${pin}`);
}

showAddress(user); // Output: City: Mumbai, PIN: 400001

Why use this?

    Avoids deep property access (user.address.city → city).

    Keeps function concise.

## 4️⃣ Rest Operator (...) in Function Parameters

You can capture remaining properties using the rest (...) operator.

function displayUser({ name, ...rest }) {
  console.log(`Name: ${name}`);
  console.log("Other Details:", rest);
}

displayUser({ name: "Prasad", age: 30, role: "Tech Lead" });
// Output:
// Name: Prasad
// Other Details: { age: 30, role: 'Tech Lead' }

Use Cases:

    Extract only specific properties and keep the rest.

    Useful in dynamic data structures.

## 5️⃣ Destructuring Array Parameters

Functions can destructure arrays, similar to objects.
🔹 Without Destructuring

function sum(arr) {
  return arr[0] + arr[1];
}

console.log(sum([10, 20])); // Output: 30

✅ With Destructuring

function sum([first, second]) {
  return first + second;
}

console.log(sum([10, 20])); // Output: 30

Advantages:

    Avoids arr[0], arr[1] syntax.

    More readable function signatures.

## 6️⃣ Combining Object and Array Destructuring

You can mix both in function parameters.

const user = {
  name: "Prasad",
  hobbies: ["Cricket", "Reading"],
};

function showHobbies({ name, hobbies: [hobby1, hobby2] }) {
  console.log(`${name}'s hobbies: ${hobby1} and ${hobby2}`);
}

showHobbies(user); // Output: Prasad's hobbies: Cricket and Reading

Why use this?

    When handling structured API responses.

    Makes accessing nested data easier.

## 7️⃣ Destructuring Function Return Values

You can destructure function return values in parameters.

function getUser() {
  return { name: "Prasad", age: 30 };
}

function greet({ name, age }) {
  console.log(`Hello, ${name}! Age: ${age}`);
}

greet(getUser()); // Output: Hello, Prasad! Age: 30

Use Case:

    When working with API responses or dynamic data.

Conclusion

Function parameter destructuring makes functions cleaner, reduces redundant property access, and improves readability. It’s widely used in: ✅ React (useState, props handling)
✅ API response handling
✅ Working with nested objects & arrays
