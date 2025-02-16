# First Order Function
### A first-order function (also called a first-order function in programming and mathematics) is a function that does not take other functions as arguments and does not return another function as a result. It operates only on basic data types like numbers, strings, or objects.
    
    function add(a, b) {
        return a + b;
    }
    console.log(add(2, 3)); // Output: 5

#### Here, add is a first-order function because:

+ It takes two numbers as arguments.
+ It returns a number.
+ It does not accept or return another function.

## First-Order vs. Higher-Order Functions:

### A higher-order function can take functions as parameters or return functions. Example:

    function operate(operation, a, b) {
        return operation(a, b);
    }
    
    console.log(operate(add, 2, 3)); // Output: 5

##### Here, operate is a higher-order function because it takes another function (add) as an argument.
