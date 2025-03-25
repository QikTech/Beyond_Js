Array Destructuring in JavaScript

Array destructuring allows you to unpack values from an array into distinct variables easily.
1. Basic Destructuring

const numbers = [1, 2, 3];

const [a, b, c] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3

2. Skipping Elements

You can skip elements using empty commas _ or simply omit values.

const numbers = [10, 20, 30, 40];

const [first, , third] = numbers;

console.log(first); // 10
console.log(third); // 30

3. Default Values

If the array does not have enough elements, you can set default values.

const numbers = [5];

const [x = 10, y = 20] = numbers;

console.log(x); // 5
console.log(y); // 20 (default value)

4. Swapping Variables

Array destructuring makes swapping values easy.

let a = 1, b = 2;

[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1

5. Rest Operator (...)

The rest operator (...) collects the remaining values into an array.

const fruits = ["Apple", "Banana", "Mango", "Orange"];

const [first, second, ...rest] = fruits;

console.log(first); // Apple
console.log(second); // Banana
console.log(rest); // ["Mango", "Orange"]

6. Nested Array Destructuring

You can destructure nested arrays.

const numbers = [1, [2, 3], 4];

const [a, [b, c], d] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
console.log(d); // 4

7. Destructuring with Functions

You can use destructuring with function return values.

function getCoordinates() {
  return [10, 20];
}

const [x, y] = getCoordinates();

console.log(x); // 10
console.log(y); // 20

8. Destructuring in Function Parameters

function printNames([first, second]) {
  console.log(first, second);
}

const names = ["Alice", "Bob"];
printNames(names); // Alice Bob

Summary
Feature	Example
Basic Destructuring	[a, b] = [1, 2]
Skipping Elements	[a, , c] = [1, 2, 3]
Default Values	[a = 10] = []
Swapping Variables	[a, b] = [b, a]
Rest Operator	[a, ...rest] = [1, 2, 3]
Nested Arrays	[a, [b, c]] = [1, [2, 3]]
Function Return Value	[x, y] = getCoordinates()
