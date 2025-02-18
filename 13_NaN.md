# What is NaN?

### The isNaN() function is used to determine whether a value is an illegal number (Not-a-Number) or not. i.e, This function returns true if the value equates to NaN. Otherwise it returns false.

### 1. NaN is a primitive value in JavaScript that is returned when a mathematical operation fails to produce a valid number.
    // Example:
    
    console.log(0 / 0);        // NaN
    console.log(Math.sqrt(-1)); // NaN
    console.log(parseInt("abc")); // NaN

### 2. Properties of NaN

    NaN is a type of number

    console.log(typeof NaN); // "number"

    Even though NaN means "Not-a-Number", JavaScript treats it as a number type.

### NaN is not equal to itself (NaN !== NaN)

    console.log(NaN === NaN); // false

    This makes NaN unique because it's the only value in JavaScript that is not equal to itself.

## 3. How to Check for NaN?
### Using isNaN() (Global Function)

### The isNaN() function checks if a value is NaN. However, it has some pitfalls because it tries to convert non-number values into numbers before checking.

    console.log(isNaN(NaN));        // true
    console.log(isNaN("hello"));    // true (because "hello" is converted to NaN)
    console.log(isNaN(123));        // false

## Using Number.isNaN() (Safer Alternative)

#### The Number.isNaN() method is a more reliable way to check for NaN because it does not try to convert the value before checking.
    
    console.log(Number.isNaN(NaN));        // true
    console.log(Number.isNaN("hello"));    // false (does not convert string)
    console.log(Number.isNaN(123));        // false

## 4. Common Causes of NaN
#### 1. Invalid Mathematical Operations
      
    console.log(0 / 0);          // NaN
    console.log(Math.sqrt(-1));  // NaN
    console.log(Math.log(-1));   // NaN
    console.log(Infinity - Infinity); // NaN

#### 2. Attempting Arithmetic with Non-Numeric Values

    console.log("hello" * 2);  // NaN
    console.log(undefined + 1); // NaN
    console.log("100px" - 50);  // NaN

#### 3. parseInt() and parseFloat() on Invalid Strings

    console.log(parseInt("abc"));   // NaN
    console.log(parseFloat("xyz")); // NaN

## 5. How to Handle NaN?

#### To avoid NaN in calculations, always validate input values before performing arithmetic.
#### Using isNaN() or Number.isNaN()

      let value = "hello";
      if (Number.isNaN(Number(value))) {
          console.log("Invalid input!");
      } else {
          console.log("Valid number!");
      }
      
      Using Default Values (|| Operator)
      
      let result = parseInt("abc") || 0; 
      console.log(result); // 0 instead of NaN

## 6. Summary

+ NaN means "Not-a-Number" and represents invalid mathematical operations.
+ typeof NaN === "number" even though it's not a valid number.
+ NaN !== NaN (it’s the only value in JavaScript that’s not equal to itself).
+ Best way to check for NaN? Use Number.isNaN(), not isNaN().
+ Prevent NaN by validating inputs and handling errors properly.
