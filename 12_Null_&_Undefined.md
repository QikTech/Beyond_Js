# What is null value

### The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values. The type of null value is object. You can empty the variable by setting the value to null.

    var user = null;
    console.log(typeof user); //object

# What is undefined property

### The undefined property indicates that a variable has not been assigned a value, or declared but not initialized at all. The type of undefined value is undefined too.

    var user; // Value is undefined, type is undefined
    console.log(typeof user); //undefined

#### Any variable can be emptied by setting the value to undefined.

    user = undefined;

### What is the difference between null and undefined

Below are the main differences between null and undefined,
| Null | Undefined| 
It is an assignment value which indicates that variable points to no object.  |	It is not an assignment value where a variable has been declared but has not yet been assigned a value. |
Type of null is object 	Type of undefined is undefined
The null value is a primitive value that represents the null, empty, or non-existent reference. 	The undefined value is a primitive value used when a variable has not been assigned a value.
Indicates the absence of a value for a variable 	Indicates absence of variable itself
Converted to zero (0) while performing primitive operations 	Converted to NaN while performing primitive operations
