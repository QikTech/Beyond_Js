# What is null value

+ Explicit absence of a value: null is an intentional empty value assigned to a variable.
+ Used for object-related values: Often used to represent that an object or value is intentionally missing.
+ It is one of JavaScript's primitive values.
+ The type of null value is object.
+ You can empty the variable by setting the value to null.
        
        Examples of null
        
        let y = null; // Explicitly assigned empty value
        console.log(y); // null
        
        let user = { name: null }; // Property exists but has no value
        console.log(user.name); // null



# What is undefined property

+ Default absence of a value: A variable that has been declared but not assigned a value automatically has undefined.
+ Property that doesn’t exist: Accessing an object property that isn’t defined returns undefined.
+ Function without a return statement: A function that does not return anything implicitly returns undefined.
+ Array element that doesn’t exist: Accessing an array index that doesn’t exist returns undefined.
+ The type of undefined value is undefined too.

        let x; // No value assigned
        console.log(x); // undefined
        
        let obj = {};
        console.log(obj.name); // undefined (property doesn't exist)
        
        function myFunc() {} // No return statement
        console.log(myFunc()); // undefined
        
        let arr = [10, 20];
        console.log(arr[5]); // undefined (index does not exist)


### What is the difference between null and undefined

Below are the main differences between null and undefined,
Null                                                             |    Undefined 
---                                                              |                            --- 
Variable is explicitly set to empty                              |    Variable is declared but not assigned a value
Type: object (due to legacy reasons)                             |    Type: undefined (primitive)
Intentional empty value                                          |    Default state for uninitialized variables
Can be set to null explicitly                                    |    Missing property returns undefined
Must be explicitly returned                                      |    If no return statement, returns undefined
Type of null is object                                           |    Type of undefined is undefined
Converted to zero (0) while performing primitive operations      |	Converted to NaN while performing primitive operations
