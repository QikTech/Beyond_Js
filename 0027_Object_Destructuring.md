# Object Destructuring

### Object destructuring is a syntax that allows you to unpack properties from an object into variables, making your code cleaner and more readable.

## 1. Basic Destructuring
    
    const user = {
      name: "Prasad",
      age: 30,
      city: "Mumbai"
    };
    
    const { name, age } = user;
    console.log(name); // Prasad
    console.log(age);  // 30

##  2. Renaming Variables

You can rename the destructured variables:
    
    const { name: fullName, city: location } = user;
    console.log(fullName); // Prasad
    console.log(location); // Mumbai

## 3. Default Values

Assign default values when a property might be undefined:
    
    const { country = "India" } = user;
    console.log(country); // India

## 4. Nested Object Destructuring

You can extract values from nested objects too:
    
    const employee = {
      id: 101,
      details: {
        department: "Engineering",
        position: "Developer"
      }
    };
    
    const {
      details: { department, position }
    } = employee;
    
    console.log(department); // Engineering
    
    ⚠️ Note: If details is undefined, nested destructuring will throw an error. Use safe access:
    
    const { details: { department = "" } = {} } = employee;

## 5. Destructuring in Function Parameters

You can destructure directly in function arguments:
    
    function displayUser({ name, city }) {
      console.log(`${name} lives in ${city}`);
    }
    
    displayUser(user); // Prasad lives in Mumbai

## 6. Destructuring with Rest Operator

You can gather the remaining properties using ...rest:
    
    const { name, ...rest } = user;
    console.log(name); // Prasad
    console.log(rest); // { age: 30, city: "Mumbai" }

## 7. Destructuring in Loops
    
    const people = [
      { name: "Amit", age: 28 },
      { name: "Neha", age: 26 }
    ];
    
    for (const { name, age } of people) {
      console.log(`${name} is ${age} years old`);
    }

## Summary
Use Case |	Syntax Example
-- | --
Basic	| const { name } = user;
Renaming |	const { name: fullName } = user;
Default Values |	const { country = "India" } = user;
Nested Destructuring | const { details: { department } } = employee;
In Function Parameters |	function show({ name }) {}
With Rest Operator |	const { name, ...rest } = user;
