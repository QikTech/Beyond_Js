# Call by Value vs Call by Reference

## Call by Value
In Call by Value, a copy of the actual argument is passed to the function, and any modifications inside the function do not affect the original variable.

## Call by Reference

In Call by Reference, a reference (or address) of the actual argument is passed to the function, allowing modifications inside the function to directly affect the original variable.

## Call by Value in JavaScript

In Call by Value, when passing primitive data types (e.g., Number, String, Boolean), a copy of the value is passed to the function. Any changes inside the function do not affect the original variable.

## Call by Reference in JavaScript

In Call by Reference, when passing Objects or Arrays, a reference to the original data is passed. Changes made to the object inside the function will reflect in the original object. However, reassigning the object inside the function does not affect the original reference (JavaScript follows Call by Sharing).
Both Call by Value and Call by Reference are ways to pass arguments to a function in programming. The key difference lies in how they handle the arguments.

## Call by Value vs Call by Reference in JavaScript

JavaScript follows Call by Value for primitive types and Call by Reference (or Call by Sharing) for objects.

## 1. Call by Value (Primitives)

+ When passing primitive data types (e.g., Number, String, Boolean), a copy of the value is passed.
+ Modifications inside the function do not affect the original variable.

      Example (Call by Value)
      
      function modifyValue(x) {
          x = x + 10;
          console.log("Inside function:", x);
      }
      
      let a = 5;
      modifyValue(a);
      console.log("Outside function:", a); // Original value remains unchanged
      
      Output:
      
      Inside function: 15
      Outside function: 5

## 2. Call by Reference (Objects & Arrays)

+ When passing Objects or Arrays, a reference to the original data is passed.
+ Changes inside the function affect the original object.
      
      Example (Call by Reference)
      
      function modifyObject(obj) {
          obj.value = obj.value + 10;
          console.log("Inside function:", obj);
      }
      
      let data = { value: 5 };
      modifyObject(data);
      console.log("Outside function:", data); // Original object is modified
      
      Output:
      
      Inside function: { value: 15 }
      Outside function: { value: 15 }
      
## Important Note: JavaScript Uses "Call by Sharing"

+ JavaScript does not truly use Call by Reference, because reassigning the object inside the function does not affect the original object.
          Example:
      
      function reassignObject(obj) {
          obj = { value: 100 }; // Reassigning a new object
          console.log("Inside function:", obj);
      }
      
      let data = { value: 5 };
      reassignObject(data);
      console.log("Outside function:", data); // Original object remains unchanged
      
      Output:
      
      Inside function: { value: 100 }
      Outside function: { value: 5 }
      
      Here, only the local variable obj inside the function is modified, not the original data.

  ## Conclusion

+ Primitives (Numbers, Strings, Booleans, etc.) → Call by Value (unchanged)
+ Objects & Arrays → Call by Sharing (mutations affect the original object, but reassignment doesn't)



# In General Programming

## 1. Call by Value In General Programming

+ A copy of the actual argument is passed to the function.
+ Changes made inside the function do not affect the original variable.
+ Memory for function arguments is allocated separately.
+ Used in languages like C, Java (for primitive data types), Python (for immutable types like int, str, tuple).

      Example (C - Call by Value)
      
      #include <stdio.h>
      
      void modify(int x) {
          x = x + 10;
          printf("Inside function: %d\n", x);
      }
      
      int main() {
          int a = 5;
          modify(a);
          printf("Outside function: %d\n", a); // Original value remains unchanged
          return 0;
      }
      
      Output:
      
      Inside function: 15
      Outside function: 5
      
## 2. Call by Reference In General Programming

+ Instead of passing a copy, a reference (or address) to the actual argument is passed.
+ Changes made inside the function reflect in the original variable.
+ No separate memory is allocated for function arguments.
+ Used in **C++ (with references), Java (for objects), Python

