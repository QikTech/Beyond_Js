# A unary function is a function that takes exactly one argument. It follows the form:
##### f(x)→output
##### f(x)→output
    Example in JavaScript:
    
    function square(x) {
        return x * x;
    }
    
    console.log(square(5)); // Output: 25
    
#### Here, square is a unary function because:
+ It takes only one argument (x).
+ It returns a result based on that single argument.

# Currying
### Currying is the process of transforming a function that takes multiple arguments into a series of unary functions.
#### Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument. Currying is named after a mathematician Haskell Curry. By applying currying, an n-ary function turns into a unary function.

    const multiArgFunction = (a, b, c) => a + b + c;
    console.log(multiArgFunction(1, 2, 3)); // 6
    
    const curryUnaryFunction = (a) => (b) => (c) => a + b + c;
    curryUnaryFunction(1); // returns a function: b => c =>  1 + b + c
    curryUnaryFunction(1)(2); // returns a function: c => 3 + c
    curryUnaryFunction(1)(2)(3); // returns the number 6

## Example: Normal Function vs Curried Function

## A regular function:

    const add = (a, b) => a + b;
    console.log(add(2, 3)); // Output: 5
    
    A curried version:
    
    const curriedAdd = a => b => a + b;
    console.log(curriedAdd(2)(3)); // Output: 5

#### Here, curriedAdd(2) returns a new function b => 2 + b, which is then called with 3.

## Practical Use: Partially Applying Functions

    Currying allows partial application of functions.
    
    const multiply = a => b => a * b;
    
    const double = multiply(2);  // Partially applied function
    console.log(double(5)); // Output: 10

    Here,

    multiply(2) returns b => 2 * b.
    Calling double(5) is equivalent to 2 * 5.

📌 Why Use Currying?
+ Enables code reuse.
+ Makes functions more flexible.
+ Helps with function composition.

Summary
| Concept | Definition | Example |
| ------ | ------ | ------|
| Function Composition	| Combining multiple functions where the output of one is the input of another. |	compose(f, g)(x) = f(g(x))
| Currying |	Converting a function with multiple arguments into a sequence of unary functions. |	curriedAdd(a)(b) = a + b

🔥 Key Takeaways:

+ Unary functions take exactly one argument.
+ Composition chains unary functions together.
+ Currying breaks down multi-parameter functions into unary functions.
