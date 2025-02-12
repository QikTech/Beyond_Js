# Lexical Scope in JavaScript

### Lexical scope (also called static scope) refers to the ability of a function to access variables from its outer scope at the time the function is defined, not when it is executed.

#### In JavaScript, scope is determined lexically, meaning that the position of functions and blocks in the code defines their scope.

## How Lexical Scope Works

### When a function is defined inside another function, the inner function has access to:

+ Its own local variables.
+ The variables of all its outer (parent) functions.
+ Global variables.

## Example 1: Lexical Scope in Action

    function outerFunction() {
        let outerVar = "I'm from outerFunction";
    
        function innerFunction() {
            console.log(outerVar); // Can access outerVar
        }
    
        innerFunction();
    }
    
    outerFunction();
    // Output: "I'm from outerFunction"
    
    Explanation:
    
    innerFunction is defined inside outerFunction, so it has access to outerVar due to lexical scope.

## Example 2: Lexical Scope vs. Local Scope

    function outer() {
        let x = 10;
    
        function inner() {
            let y = 20;
            console.log(x); // ✅ Can access x from outer()
            console.log(y); // ✅ Can access y (own variable)
        }
    
        inner();
        console.log(y); // ❌ Error! y is not defined in outer()
    }
    
    outer();
    
    Key Takeaways:
    
        inner() can access x because of lexical scope.
        outer() cannot access y because y is local to inner().

## Example 3: Lexical Scope with Nested Functions

    function grandParent() {
        let a = "Grandparent";
    
        function parent() {
            let b = "Parent";
    
            function child() {
                let c = "Child";
                console.log(a); // ✅ Accesses grandparent variable
                console.log(b); // ✅ Accesses parent variable
                console.log(c); // ✅ Accesses own variable
            }
    
            child();
        }
    
        parent();
    }
    
    grandParent();
    
    Output:
    
    Grandparent
    Parent
    Child
    
    Explanation:
    
        child() can access b from parent() and a from grandParent(), due to lexical scope.
        parent() cannot access c, as it is local to child().

## Lexical Scope with Closures

    Closures are possible because of lexical scoping—inner functions "remember" the scope they were defined in.
    
    function outer() {
        let counter = 0;
    
        return function inner() {
            counter++;
            console.log(counter);
        };
    }
    
    const increment = outer();
    increment(); // 1
    increment(); // 2
    increment(); // 3
    
    Even though outer() has finished execution, inner() retains access to counter due to lexical scope.


## Lexical Scope vs. Dynamic Scope

    JavaScript follows lexical scope, meaning the function's scope is determined at the time of definition, not at the time of execution.
    
    If JavaScript used dynamic scope, it would check variables based on where the function is called, not where it is defined.
    Example: Lexical Scope in JavaScript
    
    function foo() {
        console.log(myVar);
    }
    
    function bar() {
        let myVar = "Hello";
        foo();
    }
    
    bar(); // ❌ ReferenceError: myVar is not defined
    
    Even though foo() is called inside bar(), it does not have access to myVar from bar(), because JavaScript uses lexical scoping.
    
    If JavaScript had dynamic scope, foo() would look for myVar in the function that called it (bar()).
    
# Conclusion

+ Lexical scope means functions can access variables from their outer scope where they were defined.
+ Lexical scope is static, meaning it does not change based on where a function is called.
+ This concept is fundamental for closures, function nesting, and modular programming.
