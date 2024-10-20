---
title: JavaScript Roadmap  
markmap: 
  colorFreezeLevel: 2 
  collapsed: false
  nodeMinHeight: 30
  # maxWidth: 300
  initialExpandLevel: 2
---
## Data Types 
- Strings 
  - Operator Precedence:
    - JavaScript has a hierarchy of operator precedence, which determines how different operators are evaluated in expressions.
    - For example, the multiplication operator (``) has higher precedence than the addition operator (`+`). Therefore, expressions with both `` and `+` operators will first evaluate the `` operation.


  - Parentheses for Explicit Precedence:
    - You can use parentheses () to explicitly specify the order of evaluation, overriding the default precedence rules.
    - Expressions within parentheses are always evaluated first.
    - ```js 
        let result = 2 + 3 * 4; // Multiplication has higher precedence, so result is 14.
        let resultWithParens = (2 + 3) * 4; // Parentheses change the order, so resultWithParens is 20.
      ```

  - Associativity:
    - If operators have the same precedence, their associativity determines the order of evaluation.
    - Most binary operators in JavaScript are left-associative, meaning they are evaluated from left to right.
    - ```js 
        let result = 5 - 3 - 1; // Left-associative: (5 - 3) - 1, result is 1.
      ```
  - Assignment Operator (=) Has Right Associativity:
    - The assignment operator = has right-associative behavior, meaning it evaluates from right to left when used in succession.
    - ```js 
        let a, b;
        a = b = 5; // The rightmost assignment is evaluated first, assigning 5 to both 'a' and 'b'.
      ```
  - Operator Precedence Table:
    - JavaScript has a well-defined operator precedence table that you can refer to when in doubt.
    - You can find the table in the MDN documentation.
    - Here's a simplified example of operator precedence and associativity:
    - ```js 
      let result = 2 + 3 * 4; // Multiplication (*) has higher precedence than addition (+).
      // Steps: 3 * 4 = 12, then 2 + 12 = 14, so 'result' is 14.
      ```
- String functions
  - `length`:
    - Returns the length (the number of characters) of a string.
    - ```js 
        let text = "Hello, World!";
        let length = text.length; // 13
      ```
  - `toUpperCase()`:
    - Converts all characters in a string to uppercase.
    - ```js 
        let text = "hello";
        let uppercaseText = text.toUpperCase(); // "HELLO"
      ```
  - `toLowerCase()`:
    - Converts all characters in a string to lowercase.
    - ```js 
        let text = "WORLD";
        let lowercaseText = text.toLowerCase(); // "world"
      ```
  - `charAt(index)`:
    - Returns the character at the specified index in the string. The index is zero-based.
    - ```js 
        let text = "JavaScript";
        let character = text.charAt(4); // "S"
      ```
  - `substring(start, end)`:
    - Returns a substring of the original string, starting from the start index (inclusive) and ending at the end index (exclusive).
    - ```js 
        let text = "Hello, World!";
        let substring = text.substring(7, 12); // "World"
      ```
  - `slice(start, end)`:
    - Similar to substring, it returns a substring, but allows negative indices (counting from the end of the string).
    - ```js 
        let text = "Hello, World!";
        let slice = text.slice(-6, -1); // "World"
      ```
  - `indexOf(substring)`:
    - Returns the index of the first occurrence of substring in the string. Returns 1 if not found.
    - ```js 
        let text = "Hello, World!";
        let index = text.indexOf("World"); // 7
      ```
  - `lastIndexOf(substring)`:
    - Returns the index of the last occurrence of substring in the string. Returns 1 if not found.
    - ```js 
        let text = "Hello, World!";
        let lastIndex = text.lastIndexOf("o"); // 8
      ```
  - `replace(oldSubstring, newSubstring)`:
    - Replaces the first occurrence of oldSubstring with newSubstring in the string.
    - ```js 
        let text = "Hello, World!";
        let newText = text.replace("World", "Universe"); // "Hello, Universe!"
      ```
  - `split(separator)`:
    - Splits the string into an array of substrings based on the specified separator. Useful for breaking text into parts.
    - ```js 
        let text = "apple,banana,cherry";
        let fruits = text.split(","); // ["apple", "banana", "cherry"]
      ```
  - `trim()`:
    - Removes leading and trailing whitespace characters (spaces, tabs, newlines) from a string.
    - ```js 
        let text = "   Hello, World!   ";
        let trimmedText = text.trim(); // "Hello, World!"
      ```
  - `concat(string1, string2, ...)`:
    - Combines multiple strings into one string.
    - ```js 
        let firstName = "John";
        let lastName = "Doe";
        let fullName = firstName.concat(" ", lastName); // "John Doe"
      ```
    - You can concatenate strings using the `+` operator or template literals (introduced in ES6).
    - ```js 
        let firstName = "John";
        let lastName = "Doe";
        let fullName = firstName + " " + lastName; // "John Doe"
        let message = `Hello, ${firstName}!`; // "Hello, John!"
      ```
- Type Coercion
  - String Concatenation:
    - JavaScript will automatically convert non-string values to strings when using the + operator for concatenation.
    - ```js 
          let num = 5;
          let str = "Hello, " + num; // "Hello, 5" (num is coerced to a string)
      ```
  ​
  - Arithmetic Operations:
    - When performing arithmetic operations, JavaScript may convert operands to numbers if needed.
    - ```js 
        let num1 = "5";
        let num2 = 10;
        let sum = num1 + num2; // "510" (both are coerced to strings)
        let total = num1 - num2; // -5 (both are coerced to numbers)
      ```
  ​
  - Comparison Operators:
    - JavaScript will coerce values to the same type before comparing them using equality (==) and inequality (!=) operators. This can lead to unexpected results.
    - ```js 
        let num = 5;
        let str = "5";
        console.log(num == str); // true (str is coerced to a number)
      ```
  ​
  - Truthy and Falsy Values:
    - JavaScript has truthy and falsy values. Values like 0, "" (empty string), null, undefined, NaN, and false are falsy. All other values are truthy.
    - ```js 
        if (0) {
          // This code won't execute because 0 is falsy.
        }
      ```
  ​
  - Logical Operators:
    - JavaScript performs type coercion when evaluating logical expressions using && and || operators.
    - ```js 
        let result = "Hello" && true; // true (both operands are truthy)
      ``` 
  ​
  - Function Arguments:
    - Function parameters can receive values of different types, and JavaScript will attempt to coerce them if necessary.
    - ```js 
        function greet(name) {
          console.log("Hello, " + name);
        }

        greet("Alice"); // "Hello, Alice"
        greet(42); // "Hello, 42" (42 is coerced to a string)
      ```

- Conversion Between String and Number Type
  - Converting Strings to Numbers:
    - Using `parseInt()` and parseFloat():
      - You can use the parseInt() function to convert a string to an integer, and parseFloat() to convert a string to a floating-point number.
      - ```js 
          let strInt = "42";
          let strFloat = "3.14";

          let numInt = parseInt(strInt); // 42
          let numFloat = parseFloat(strFloat); // 3.14
        ```
  ​
    - Using the Number() Constructor:
      - The Number() constructor can be used to convert a string to a number.
      - ```js 
          let strNum = "123";
          let num = Number(strNum); // 123
        ```
  ​
    - Using the Unary + Operator:
      - You can use the unary + operator to convert a string to a number.
      - ```js 
          let strNum = "456";
          let num = +strNum; // 456
        ```
  ​
    - Converting Numbers to Strings:
      - Using String() Constructor or .toString() Method:
      - You can use the String() constructor or the .toString() method to convert a number to a string.
      - ```js
          let num = 42;
          let str1 = String(num); // "42"
          let str2 = num.toString(); // "42"
        ```
  ​
    - Using String Concatenation:
      - You can concatenate a number with an empty string to implicitly convert it to a string.
      - ```js
          let num = 123;
          let str = num + ""; // "123"
        ```
  ​
    - Using Template Literals (ES6 and later):
      - Template literals can implicitly convert a variable to a string within a template literal string.
      - ```js
          let num = 789;
          let str = `${num}`; // "789"
        ```
  ​
    - Using .toLocaleString() Method:
      - The .toLocaleString() method converts a number to a string with localized formatting.
      - ```js 
          let num = 1000;
          let str = num.toLocaleString(); // "1,000" (formatted as per locale)
        ```
- Boolean
  - **Boolean Values**:
    - There are only two possible Boolean values: `true` and `false`. These values are case-sensitive, so `True` and `False` are not valid Boolean values.
    
    - ```jsx
        let isTrue = true;
        let isFalse = false;
      ```
  - **Boolean Expressions**:
    - Boolean expressions are conditions that evaluate to either `true` or `false`. These expressions are used in control structures like `if` statements and loops to make decisions in your code.
    - ```jsx
        if (isTrue) {
          // This block will execute because isTrue is true.
        }
        
        if (!isFalse) {
          // This block will execute because !isFalse is true (logical NOT).
        }
        
      ```
  - **Logical Operators**:
      - JavaScript provides logical operators like `&&` (logical AND), `||` (logical OR), and `!` (logical NOT) to work with Boolean values.
      
      - ```jsx
          let x = true;
          let y = false;
          
          let result1 = x && y; // false (logical AND)
          let result2 = x || y; // true (logical OR)
          let result3 = !x;     // false (logical NOT)
          
        ```
      
  - **Truthy and Falsy Values**:
      - JavaScript has truthy and falsy values. Values like `0`, `""` (empty string), `null`, `undefined`, `NaN`, and `false` are falsy. All other values are truthy.
      
      - ```jsx
          if (0) {
            // This block won't execute because 0 is falsy.
          }
          
          if ("Hello") {
            // This block will execute because "Hello" is truthy.
          }
        
        ```
      
  - **Boolean Conversion**:
      - You can convert other data types to Booleans using the `Boolean()` constructor or the double negation `!!` operator.
      
      - ```jsx
          let value = 42;
          let boolValue1 = Boolean(value); // true (any non-zero number is truthy)
          let boolValue2 = !!value;        // true
          
        ```
        
  - **Comparisons**:
      - Many JavaScript operations, like comparisons, return Boolean values. For example, `5 > 3` evaluates to `true`, and `10 === "10"` evaluates to `false`.

      - Booleans are fundamental for creating conditional logic, controlling program flow, and making decisions in JavaScript code. Understanding how to work with Booleans is essential for programming in JavaScript.


- Null
  - **Null as a Value**:
    - `null` is a JavaScript keyword that represents the intentional absence of a value.
    - It is often used to initialize a variable when you don't want it to have any initial value.
    
    - ```jsx
        let emptyValue = null;
      ```
    
  - **typeof `null`**:
    - The `typeof` operator applied to a `null` value returns `"object"`. This is a historical quirk in JavaScript and can be considered a language design flaw.
    
    - ```jsx
        typeof null; // "object"
      
      ```
    
  - **Comparison with `undefined`**:
    - While `null` and `undefined` both represent the absence of value, they are not the same. `undefined` typically indicates a variable that has been declared but hasn't been assigned any value, while `null` is often used to represent a deliberate absence of value.
    
    - ```jsx
      let undefinedValue; // This variable is undefined.
      let nullValue = null; // This variable is deliberately set to null.
      
      ```
    
  - **Checking for `null`**:
    - You can use strict equality (`===`) to check if a variable is `null`.
      
    - ```jsx
        let value = null;
        if (value === null) {
          // This block will execute because 'value' is null.
        }
      
      ```
    
  - **Common Use Cases**:
    - `null` is often used to reset or clear the value of a variable, especially when dealing with objects.
    
    - ```jsx
      let obj = { name: "Alice" };
      
      // Clearing the object's value
      obj = null;
      
      // Now 'obj' is null, and the original object is no longer accessible.
      
      ```
    
  - **Avoiding Errors**:
    - When working with potentially `null` values, it's a good practice to check if a value is `null` before accessing its properties or methods to avoid runtime errors.
    
    - ```jsx
        let user = getUserFromDatabase();
        
        if (user !== null) {
          // It's safe to access 'user' properties here.
          console.log(user.name);
        }
      ```
- Undefined
  - Declaration Without Initialization:
    - When you declare a variable without assigning an initial value to it, that variable's value is undefined.
    - ```jsx
        let myVariable;
        console.log(myVariable); // undefined
      ```
  - Function Parameters:
    - If a function expects arguments but is called without providing values for those arguments, the corresponding parameters inside the function will have the value undefined.
    - ```jsx
        function greet(name) {
          console.log(name);
        }

        greet(); // undefined (name parameter is not provided)
      ```
  - Accessing Nonexistent Object Properties:
    - When you attempt to access a property that does not exist in an object, the result is undefined.
    - ```jsx
        let person = {};
        console.log(person.age); // undefined (age property does not exist)
      ```
  - Explicit Assignment:
    - You can explicitly assign the value undefined to a variable or property.
    - ```jsx
        let emptyValue = undefined;
        let person = { name: "Alice" };
        person.age = undefined;
      ```
  - typeof `undefined`:
    - The typeof operator, when applied to undefined, returns the string "undefined". This can be used to check the type of a variable or value.
    - ```jsx
        typeof undefined; // "undefined"
      ```
  - Comparison with `null`:
    - While undefined and null both represent the absence of a value, they are not the same. undefined typically indicates an uninitialized variable or missing property, while null is often used to signify a deliberate absence of value.
    - ```jsx
        let x;
        let y = null;

        console.log(x); // undefined
        console.log(y); // null
      ```
  - Avoiding Errors:
    - When working with potentially undefined values, it's a good practice to check if a value is undefined before attempting to access its properties or methods to prevent runtime errors.
    - ```jsx
        let data = fetchData();

        if (data !== undefined) {
          // It's safe to access 'data' properties here.
          console.log(data.value);
        }
      ```





## Conditionals
- Truthy and Falsy
  - **Truthy Values:**
    - **Non-Empty Strings:**
      - Any non-empty string is considered truthy.
      - ```jsx
          if ("Hello") {
            // This block will execute because "Hello" is truthy.
          }
        
        ```
    - **Numbers (Except 0):**
      - Numeric values (both positive and negative) other than `0` are considered truthy.
    
      - ```jsx
          if (42) {
            // This block will execute because 42 is truthy.
          }
        
        ```
    - **Non-Empty Arrays and Objects:**
      - Non-empty arrays and objects are considered truthy.
    
      - ```jsx
        if ([1, 2, 3]) {
          // This block will execute because the array is truthy.
        }
        
        if ({ name: "Alice" }) {
          // This block will execute because the object is truthy.
        }
        
        ```
    - **The Boolean Value `true`:**
      - The Boolean value `true` is always truthy.
    
      - ```jsx
        if (true) {
          // This block will execute because 'true' is truthy.
        }
        
        ```
    - **Functions:**
      - Functions are considered truthy values, even if they don't return a specific value.
    
      - ```jsx
            function myFunction() {
              // Function body
            }
            
            if (myFunction) {
              // This block will execute because 'myFunction' is truthy.
            }
        
        ```
  - **Falsy Values:**
    - **The Boolean Value `false`:**
      - The Boolean value `false` is always falsy.
      - ```jsx
          if (false) {
            // This block won't execute because 'false' is falsy.
          }
        ```
    - **The Number 0:**
      - The number `0` is considered falsy.
      - ```jsx
          if (0) {
            // This block won't execute because '0' is falsy.
          }
        
        ```
    - **The Empty String `""`:**
      - An empty string `""` is considered falsy.
    
      - ```jsx
        if ("") {
          // This block won't execute because '""' is falsy.
        }
        ```
    - **The Special Value `null`:**`null` 
      - represents the absence of any value or object and is considered falsy.
      - ```jsx
          let myVar = null;
          if (myVar) {
            // This block won't execute because 'myVar' is falsy.
          }
          
        ```
    - **The Special Value `undefined`:**`undefined` 
      - represents a declared variable with no assigned value and is considered falsy.
    
      - ```jsx
          let myVar;
          if (myVar) {
            // This block won't execute because 'myVar' is falsy.
        }
        
        ```
    
    - **The Special Value `NaN`:**`NaN` 
      - represents "Not-a-Number" and is considered falsy.
    
      - ```jsx
          let result = 10 / "apple"; // NaN
          if (result) {
            // This block won't execute because 'result' is falsy.
          }
        ```
    

- if,  if...else and and if-else-if
  - **1. `if` Statement:**
  - The `if` statement is used to execute a block of code if a specified condition evaluates to `true`. If the condition is `false`, the code block is skipped, and the program continues with the next statement.

  - **Syntax:**
    - ```jsx
        if (condition) {
          // Code to execute if the condition is true
        }
      ```

  - **Example:**
    - ```jsx
        let age = 25;
        if (age >= 18) {
          console.log("You are an adult.");
        }
      ```


  - **2. `if...else` Statement:**
    - The `if...else` statement extends the `if` statement by providing an alternative block of code to execute when the condition is `false`. If the condition in the `if` statement is `true`, the code block under `if` is executed; otherwise, the code block under `else` is executed.

    - **Syntax:**
      - ```jsx
        if (condition) {
          // Code to execute if the condition is true
        } else {
          // Code to execute if the condition is false
        }
        ```
      - **Example:**
      - ```jsx
            let hour = 14;

            if (hour < 12) {
              console.log("Good morning!");
            } else {
              console.log("Good afternoon!");
            }
        ```

  - **3. `if...else if...else` Statement:**
    - The `if...else if...else` statement allows you to test multiple conditions sequentially until one of them evaluates to `true`. The code block associated with the first `true` condition is executed, and the rest of the conditions are skipped.

    - **Syntax:**
    - ```jsx
        if (condition1) {
          // Code to execute if condition1 is true
        } else if (condition2) {
          // Code to execute if condition2 is true
        } else {
          // Code to execute if none of the conditions are true
        }
      ```
    - **Example:**
    - ```jsx
        let score = 85;

        if (score >= 90) {
          console.log("A");
        } else if (score >= 80) {
          console.log("B");
        } else if (score >= 70) {
          console.log("C");
        } else {
          console.log("D");
        }

      ```

- Ternary Operator
  - The ternary operator, also known as the conditional operator, is a compact way to write conditional expressions in JavaScript. It provides a concise alternative to the traditional `if...else` statement for evaluating conditions and returning values based on whether the condition is true or false. The ternary operator has the following syntax:

  - ```jsx
      condition ? expression_if_true : expression_if_false;
    ```

  - **Example 1: Basic Usage**
    - ```jsx
          let age = 20;
          let message = age >= 18 ? "You are an adult" : "You are not an adult";
          console.log(message);
      ```
  - **Example 2: Using Expressions**
    - ```jsx
        let score = 75;
        let grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "D";
        console.log(grade);
      ```

  - **Example 3: Returning Values**
    - The ternary operator can be used to return values from functions conditionally:

    - ```jsx
        function getDiscount(isMember) {
          return isMember ? 10 : 0;
        }

        let userIsMember = true;
        let discount = getDiscount(userIsMember);
        console.log(discount); // Output: 10
      ```

- Nested if...else
  - ```jsx
      if (condition1) {
        // Code to execute if condition1 is true
        if (condition2) {
          // Code to execute if both condition1 and condition2 are true
        } else {
          // Code to execute if condition1 is true but condition2 is false
        }
      } else {
        // Code to execute if condition1 is false
      }
    ```
  - ```jsx
      let temperature = 25;
      let isRaining = false;

      if (temperature > 30) {
        if (isRaining) {
          console.log("It's hot, but don't forget your umbrella!");
        } else {
          console.log("It's hot, enjoy the weather!");
        }
      } else {
        if (isRaining) {
          console.log("It's not too hot, but don't forget your umbrella!");
        } else {
          console.log("It's a pleasant day!");
        }
      }
    ```

- switch...case
  - ```jsx
      switch (expression) {
        case value1:
          // Code to execute if expression matches value1
          break;
        case value2:
          // Code to execute if expression matches value2
          break;
        // Additional cases can be added as needed
        default:
          // Code to execute if expression doesn't match any case
      }
    ```

  - ```jsx
        let day = "Monday";

        switch (day) {
          case "Monday":
            console.log("It's the start of the workweek.");
            break;
          case "Friday":
            console.log("It's almost the weekend.");
            break;
          default:
            console.log("It's another day.");
        }
    ```



## Loops 
- while loop
  - ```js 
    while (condition) {
      // Code to execute as long as the condition is true
    }
    ```
  - Example 
  - ```js
      let count = 0;

      while (count < 5) {
        console.log("Count: " + count);
        count++;
      }
    ```
- do while loop
  - ```js
    do {
      // Code to execute at least once
    } while (condition);
    
    ```
  - example of a simple do...while loop:
  - ```js 
      let count = 0;

      do {
        console.log("Count: " + count);
        count++;
      } while (count < 5);
    ```

- for loop 
  - ```js
      for (initialization; condition; increment/decrement) {
        // Code to execute in each iteration
      } 
    ```
  - example of a simple for loop:
    - ```js 
        for (let i = 0; i < 5; i++) {
          console.log("Iteration " + i);
        }
      ```

  - Iterating Over Arrays:
    - ```js 
        const fruits = ["apple", "banana", "cherry"];

        for (let i = 0; i < fruits.length; i++) {
          console.log(fruits[i]);
        }
      ```
  - Counting Down: 
    - ```js
        for (let i = 5; i > 0; i--) {
          console.log(i);
        } 
      ```
  - Nested Loops
    - ```js
        for (let i = 0; i < 3; i++) {
          for (let j = 0; j < 2; j++) {
            console.log(i, j);
          }
        }
        
      ```
  - break and continue
    - break Statement:
      - ```js
          for (let i = 0; i < 5; i++) {
            if (i === 3) {
              break;
            }
            console.log(i);
          } 
        ```
    - continue Statement:
      - ```js
          for (let i = 0; i < 5; i++) {
            if (i === 2) {
              continue;
            }
            console.log(i);
          }
 
        ```
## Loops 
- Declaring Arrays:
  - You can create an array in JavaScript using square brackets []. You can declare an empty array or initialize it with values.
  - ```js 
      // Empty array
      let emptyArray = [];

      // Array with values
      let numbers = [1, 2, 3, 4, 5];
      let fruits = ["apple", "banana", "cherry"];
    ```
- Accessing Elements:
  - Array elements are accessed using zero-based indices. You can use square brackets with the index to retrieve or modify elements.
  - ```js 
      let fruits = ["apple", "banana", "cherry"];
      console.log(fruits[0]); // Output: "apple"
      fruits[1] = "orange"; // Modifies the second element to "orange"
    ```
- Array Length:
  - You can find the number of elements in an array using the length property.
  - ```js 
      let numbers = [1, 2, 3, 4, 5];
      console.log(numbers.length); // Output: 5
    ```
- Adding and Removing Elements:
  - Arrays have methods like push, pop, shift, and unshift to add and remove elements.
  - ```js 
      let fruits = ["apple", "banana"];
      fruits.push("cherry"); // Adds "cherry" to the end
      fruits.pop(); // Removes the last element ("cherry")
      fruits.unshift("orange"); // Adds "orange" to the beginning
      fruits.shift(); // Removes the first element ("orange")
    ```
- Iterating Through Arrays:
  - You can use loops like for and for...of to iterate through the elements of an array.
  - ```js 
      let numbers = [1, 2, 3, 4, 5];
      for (let i = 0; i < numbers.length; i++) {
        console.log(numbers[i]);
      }

      for (let number of numbers) {
        console.log(number);
      }
    ```
- Common Array Methods:
  - JavaScript provides various built-in array methods for performing operations like filtering, mapping, and reducing arrays. Some common array methods include map, 
  - ```js 
      filter, reduce, forEach, and find.
      let numbers = [1, 2, 3, 4, 5];
      let doubled = numbers.map((num) => num * 2); // [2, 4, 6, 8, 10]
      let evenNumbers = numbers.filter((num) => num % 2 === 0); // [2, 4]
    ```
- Arrays of Different Types:
  - JavaScript allows you to create arrays that contain elements of different data types.
  - ```js 
      let mixedArray = [1, "apple", true, { name: "John" }];
    ```
- Multidimensional Arrays:
  - You can create arrays of arrays to represent multidimensional data structures like matrices.
  - ```js 
      let matrix = [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
      ];
    ```
- Array Destructuring:
  - JavaScript supports array destructuring, which allows you to assign array elements to variables.
  - ```js 
      let [first, second] = [1, 2];
      console.log(first); // Output: 1
      console.log(second); // Output: 2
    ```
## Objects
- Understanding Objects
  - Let's use a hypothetical Netflix movie object as a reference to understand JavaScript objects:
  - ```js 
      let netflixMovie = {
        title: "Inception",
        year: 2010,
        director: "Christopher Nolan",
        genres: ["Sci-Fi", "Action", "Thriller"],
        duration: 148,
        isAvailable: true,
        play: function() {
          console.log("Now playing: " + this.title);
        },
        pause: function() {
          console.log("Paused: " + this.title);
        }
      };
    ```
  - You can access properties and call methods of an object using dot notation:
  - ```sh 
      console.log(netflixMovie.title); // Output: "Inception"
      console.log(netflixMovie.year); // Output: 2010
      console.log(netflixMovie.genres); // Output: ["Sci-Fi", "Action", "Thriller"]

      netflixMovie.play(); // Output: "Now playing: Inception"
      netflixMovie.pause(); // Output: "Paused: Inception"
    ```

- **Accessing keys**
  - Using `Object.keys()`: 
    - The `Object.keys()` method returns an array of the object's own enumerable property names (keys).
    - ```js
        let netflixMovie = {
          title: "Inception",
          year: 2010,
          director: "Christopher Nolan",
          genres: ["Sci-Fi", "Action", "Thriller"],
          duration: 148,
          isAvailable: true
        };

        let keys = Object.keys(netflixMovie);
        console.log(keys); // Output: ["title", "year", "director", "genres", "duration", "isAvailable"]
      ```
    
  - Using a `for...in` Loop: 
    - You can iterate through the object's keys using a `for...in` loop.
    - ```js
          for (let key in netflixMovie) {
            console.log(key); // Output: "title", "year", "director", "genres", "duration", "isAvailable"
          }
      ```

  - Using `Object.getOwnPropertyNames()`: 
    - The `Object.getOwnPropertyNames()` method returns an array of all property names (both enumerable and non-enumerable) of an object.
    - ```js 
        let keys = Object.getOwnPropertyNames(netflixMovie);
        console.log(keys); // Output: ["title", "year", "director", "genres", "duration", "isAvailable"]
      ```
  - Using `Reflect.ownKeys()`: 
    - The `Reflect.ownKeys()` method returns an array of all property names (including symbols) of an object.
    - ```js 
        let keys = Reflect.ownKeys(netflixMovie);
        console.log(keys); // Output: ["title", "year", "director", "genres", "duration", "isAvailable"]
      ```

- for...in loop
  - The for...in loop in JavaScript is used to iterate over the properties (also called enumerable keys) of an object. It provides an easy way to loop through the keys of an object, making it particularly useful for working with objects and dictionaries. 
  - Here's the basic syntax of the for...in loop:
  - ```js 
      for (let key in object) {
        // Code to execute for each property/key
      }
    ```
  - an example of using a for...in loop to iterate over the properties of an object:
  - ```js 
        let person = {
          firstName: "John",
          lastName: "Doe",
          age: 30
        };

        for (let key in person) {
          console.log(key + ": " + person[key]);
        }
    ```

  - It's important to note a few key considerations when using `for...in` loops:

    - 1. **Enumeration Order:** 
      - The order in which properties are enumerated in a `for...in` loop is not guaranteed to be in any particular order. Different JavaScript engines may iterate over object properties in different orders.
    - 2. **Inherited Properties:** 
      - `for...in` also iterates over inherited properties in addition to the object's own properties. To avoid this, you can use the `hasOwnProperty` method to check if a property is an object's own property.
    
      - ```jsx
          for (let key in object) {
            if (object.hasOwnProperty(key)) {
              // Code to execute for each own property
            }
          }
        
        ```
    
    - 3. **Prototype Chain:** 
      - Be cautious when using `for...in` with objects that are part of a prototype chain (e.g., objects created from constructors or classes). It may iterate over properties defined in the prototype chain as well.

- Properties and Methods
  - Properties:
    - Object Properties: Objects can have named properties that store values. These properties are accessed using dot notation (object.property) or bracket notation (object["property"]).
    - ```js 
        let person = {
          firstName: "John",
          lastName: "Doe",
          age: 30
        };
        console.log(person.firstName); // Output: "John"
      ```
    - Built-in Object Properties: Some objects in JavaScript have built-in properties. For example, strings have a length property, arrays have a length property and forEach method, and functions have a name property.
    - ```js 
        let text = "Hello, world!";
        console.log(text.length); // Output: 13
      ```
  - **Methods:**
    - Object Methods: 
      - Objects can have methods, which are functions associated with the object. These methods can perform actions or calculations related to the object's data.
      - ```js 
          let car = {
            brand: "Toyota",
            model: "Camry",
            start: function() {
              console.log("Engine started.");
            }
          };

          car.start(); // Output: "Engine started."
        ```
    - Built-in Object Methods: 
      - JavaScript provides built-in methods for many objects, such as arrays, strings, and dates. For example, arrays have methods like push, pop, map, and filter, while strings have methods like toUpperCase, toLowerCase, and slice.
      - ```js 
          let numbers = [1, 2, 3, 4, 5];
          numbers.push(6); // Adds 6 to the end of the array
          let uppercaseText = "Hello".toUpperCase(); // Converts "Hello" to "HELLO"
        ```
    - Function Methods: 
      - Functions are objects in JavaScript and can have methods of their own. For example, you can define custom methods on functions or use built-in methods like apply and call to control their execution context.
      - ```js 
          function greet() {
            console.log("Hello, " + this.name + "!");
          }

          greet.name = "John";
          greet(); // Output: "Hello, John!"
        ```
    - Prototype Methods: 
      - In JavaScript, you can add methods to object prototypes, which makes those methods available to all objects of that type. For instance, you can add a custom method to the Array.prototype to extend the functionality of all arrays.
      - ```js 
          Array.prototype.getFirstElement = function() {
            return this[0];
          };

          let numbers = [1, 2, 3];
          console.log(numbers.getFirstElement()); // Output: 1
        ```


## Functions 
- Understanding Functions
  - Defining Functions:
    - You can define functions in JavaScript using the function keyword. Here's a simple example of a function that represents playing a Netflix movie:
    - ```js 
        function playNetflixMovie(movie) {
          console.log("Now playing: " + movie.title);
        }
      ```

  - Calling Functions:
    - To execute a function, you "call" it by using its name followed by parentheses, passing any required arguments (values) inside the parentheses.
    - ```jsx
        let netflixMovie = {
          title: "Inception",
          year: 2010,
          director: "Christopher Nolan",
          genres: ["Sci-Fi", "Action", "Thriller"],
          duration: 148,
          isAvailable: true
        };

        playNetflixMovie(netflixMovie); // Output: "Now playing: Inception"

      ```
    - In this example, we're calling the `playNetflixMovie` function and passing the `netflixMovie` object as an argument.

  - Function Parameters:
    - Functions can accept parameters (inputs) that are used within the function. These parameters act as variables inside the function.
    - ```jsx
      function greet(name) {
        console.log("Hello, " + name + "!");
      }
      greet("John"); // Output: "Hello, John!"
      ```
    - In the `greet` function, `name` is a parameter that accepts a value when the function is called.

  - Return Values:
    - Functions can also return values using the `return` keyword. This allows you to get results from a function.
    - ```jsx
        function add(a, b) {
          return a + b;
        }

        let result = add(3, 5);
        console.log(result); // Output: 8
      ```
    - In the `add` function, the `return a + b;` statement returns the sum of `a` and `b` to the caller.

  - Anonymous Functions:
    - You can define functions without a name, called anonymous functions, which are often used as callbacks or assigned to variables.
    - ```js 
      let multiply = function(a, b) {
        return a * b;
      };

      console.log(multiply(4, 6)); // Output: 24
    ```
  - Arrow Functions (ES6):
    - ES6 introduced arrow functions, which provide a more concise syntax for defining functions.
    - ```js
        let divide = (a, b) => a / b;
        console.log(divide(8, 2)); // Output: 4
      ```
- Declaring and defining function
  - Declaring Functions:
    - To declare a function in JavaScript, you use the function keyword, followed by the function name, a set of parentheses for parameters (if any), and curly braces for the function body. Here's an example declaration of a function that plays a Netflix movie:
    - ```js 
        function playNetflixMovie(movie) {
          // Function body
          console.log("Now playing: " + movie.title);
        }
      ```
  - Defining Functions:
    - Defining a function involves providing the actual code that the function will execute. It's essentially the implementation of the function. Here's how you define the playNetflixMovie function:
    - ```js 
        function playNetflixMovie(movie) {
          console.log("Now playing: " + movie.title);
        }
      ```
  - Calling Functions:
    - To execute (or call) a function, you use its name followed by parentheses. You can pass arguments (values) to the function if it expects parameters.
    - ```js 
        let netflixMovie = {
          title: "Inception",
          year: 2010,
          director: "Christopher Nolan",
          genres: ["Sci-Fi", "Action", "Thriller"],
          duration: 148,
          isAvailable: true
        };

        playNetflixMovie(netflixMovie); // Calling the function with the movie object
      ```
- anonymous functions
  - As a Function Expression:
    - You can define an anonymous function as an expression by assigning it to a variable. This is useful when you need to pass functions as arguments to other functions, such as in the case of callbacks.
    - ```js 
        let add = function(a, b) {
          return a + b;
        };

        let result = add(3, 5); // Calling the anonymous function
        console.log(result); // Output: 8
      ```
  - As Immediately Invoked Function Expressions (IIFE):
    - Anonymous functions can be invoked immediately after they are defined. This is often used to create private scopes and avoid polluting the global namespace.
    - ```js 
        (function() {
          console.log("This is an IIFE.");
        })();
      ```
  - As Function Arguments (Callbacks):
    - Anonymous functions are frequently used as callbacks when passing functions as arguments to other functions, like in asynchronous operations or array methods.
    - ```js 
        let numbers = [1, 2, 3, 4, 5];

        let squared = numbers.map(function(number) {
          return number * number;
        });

        console.log(squared); // Output: [1, 4, 9, 16, 25]
      ```

- methods
  - Defining Methods:
    - Methods are defined within object literals or as properties of a class prototype. Here's an example of defining methods within an object literal:
    - ```js 
      let person = {
        firstName: "John",
        lastName: "Doe",
        fullName: function() {
          return this.firstName + " " + this.lastName;
        }
      };
    ```
  - Calling Methods:
    - To call a method, you use dot notation (object.method()). For example:
    - ```js 
        console.log(person.fullName()); // Output: "John Doe"
      ```
  - The this Keyword:
    - Inside a method, the this keyword refers to the object that the method belongs to. It allows you to access and modify properties of the object.
    - ```js 
        let person = {
          firstName: "John",
          lastName: "Doe",
          greet: function() {
            console.log("Hello, " + this.firstName + " " + this.lastName + "!");
          }
        };

        person.greet(); // Output: "Hello, John Doe!"
      ```
  - Methods in Classes (ES6):
    - In modern JavaScript (ES6 and beyond), classes are often used to define objects with methods. Here's an example of a class with a method:
    - ```js 
        class Car {
          constructor(brand) {
            this.brand = brand;
          }

          start() {
            console.log(this.brand + " is starting.");
          }
        }

        let myCar = new Car("Toyota");
        myCar.start(); // Output: "Toyota is starting."
      ```
  - Built-in Object Methods:
    - JavaScript provides many built-in methods for various objects, such as arrays, strings, and dates. These methods allow you to perform operations on objects of those types.
    - ```js 
        let numbers = [1, 2, 3, 4, 5];
        let sum = numbers.reduce(function(total, num) {
          return total + num;
        }, 0);

        console.log(sum); // Output: 15

      ```
- Higher Order Functions
  - Higher-order functions are a fundamental concept in JavaScript that can greatly enhance your ability to work with data and perform complex operations. In the context of your Netflix-like OTT (Over-The-Top) streaming service project, understanding higher-order functions can help you manage and manipulate large datasets, filter content, and create a more dynamic user experience.

  - **What Are Higher-Order Functions?**

    - A higher-order function is a function that takes one or more functions as arguments, returns a function as its result, or both. These functions allow you to abstract and modularize common patterns of behavior in your code.
  - map: 
    - The map function is used to transform each element in an array into a new array based on a provided function. In your project, this can be used to extract specific data from a list of movies, such as their titles.
    - ```js 
        const movieData = [
          { title: 'Movie 1', rating: 4.5 },
          { title: 'Movie 2', rating: 3.8 },
          { title: 'Movie 3', rating: 4.2 }
        ];

        const movieTitles = movieData.map(movie => movie.title);
        // Result: ["Movie 1", "Movie 2", "Movie 3"]
      ```
  - filter:
    - The filter function creates a new array containing elements that meet a specified condition. You can use it to filter out movies that meet certain criteria, such as a minimum rating.
    - ```js 
        const highRatedMovies = movieData.filter(movie => movie.rating > 4.0);
        // Result: [{ title: 'Movie 1', rating: 4.5 }, { title: 'Movie 3', rating: 4.2 }]
      ```
  - reduce:
    - The reduce function is used to accumulate values in an array and return a single result. You can employ it to calculate the total rating of all movies in your project.
    - ```js 
        const totalRating = movieData.reduce((accumulator, movie) => accumulator + movie.rating, 0);
      // Result: 12.5
      ```
  - forEach:
    - The forEach function iterates over an array and performs a specified action for each element. You can use it to display a list of movies or execute side effects, such as updating user profiles.
    - ```js 
        movieData.forEach(movie => {
          console.log(`Title: ${movie.title}, Rating: ${movie.rating}`);
        });
      ```
  - Custom Higher-Order Functions:
    - In your project, you may also create custom higher-order functions that encapsulate specific behaviors. For example, you can create a function that accepts a callback to fetch movie data from an API or a function to validate user inputs during registration.
    - ```js 
        function fetchData(url, callback) {
          // Perform an HTTP request and call the callback with the data
        }

        fetchData('<https://api.netflix-clone.com/movies>', movieData => {
          // Process movieData
        });
      ```

## Forms 
- Taking user inputs via forms
  - Creating HTML Forms:
    - ```html
        <form id="search-form">
          <input type="text" id="search-input" placeholder="Search for movies...">
          <button type="submit">Search</button>
        </form>
      ```
  - Accessing Form Elements:
    - ```js
      const searchForm = document.getElementById('search-form');
      const searchInput = document.getElementById('search-input'); 
      ```
  - Handling Form Submission:
    - ```js
        searchForm.addEventListener('submit', (event) => {
        event.preventDefault(); // Prevent the default form submission

        const searchTerm = searchInput.value;

        // Perform a search operation based on the user's input (e.g., fetch movie data)
        searchMovies(searchTerm);
      });
      ```
  - Validating User Inputs:
    - ```js
        function searchMovies(searchTerm) {
          if (searchTerm.trim() === '') {
            alert('Please enter a search term.');
            return;
          }
          // Proceed with the search operation
        }
      ```
  - Resetting Form:
    - ```js
        function searchMovies(searchTerm) {
          if (searchTerm.trim() === '') {
            alert('Please enter a search term.');
            return;
          }

          // Proceed with the search operation

          // Reset the form
          searchForm.reset();
          searchInput.value = '';
        }
      ```
  - Handling Other Types of Forms:
  - Accessibility Considerations:

- Client side form validation using Js
  - HTML Forms:
    - ```html
      <form id="registration-form">
        <input type="text" id="username" placeholder="Username" required>
        <input type="password" id="password" placeholder="Password" required>
        <input type="password" id="confirm-password" placeholder="Confirm Password" required>
        <button type="submit">Register</button>
      </form> 
      ```
  - JavaScript Validation:
    - ```js
        const registrationForm = document.getElementById('registration-form');
        registrationForm.addEventListener('submit', function (event) {
          event.preventDefault(); // Prevent the default form submission

          const username = document.getElementById('username').value;
          const password = document.getElementById('password').value;
          const confirmPassword = document.getElementById('confirm-password').value;

          // Perform validation checks
          if (username === '') {
            alert('Please enter a username.');
          } else if (password === '') {
            alert('Please enter a password.');
          } else if (password !== confirmPassword) {
            alert('Passwords do not match.');
          } else {
            // Form is valid, submit it or perform further actions
            // You can use AJAX to send the data to the server
            // Or navigate to another page
            alert('Registration successful!');
          }
        });
      ```
  - Styling Validation Feedback:
    - You can improve the user experience by providing visual feedback for validation errors.
    - For example, you can change the border color of input fields or display error messages next to them. CSS classes can be applied dynamically to style elements based on validation results.
  - Accessible Validation:
    - Ensure your validation feedback is accessible to all users. Use semantic HTML and ARIA attributes to convey validation errors to users with disabilities.
    - By implementing client-side form validation, you can create a smoother and more responsive user registration experience in your Netflix OTT project while reducing the likelihood of invalid data reaching the server.

    
## [Ref](https://letsupgrade.notion.site/Notes-JavaScript-Zero-to-Hero-in-5-Days-6e2e4aab47e74c55874af9534f531ef1)

## Basic 
- Javascript Keywords
  - keywords are predefined words in a programming language with a specific use
  - we use them to define the structure and flow of a program.
  - there are keywords like const, var, catch, await, typeOf, static, protected, goTo, let amongst others
- Variable declaration
- Data types in Javascript
- Naming conventions in javascript
- Scope in Javascript
  - Block scope
    - JavaScript had only Global Scope and Function Scope.
    - ES6 introduced two important new JavaScript keywords: `let` and `const`. 
    - These two keywords provide Block Scope in JavaScript. 
    - Variables declared inside a `{ }` block cannot be accessed from outside the block.
    - ```js
      {
        let x = 2;
      }
      // x can NOT be used here 
      ```
  - Function scope
    - JavaScript has function scope: Each function creates a new scope. 
    - Variables defined inside a function are not accessible (visible) from outside the function. 
    - Variables declared with var, let and const are quite similar when declared inside a function.
    - ```js 
      function functionExample() {
        var variableName = "Volvo";   // Function Scope
      };
      ```
  - Global scope
    - Variables declared Globally (outside any function) have Global Scope. 
    - Global variables can be accessed from anywhere in a JavaScript program. 
    - Variables declared with `var`, `let` and `const` are quite similar when declared outside a block.
    - ``` ts
        let x = 2;  // Global scope
      ```
- Javascript blocks
  - Functions
    - A function consists of a set of statements but executes as a single unit. A function can be written like:
    - ```js 
      function sayHello() {
          console.log("Hello world"); 
      };
      // sayHello()
      ```
  - Conditional statements
  - Loops in Javascript
- What is 'this'?
- Data types cont'd
  - Arrays in Javascript
  - Objects in Javascript
- Methods in Javascript
  - String methods
    - String length 

  - Array Methods
- Array and object destructuring in Javascript
  - ```js
      let array = [1, 2, 'kitty', 4, 5, 6, 7];
      let [1, 2, 3, 4, 5, 6, 7] = array;
      console.log(3);

      //console output: kitty 
    ```
- Functions and types of functions
  - Regular function
    - can return anything; always runs to completion after invocation
    - ```js
        function thisIsAFunction() {
          //Enter function code block here
        } 
      ```
  - Generator function
    - returns a Generator object; can be paused and resumed with the yield operator
  - Async function
    - returns a Promise; can be paused and resumed with the await operator.
  - Function return statement in JavaScript
  - Arrow functions
- Javascript Spread operator
  - The JavaScript spread operator `(...)` allows us to quickly copy all or part of an existing array or object into another array or object.
  - ```js
      var firstSixNumbers = [1, 2, 3, 4, 5, 6];
      var firstTenNumbers = [...firstSixNumbers, 7, 8, 9, 10];
      console.log(firstTenNumbers);

      //console output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 
    ```

- References
  - [Link](https://dev.to/dumebii/advanced-javascript-all-you-need-to-know-and-more-4li9)




## JavaScript Callback 
- callback is a function which is to be executed after another function has finished execution
- Any function that is passed as an argument to another function so that it can be executed in that other function is called as a callback function
- This results in callback hell.
- ```js
    // callbacks an callback hell
    let fruits = ["apple", "banana", "orange"];

    const animateAll = (animate) => {
      // below is the callback hell
      setTimeout(() => {
        animate(fruits[0]);
        setTimeout(() => {
          animate(fruits[1]);
          setTimeout(() => {
            animate(fruits[2]);
          }, 1000);
        }, 1000);
      }, 1000);
    };

    const animate = (fruit) => {
      console.log("calling", fruit);
    };

    animateAll(animate);
  ```
- Output : 
- ```sh
    calling apple
    calling banana
    calling orange
  ```

## Import / Export 
- Named exports
  - Named exports are used to export several values from a module.
  - ```js
      // mathConstants.js
      export const pi = 3.14;
      export const exp = 2.7;
      export const alpha = 0.35;

      // -------------

      // myFile.js
      import { pi, exp } from './mathConstants.js'; // Named import -- destructuring-like syntax
      console.log(pi) // 3.14
      console.log(exp) // 2.7

      // -------------

      // mySecondFile.js
      import * as constants from './mathConstants.js'; // Inject all exported values into constants variable
      console.log(constants.pi) // 3.14
      console.log(constants.exp) // 2.7 
    ```
  - While named imports looks like destructuring, 
  - they have a different syntax and are not the same. They don't support default values nor deep destructuring.
  - you can do aliases but the syntax is different from the one used in destructuring:
  - ```js
      import { foo as bar } from 'myFile.js'; 
      // foo is imported and injected into a new bar variable Default import / export 
    ```
  - Concerning the default export, there is only a single default export per module
  - A default export can be a function, a class, an object or anything else. 
  - This value is considered the "main" exported value since it will be the simplest to import.
  - ```js
      // coolNumber.js
      const ultimateNumber = 42;
      export default ultimateNumber;

      // ------------

      // myFile.js
      import number from './coolNumber.js';
      // Default export, independently from its name, is automatically injected into number variable;
      console.log(number) // 42 
    ```


- Function exporting 
  - ```js
      // sum.js
      export default function sum(x, y) {
        return x + y;
      }
      // -------------

      // myFile.js
      import sum from './sum.js';
      const result = sum(1, 2);
      console.log(result) // 3 
    ```

## Spread and Rest Operators
- The spread and rest operators are useful for quickly and easily manipulating collections and arguments. 
- Spread
  - Spread operators allow us to expand an array or object into its individual elements, 
  - while rest operators allow us to condense multiple elements into a single array or object.
  - Spread operators are written using three consecutive `dots (...)`, and they provide us with an easy way to break up an array or an object into its individual elements.

  - ```js
      let array = [1, 2, 3, 4]; 
      let newArray = [...array, 5]; // [1, 2, 3, 4, 5]
    ```
  - The Spread Operator will take our array, expand it into its individual elements (1, 2, 3, 4), and then add the fifth element (5). The result is a new array that is one element longer than the original:
  - ```js
      // ES6/Babel
      const pet = {
        name: 'Oscar'
      }

      const newPet = {
        ...pet, 
        age: 6
      }
      console.log(newPet); 
      ```

      Output: 
      ```sh
      [Object, Object] {
        age: 6,
        name: "Oscar"
      }
    ```
- Rest
  - The rest operator is essentially the opposite of the spread operator. It collects multiple elements into an array. This is useful if you don’t know how many arguments a function may receive, and you want to capture all of them as an array.
  - ```js
      function sum(...nums){
        let total =0; 
        nums.map(num => {
          total += num; 
        });
        return total; 

      } 
      console.log( sum(1, 2, 3, 4, 5) ); 

      // 15
    ```


## Reducer 
## map vs. forEach
- Both map() and forEach() are array methods in JavaScript that are used to iterate over each item in an array. 
- However, they have different functionalities and therefore perform differently in certain scenarios. 
- map()
  - The map() method is used to create a new array by performing a function on each element of the existing array.
  - It returns a new array with the same number of elements as the original array, where each element is the result of the function applied to the corresponding element in the original array.
  - ```js
      const originalArray = [1, 2, 3, 4, 5];
      const doubledArray = originalArray.map((num) => num * 2);
      console.log(doubledArray); // Output: [2, 4, 6, 8, 10] 
    ```
- foreach()
  - The forEach() method is used to execute a function on each element of an array. It does not create a new array like map() does, but instead performs an action on each element of the existing array.
  - ```js
      const originalArray = ['apple', 'banana', 'orange'];
      originalArray.forEach((item) => console.log(item));
      // Output: "apple", "banana", "orange"
    ```
- Performance differences
  - While both map() and forEach() perform similar actions, there are some key differences in their performance.
  - One significant difference is that map() returns a new array, whereas forEach() does not.
  - This means that if you need to create a new array based on the values of an existing array, map() is the better choice. 
  - On the other hand, if you only need to perform an action on each element of an array and do not need to create a new array, forEach() may be a better choice.
  - Another difference is that map() creates a new array with the same length as the original array, whereas forEach() does not modify the length of the original array. 
  - This means that map() can be slower in cases where the resulting array is not needed, as it requires additional memory allocation and copying.
  - In terms of speed, it is generally accepted that forEach() is faster than map() for simple iterations, as forEach() does not need to create a new array. However, this can vary depending on the specific use case and the amount of data being processed.
  - ```js
      const numbers = [1, 2, 3, 4, 5];

      // Using map()
      console.time('map');
      const doubledNumbersMap = numbers.map((num) => num * 2);
      console.timeEnd('map');

      // Using forEach()
      console.time('forEach');
      const doubledNumbersForEach = [];
      numbers.forEach((num){
        doubledNumbersForEach.push(num * 2);
      });
      console.timeEnd('forEach');

      console.log(doubledNumbersMap); // Output: [2, 4, 6, 8, 10]
      console.log(doubledNumbersForEach); // Output: [2, 4, 6, 8, 
    ```
  - When we run this code, we get the following output:
  - ```sh 
      map: 0.012939453125ms
      forEach: 0.007080078125ms
    ``` 

## Javascript 6 types of arrow functions `{} => {}`

- No Parameters 
  - if the function takes no parameters, you are empty parenthesis. 
  - ```js 
    const greet = () => "Hello"; 
    console.log(greet()); 
    ```

- Single Parameters
  - If there's only on parameter, parentheses are optional. 
  - ```js
      const square = x => x * x; 
      console.log(square(4)); 
    ```
- Multiple Parameters 

  - If there's only on parameter, parentheses are optional 
  - ```js 
      const add = (a, b) => a + b; 
      console.log( add(2, 3) ); 
    ```

- Function Body with Multiple Statements
  - If the function body has more than one statement, you need to use curly braces and specify the return keyword (if you want to return something). 
  - ```js
      const greetPerson = name => {
        const greeting = "Hello, " + name + "!"; 
        return greeting;  
      } 
      console.log( greetPerson("Alice"));  
    ```
- Returning Object Literials 
  - When directly returning and object literal, wrap the literal in parentheses to differentiate it from the function block.
  - ```js
      const makePerson = (firstName, lastName) => 
      ({ first: firstName, last: lastName });
      console.log( makePerson("John", "Doe") );

      // Outputs: { first: 'John', last: 'Doe'}
    ```

- Higher Order Functions and Callbacks 
  - Arraow functions are particularly popular when used as short callbacks. 
  - ```js 
    const numbers = [1,2,3,4]; 
    const doubled = numbers.map(num => num * 2); 
    console.log(doubled); 

    //Outputs: [2,4,6,8]
  ```


## Virtual DOM vs Shadow DOM


## Async vs. Defer
- __async Impact__: Using async scripts can speed up the page rendering process since the browser doesn't wait for the script to download and execute before moving forward. However, this can lead to potential issues if scripts depend on each other or manipulate the DOM before it's fully parsed.

- __defer Impact__: By utilizing defer, scripts are executed after the HTML parsing is complete. This ensures that scripts don't interfere with the rendering process. It's particularly useful when dependencies exist between scripts or when scripts need to manipulate the DOM.
- ```html 
    <!DOCTYPE html>
    <html>
    <head>
      <title>Async and Defer Example</title>
      <script async src="script1.js"></script>
      <script defer src="script2.js"></script>
    </head>
    <body>
      <h1>Async and Defer Example</h1>
      <p>This is a paragraph.</p>
      <script>
        console.log("Inline script");
      </script>
    </body>
    </html>
  ```
- `<script async src="script1.js"></script>`: This script tag has the async attribute, indicating that the browser should download and execute the script asynchronously. The script file specified by the src attribute will not block the HTML parsing. Once the script finishes downloading, it will pause HTML parsing, execute the script, and resume parsing.

- `<script defer src="script2.js"></script>`: This script tag has the defer attribute, indicating that the script file should be downloaded asynchronously. However, unlike async, the execution of the script is deferred until the HTML parsing is complete. The script2.js file will maintain its order of execution as it appears in the HTML document.

- `<script>console.log("Inline script");</script>`: This is an inline script that doesn't have any attributes. It will be executed synchronously as part of the HTML parsing process.

- Best Practices for Using async and defer:

  - __Prioritize Critical Scripts__: Place essential scripts, such as those required for rendering or core functionality, directly in the HTML without using async or defer attributes. This ensures that critical scripts are loaded and executed synchronously, avoiding any delays.

  - __Use async for Non-Critical Scripts__: For scripts that are not essential to the initial page rendering, but can be loaded and executed independently, utilize the async attribute. This allows the browser to download and execute the scripts asynchronously, reducing potential blocking of HTML parsing.
  Utilize defer for Dependent Scripts: When scripts have dependencies on other scripts or need access to the fully parsed DOM, use the defer attribute. This ensures that dependent scripts are executed in the order specified and have access to the necessary resources.

  - __Minimize Script Size__: Optimize and minify your scripts to reduce their file size. Smaller scripts download faster, improving overall page loading time. Tools like UglifyJS or Terser can help with script minification.

  - __Place Scripts Before Closing Body Tag__: To prevent rendering delays and ensure proper DOM access, place script tags just before the closing `</body>` tag. This allows the browser to render the HTML content before fetching and executing the scripts.




## Exploit Destructuring
- use of destructuring in JavaScript allows you to ‘unpack’ values from arrays or properties from objects and assign them to individual variables.
- ```js
    let student = {
        name: 'John Doe',
        grade: 'A',
        age: 23
    };


    // Traditional Approach
    let name = student.name;
    let grade = student.grade;
    let age = student.age;


    // Using Destructuring
    let { name, grade, age } = student; 
  ```

## Short-circuit evaluation with logical operators (&& and ||)
- can save computing power and clean up your code. It prevents unnecessary operations from being executed.
- ```js
    let name = fetchedName || "Default Name";
  ```
- If fetchedName is `undefined`, `null`, `NaN`, `0`, `false`, or `""`, then "Default Name" will be assigned to name.


## Async/Await
- Since JavaScript operates on a `single thread`, managing asynchronous tasks can get complicated. 
- Though Promises offer one way of managing asynchronous code, the use of `async/await` syntax leads to cleaner and more easily readable code.
- ```js
    async function fetchData() {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        console.log(data);
    }
    fetchData();
  ```
- the await keyword makes JavaScript `pause` until the `Promise settles`, and then `resumes` with the result

## Adopt ES6 Modules
- ES6 Modules help maintain the structure, reusability, and manageability of your code
- ```js
    // lib.js
    export function add(a, b) {
        return a + b;
    }
    // main.js
    import { add } from './lib.js';
    console.log(add(2, 3));  // 5
  ```

## JavaScript Hoisting
- **var**: Hoisted and initialized with undefined
- **let** and **const**: Hoisted but not initialized, causing a ReferenceError if accessed before declaration.
- **Function Declarations**: Fully hoisted, including the function body.
- **Variable Hoisting**
  - Variables declared with var are hoisted to the top of their scope, but their initialization is not hoisted
  - This means that the variable is moved to the top of the scope, but it is initialized with undefined until the line of code where the variable is assigned a value is reached

  - ```js
      console.log(x); // Output: undefined
      var x = 5;
      console.log(x); // Output: 5
    ```
- **Function Hoisting**
  - Function declarations are fully hoisted, meaning that both the function name and its implementation are moved to the top of the scope
  - This allows you to call the function before its declaration in the code.
  - ```js
      hoistedFunction(); // Output: "This function has been hoisted!"

      function hoistedFunction() {
          console.log("This function has been hoisted!");
      } 
    ```
- **Let** and **Const** Hoisting
  - Variables declared with let and const are also hoisted but in a different way
  - They are hoisted to the top of their block scope but are not initialized.
  - This means they are in a "temporal dead zone" (TDZ) from the start of the block until the declaration is encountered in the code
  - Accessing them before their declaration results in a ReferenceError.

  - ```js
      console.log(y); // ReferenceError: Cannot access 'y' before initialization
      let y = 10;
      console.log(y); // Output: 10 
    ```

## The ways to use JavaScript promises
- Asynchronous programming with promises
  - using a `Promise` to handle the results of a network operation
  - Instead of making a network call, we just use a timeout
  - ```js
      function fetchData() {
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            const data = "This is the fetched data!";
            resolve(data); 
          }, 2000);
        });
      }

      const promise = fetchData();

      promise.then((data) => {
        console.log("This will print second:", data);
      });

      console.log("This will print first.");
    ```
  - Oftentimes, you’ll see the `Promise` called and directly handled, like so:
  - ```js 
        fetchData().then((data) => {
          console.log("This will print second:", data);
        });
    ```
  - Now let’s think about errors. In our example, we can simulate an error condition:
  - ```js
      function fetchData() {
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            if (Math.random() < 0.5) {
              reject("An error occurred while fetching data!");
            } else {
              const data = "This is the fetched data!";
              resolve(data);
            }
          }, 2000);
        });
      }
    
    ```
  - In a real-world application, this could happen if the network call failed or the server returned an error. 
  - To handle the possibility of failure when calling `fetchData()`, we use `catch()`
  - ```js
      fetchData().then((data) => {
        console.log("That was a good one:", data);
      }).catch((error) => {
        console.log("That was an error:", error)
      }); 
    ```

- Promise chains in JavaScript
  - One of the beauties of promises is that you can chain them together. 
  - This helps avoid deeply nested callbacks and simplifies nested asynchronous error handling.
  - ```js
      function processData(data) {
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            const processedData = data + " - Processed";
            resolve(processedData);
          }, 1000);
        });
      }

      fetchData()
        .then((data) => {
          console.log("Fetched data:", data);
          return processData(data); 
        })
        .then((processedData) => {
          console.log("Processed data:", processedData);
        })
        .catch((error) => {
          console.error("Error:", error);
        });
    ```
  - If you run this code several times, you’ll notice that when `fetchData()` succeeds, both `then()` methods are called correctly. 
  - When `fetchData()` fails, the whole chain short circuits and the ending `catch()` are called. This is similar to how try/catch blocks work.
- Run no matter what: Promise.finally()
  - Just like try/catch gives you a `finally()`, `Promise.finally()` will run no matter what happens in the promise chain
  - ```js 
      fetchData()
        .then((data) => {
          console.log("Fetched data:", data);
          return processData(data); 
        })
        .then((processedData) => {
          console.log("Processed data:", processedData);
        })
        .catch((error) => {
          console.error("Error:", error);
        })
        .finally(() => {
          console.log("Cleaning up.");
        })
    ```
  - The `finally()` is useful when you need to do something no matter what happens, like close a connection.

- Fail fast: Promise.all()
  - Now let’s consider a situation where we need to make multiple calls simultaneously.
  - Let’s say we need to make two network requests and we need the results of both. 
  - If either one fails, we want to fail the whole operation. 
  - Our chaining approach above could work, but it's not ideal because it requires that one request finishes before the next begins. 
  - Instead, we can use `Promise.all()`
  - ```js 
      Promise.all([fetchData(), fetchOtherData()])
        .then((data) => { // data is an array
          console.log("Fetched all data:", data);
        })
        .catch((error) => {
          console.error("An error occurred with Promise.all:", error);
        });
    ```
  - Because JavaScript is `single-threaded`, these operations are not truly concurrent but they are much closer.
  - In particular, the JavaScript engine can initiate one request and then start the other while it is still in flight. 
  - This approach gets us as close to parallel execution as we can get with JavaScript.
  - If any one of the promises passed to `Promise.all()` fails, it’ll stop the whole execution and go to the provided `catch()`. 
  - In that way, `Promise.all()` is “fail fast." 
  - You can also use `finally()` with `Promise.all()`, and it will behave as expected, running no matter how the set of promises pans out.
  - In the `then()` method, you'll receive an array, with each element corresponding to the promise passed in, like so:
  - ```js
      Promise.all([fetchData(), fetchData2()])
        .then((data) => {
          console.log("FetchData() = " + data[0] + " fetchMoreData() = " + data[1] );
        })
    ```
- Let the fastest one win: Promise.race()
  - Sometimes you have several asynchronous tasks but you only need the first one to succeed. 
  - This could happen when you have two services that are redundant and you want to use the fastest one.
  - Let’s say `fetchData()` and `fetchSameData()` are two ways to request the same information, and they both return promises. Here’s how we use `race()` to manage them:
  - ```js
      Promise.race([fetchData(), fetchSameData()])
      .then((data) => {
        console.log("First data received:", data);
      }); 
    ```
  - In this case, the `then()` callback will receive only one value for data—the return value of the winning (fastest) `Promise`.
  - Errors are slightly nuanced with `race()`. 
  - If the rejected `Promise` is the first to happen, then the whole race ends and `catch()` is called. 
  - If the rejected promise happens after another promise has been resolved, the error is ignored.
- All or none: Promise.allSettled()
  - If you want to wait for a collection of async operations to all complete, whether they fail or succeed, you can use `allSettled()`. For example:
  - ```js
      Promise.allSettled([fetchData(), fetchMoreData()]).then((results) =>
        results.forEach((result) => console.log(result.status)),
      ); 
    ```
  - The `results` argument passed into the `then()` handler will hold an array describing the outcomes of the operations, something like:
  - ```sh
    [0: {status: 'fulfilled', value: "This is the fetched data!"},
     1: {status: 'rejected', reason: undefined}]
 
    ```

  - So you get a status field that is either `fulfilled` or `rejected`. 
  - If it is fulfilled (resolved), then the value will hold the argument called by `resolve()`. 
  - Rejected promises will populate the `reason` field with the error cause, assuming one was provided.
- Promise.withResolvers()
  - Since March 2024, Promise.withResolvers() has been supported across the latest devices and browsers.
  - This feature introduces a static method that returns an object containing a new Promise and two functions to either resolve or reject it
  - ```js
      const { promise, resolve, reject } = Promise.withResolvers()
 
    ```
  - This method provides an alternative to the traditional new Promise() constructor.
  - Example
  - ```js
      // First, define the helper function to create a promise with resolvers
      function withResolvers() {
        let resolve, reject;
        const promise = new Promise((res, rej) => {
          resolve = res;
          reject = rej;
        });
        return { promise, resolve, reject };
      }

      // Usage example
      const { promise, resolve, reject } = withResolvers();

      // This will log "Waiting for promise resolution"
      console.log("Waiting for promise resolution");

      // Resolve the promise after 2 seconds
      setTimeout(() => {
        resolve("Promise resolved!");
      }, 2000);

      // Handle the resolution of the promise
      promise.then((message) => {
        console.log(message); // Logs "Promise resolved!" after 2 seconds
      });
      
    ```


## Very useful functions 
- Shuffle the array and return an array
  - can shuffle the array using the random method of the math module
  - ```js
      const shuffle = array => array.sort(() => 0.5-Math.random());
      //output
      shuffle([1,5,2,45])  
      [5,2,1,25]
    ```
- Generate a random string
  - Sometimes there may be a situation where you need to generate random strings
  - ```js
      const randomstr = Math.random().toString(36).substring(7)
    ```

- Detecting dark mode
  - use this snippet of code to check whether the dark mode is on or off
  - ```js
      const isDark = window.matchMedia && window.matchMedia(`(prefers-color-scheme:dark)`).match
    ``` 

- Remove duplicates from an array
  - Removing duplicate elements is one of the common things that we do in an array
  - ```js
      const num = [1,2,2,2,5,66,666,55,5]
      const name = ["adarsh","gupta","adarsh","raj","ratesh","raj"]
      const uniquenum = [... new Set(num)]
      // [1,2,5,66,666,55]

      const uniquenames = [... new Set(name)
      // ["adarsh","gupta","raj","ratesh"]
    ```
- Reverse a string
  - Reverse a string has never been such easy, firstly we convert it into an array
  - ```js
      const rev = (str) => str.split("").reverse().join("")
    ```

- Check if an array is not empty
  - Checking if an array is empty or not using the isArray method and confirming it by checking the length of Object.keys(arr) by passing the array
  - ```js
      const isArrayNotEmpty = (arr) => Array.isArray(arr) && 
      Object.keys(arr).length > 0; // Examples
      isArrayNotEmpty([]); // false
      isArrayNotEmpty([1, 2, 3]); // true  
    ```

- Swapping two variables
  - The below code is one of the simpler ways ==to swap two variables== without using a third variable and with just one line of code
  - ```js
      [var1, var2] = [var2, var1];
    ```

- Get Value of a brower Cookie
  - Retrieve the value of a cookie by accessing with document.cookie
  - ```js
      const cookie = name => `; ${document.cookie}`.split(`; ${name}=`).pop().split(';').shift();

      cookie('_ga');
      // Result: "GA1.2.1929736587.1601974046"
    ```
- Convert RGB to Hex
  - ```js
      const rgbToHex = (r, g, b) =>
        "#" + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);

      rgbToHex(0, 51, 255); 
      // Result: #0033ff
    ```
- Copy to Clipboard
  - Easily copy any text to clipboard using navigator.clipboard.writeText
  - ```js
      const copyToClipboard = (text) => navigator.clipboard.writeText(text);

      copyToClipboard("Hello World");
    ```
- Check if Date is Valid
  - Use the following snippet to check if a given date is valid or not.
  - ```js
      const isDateValid = (...val) => !Number.isNaN(new Date(...val).valueOf());

      isDateValid("December 17, 1995 03:24:00");
      // Result: true
    ```

- Find the day of year
  - Find which is the day by a given date.
  - ```js
      const dayOfYear = (date) =>
        Math.floor((date - new Date(date.getFullYear(), 0, 0)) / 1000 / 60 / 60 / 24);

      dayOfYear(new Date());
      // Result: 272
    ```


- Capitalise a String
  - Javascript doesn't have an inbuilt capitalise function, so we can use the following code for the purpose.
  - ```js
      const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)

      capitalize("follow for more")
      // Result: Follow for more
  ```


- Find the number of days between two days
  - Find the days between 2 given days using the following snippet.
  - ```js
      const dayDif = (date1, date2) => Math.ceil(Math.abs(date1.getTime() - date2.getTime()) / 86400000)

      dayDif(new Date("2020-10-21"), new Date("2021-10-22"))
      // Result: 366
  ```

- Clear All Cookies
  - You can easily clear all cookies stored in a web page by accessing the cookie using document.cookie and clearing it.
  - ```js
    const clearCookies = document.cookie.split(';').forEach(cookie => document.cookie = cookie.replace(/^ +/, '').replace(/=.*/, `=;expires=${new Date(0).toUTCString()};path=/`));
    ```

- Generate Random Hex
  - You can generate random hex colors with Math.random and padEnd properties.
  - ```js
      const randomHex = () => `#${Math.floor(Math.random() * 0xffffff).toString(16).padEnd(6, "0")}`;

      console.log(randomHex());
      // Result: #92b008
  ```

- Remove Duplicated from Array
  - You can easily remove duplicates with Set in JavaScript. Its a life saver.
  - ```js
    const removeDuplicates = (arr) => [...new Set(arr)];

    console.log(removeDuplicates([1, 2, 3, 3, 4, 4, 5, 5, 6]));
    // Result: [ 1, 2, 3, 4, 5, 6 ]
    ```


- Get Query Params from URL
  - You can easily retrieve query params from a url either by passing window.location or the raw URL goole. com?search=easy&page=3
  - ```js
    const getParameters = (URL) => {
      URL = JSON.parse('{"' + decodeURI(URL.split("?")[1]).replace(/"/g, '\\"').replace(/&/g, '","').replace(/=/g, '":"') +'"}');
      return JSON.stringify(URL);
    };

    getParameters(window.location)
    // Result: { search : "easy", page : 3 }
    ```

- Log Time from Date
  - We can log time, in the format hour::minutes::seconds from a given date.
  - ```js
      const timeFromDate = date => date.toTimeString().slice(0, 8);

      console.log(timeFromDate(new Date(2021, 0, 10, 17, 30, 0))); 
      // Result: "17:30:00"
    ```



- Check if a number is even or odd
  - ```js
      const isEven = num => num % 2 === 0;

      console.log(isEven(2)); 
      // Result: True
    ```


- Find Average of Numbers
  - Find the average between multiple numbers using reduce method.
  - ```js
      const average = (...args) => args.reduce((a, b) => a + b) / args.length;

      average(1, 2, 3, 4);
      // Result: 2.5
    ```



- Scroll to Top
  - You can use window.scrollTo(0, 0) method to automatic scroll to top. Set both x and y as 0.
  - ```js
      const goToTop = () => window.scrollTo(0, 0);

      goToTop();
    ```

- Reverse a string
  - You can easily reverse a string using split, reverse and join methods.
  - ```js
      const reverse = str => str.split('').reverse().join('');

      reverse('hello world');     
      // Result: 'dlrow olleh'
    ```


- Check if array is empty
  - Simple one liner to check if an array is empty, will return true or false.
  - ```js
      const isNotEmpty = arr => Array.isArray(arr) && arr.length > 0;

      isNotEmpty([1, 2, 3]);
      // Result: true
    ```


- Get Selected Text
  - Get the text the user has select using inbuilt getSelection property.
  - ```js
      const getSelectedText = () => window.getSelection().toString();

      getSelectedText();
    ```
    
- Shuffle an Array
  - Shuffling an array is super easy with sort and random methods.
  - ```js
      const shuffleArray = (arr) => arr.sort(() => 0.5 - Math.random());

      console.log(shuffleArray([1, 2, 3, 4]));
      // Result: [ 1, 4, 3, 2 ]
    ```
- Detect Dark Mode
  - Check if a user's device is in dark mode with the following code.
  - ```js
      const isDarkMode = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches

      console.log(isDarkMode) // Result: True or False
    ```

- Reverse a String
  - ```js
      const reversedString = str => str.split('').reverse().join('');
      reversedString("Hello World"); // dlroW olleH
    ```


- Title Case a String
  - ```js
      const titleCase = sentence => sentence.replace(/\b\w/g, char => char.toUpperCase());
      titleCase("hello world"); // Hello World
    ```

- Swap Values Between Variables
  - ```js
      [a, b] = [b, a];
    ```


- Convert a Number to a Boolean
  - ```js
      const isTruthy = num => !!num;
      isTruthy(0) // False
    ```
- Get Unique Values from an Array
  - ```js
      const uniqueArray = arr => [...new Set(arr)];
      uniqueArray([5,5,2,2,2,4,2]) // [ 5, 2, 4 ]
    ```

- Truncate a String
  - ```js
      const truncateString = (str, maxLength) => (str.length > maxLength) ? `${str.slice(0, maxLength)}...` : str;
      truncateString("Hello World", 8); // Hello Wo...
    ```

- Deep Clone an Object
  - ```js
      const deepClone = obj => JSON.parse(JSON.stringify(obj));

      const obj1 = { name: "John", age: 40};
      const obj2 = deepClone(obj1);
      obj2.age = 20;
      console.log(obj1.age); // 40

      //This method works for most objects, but it has some limitations. Objects with circular references or functions cannot be converted to JSON, so this method will not work for those types of objects.
    ```

- Find the Last Occurrence in an Array
  - ```js
      const lastIndexOf = (arr, item) => arr.lastIndexOf(item);
      lastIndexOf([5, 5, 4 , 2 , 3 , 4], 5) // 1
      ```
    ## Merge Arrays
    - ```js
      const mergeArrays = (...arrays) => [].concat(...arrays);
      mergeArrays([5, 5, 4], [2 , 3 , 4]) // [5, 5, 4, 2, 3, 4]
    ```


- Find Longest Word in a Sentence
  - ```js
      const longestWord = sentence => sentence.split(' ').reduce((longest, word) => word.length > longest.length ? word : longest, '');
      longestWord("The quick brown fox jumped over the lazy dog") // jumped
    ```


- Generate a Range of Numbers
  - ```js
      const range = (start, end) => [...Array(end - start + 1)].map((_, i) => i + start);
      range(5, 15); // [5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
    ```


- Check if Object is Empty
  - ```js
      const isEmptyObject = obj => Object.keys(obj).length === 0;
      isEmptyObject({}) // true
      isEmptyObject({ name: 'John' }) // false
    ```


- Calculate Average of Numbers
  - ```js
      const average = arr => arr.reduce((acc, num) => acc + num, 0) / arr.length;
      average([1, 2, 3, 4, 5, 6, 7, 8, 9]) // 5
    ```


- Convert Object to Query Parameters
  - ```js
      const objectToQueryParams = obj => Object.entries(obj).map(([key, val]) => `${encodeURIComponent(key)}=${encodeURIComponent(val)}`).join('&');
      objectToQueryParams({ page: 2, limit: 10 }) // page=2&limit=10
    ```


- Calculate Factorial of a Number
  - ```js
      const factorial = num => num <= 1 ? 1 : num * factorial(num - 1);
      factorial(4) // 24
    ```


- Count Vowels in a String
  - ```js
      const countVowels = str => (str.match(/[aeiou]/gi) || []).length;
      countVowels('The quick brown fox jumps over the lazy dog') // 11
    ```

- Check for a Valid Email
  - ```js
      const isValidEmail = email => /^[\w-]+(\.[\w-]+)*@([\w-]+\.)+[a-zA-Z]{2,7}$/.test(email);
      isValidEmail("example@email.com") // true
      isValidEmail("example") // false
    ```

- Remove Whitespace from a String
  - ```js
      const removeWhitespace = str => str.replace(/\s/g, '');
      removeWhitespace("H el l o") // Hello
    ```

- Check for Leap Year
  - ```js
      const isLeapYear = year => (year % 4 === 0 && year % 100 !== 0) || (year % 400 === 0);
      isLeapYear(2023) // false
      isLeapYear(2004) // true
    ```

- Generate a random string of specified length
  - ```js
      const generateRandomString = length => [...Array(length)].map(() => Math.random().toString(36)[2]).join('')
      generateRandomString(8) // 4hq4zm7y
    ```

- Copy content to the clipboard
  - ```js
      const copyToClipboard = (content) => navigator.clipboard.writeText(content)
      copyToClipboard("Hello World")
    ```

- Get Current Time in HH:MM:SS format
  - ```js
      const currentTime = () => new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false })
      currentTime() // 19:52:21
    ```

- Check if a number is even or odd
  - ```js
      const isEven = num => num % 2 === 0
      isEven(1) // false
      isEven(2) // true
    ```

- Detect if it is dark mode
  - ```js
      const isDarkMode = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches
      console.log(isDarkMode) // false
    ```


- Scroll to the top of the page
  - ```js
      const goToTop = () => window.scrollTo(0, 0)
      goToTop()
    ```

- Check for a Valid Date
  - ```js
      const isValidDate = date => date instanceof Date && !isNaN(date);
      isValidDate(new Date("This is not date.")) // false
      isValidDate(new Date("08-10-2023")) // true
    ```


- Generate Range of Dates
  - ```js
      const generateDateRange = (startDate, endDate) => Array.from({ length: (endDate - startDate) / (24 * 60 * 60 * 1000) + 1 }, (_, index) => new Date(startDate.getTime() + index * 24 * 60 * 60 * 1000));

      generateDateRange(new Date("2023-09-31"), new Date("2023-10-08")) 
      // [Sun Oct 01 2023 06:30:00 GMT+0630 (Myanmar Time), Mon Oct 02 2023 06:30:00 GMT+0630 (Myanmar Time), Tue Oct 03 2023 06:30:00 GMT+0630 (Myanmar Time), Wed Oct 04 2023 06:30:00 GMT+0630 (Myanmar Time), Thu Oct 05 2023 06:30:00 GMT+0630 (Myanmar Time), Fri Oct 06 2023 06:30:00 GMT+0630 (Myanmar Time), Sat Oct 07 2023 06:30:00 GMT+0630 (Myanmar Time), Sun Oct 08 2023 06:30:00 GMT+0630 (Myanmar Time)]
    ```


- Calculate the interval between two dates
  - ```js
      const dayDiff = (d1, d2) => Math.ceil(Math.abs(d1.getTime() - d2.getTime()) / 86400000)
      dayDiff(new Date("2023-10-08"), new Date("1999-04-31")) // 8926
    ```


- Find the day of the year in which the date falls
  - ```js
      const dayInYear = (d) => Math.floor((d - new Date(d.getFullYear(), 0, 0)) / 1000 / 60 / 60 / 24)
      dayInYear(new Date('2023/10/08'))// 281
    ```


- Check for Array Equality
  - ```js
      const areArraysEqual = (arr1, arr2) => JSON.stringify(arr1) === JSON.stringify(arr2);
      areArraysEqual([1, 2, 3], [4, 5, 6]) // false
      areArraysEqual([1, 2, 3], [1, 2, 3]) // false
    ```


- Unravel the Mystery of ‘this’
  - One of the more challenging aspects of JavaScript that senior developers need to fully grasp is the this keyword. 
  - The value of this can change based on the context it's used in, which could be inside a method, a regular function, or a constructor function.

  - For example, inside a method, this pertains to the object that owns the method:

  - ```js
      let car = {
          model: 'Toyota',
          getModel: function() {
              return this.model;
          }
      };
      console.log(car.getModel());  // 'Toyota'
      ```
    - But inside a regular function, this refers to the global object (window in a browser):
    - ```js
      function testFunction() {
          console.log(this);
      }
      testFunction();  // Window {...} (or the global object)
    ```



- Finding operation system detail 
  - you could find operating system details using simple JS
  - The window.navigator object contains information about the visitor's browser OS details
  - ```js
      console.log(navigator.platform);
    ```

- Getting the timezone offset from the date
  - can use the getTimezoneOffset method of the date object
  - This method returns the time zone difference, in minutes, from the current locale (host system settings) to UTC
  - ```js
      var offset = new Date().getTimezoneOffset();
      console.log(offset); // -330 
    ```
- To get the status of a checkbox.
  - can apply the checked property on the selected checkbox in the DOM
  - If the value is true it means the checkbox is checked, otherwise it means that it's unchecked
  - ```js
      <input type="checkbox" id="checkboxname" value="Agree" /> Agree the
  conditions<br />

      console.log(document.getElementById(‘checkboxname’).checked); // true or false
    ```
- Adding CSS to console messages
  - you can even apply CSS styles to console messages similar to HTML text on the web page
  - ```js
      console.log(
        "%c The text has a purple color, with large font and white background",
        "color: purple; font-size: x-large; background: white"
      ); 
    ```
- Capture the browser back button
  - You can do it using the beforeunload event which is triggered when the window
  - ```js
       window.addEventListener('beforeunload', () => {
        console.log('Clicked browser back button');
      }); 
    ```
- Grouping and nesting the console output
  - The console.group() can be used to group related log messages and you can use console.groupEnd() to close the group

  - ```js
      console.group("User Details");
      console.log("name: Sudheer Jonna");
      console.log("job: Software Developer");

      // Nested Group
      console.group("Address");
      console.log("Street: Commonwealth");
      console.log("City: Los Angeles");
      console.log("State: California");

      // Close nested group
      console.groupEnd();

      // Close outer group
      console.groupEnd(); 
    ```

- Preventing the page from refreshing using void(0)
  - Void(0) is used to prevent the page from refreshing
  - This will be helpful to eliminate the unwanted effects because it will return the undefined primitive value
  - It's commonly used in HTML documents that use anchor elements.
  - For instance, when you click a link, the browser loads a new page or refreshes the same page. It won't happen.
  - For example, the below link gives the alert without reloading the page.
  - ```js 
      <a href="JavaScript:void(0);" onclick="alert('Well done!')">
        Click Me!
      </a>
    ```
- Redirecting new page.
  - you can redirect the user to a new page by setting the href property of the location object, which is a property of the window object.
  - ```js
      function redirect() {
        window.location.href = "newPage.html";
      }
    ```
- Validation of emails
  - The following snippet validates any email with complete logic
  - ```js
      function validateEmail(email) {
        var re =
          /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return re.test(String(email).toLowerCase());
      } 
    ```
  - If you want an easier one that also accepts Unicode characters. You can use the below one!
  - ```js 
      function validateEmailUnicode(email) {
        var re =
          /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return re.test(String(email).toLowerCase());
      }
    ```

- Getting the current URL
  - You can use window.location.href to both get the current URL and update the URL
  - ```js
      onsole.log("location.href", window.location.href); // Returns full URL 
    ```
  - You can also use document.URL for read-only purposes (cannot be used to navigate to a new URL) but this solution has issues in Firefox.
  - ```js 
      console.log("document.URL", document.URL); // Returns full URL (Read-only)
    ```

- Detecting a mobile browser using regex
  - can use regex which returns a true or false value depending on whether or not the user is browsing with a mobile
  - ```js
      window.mobilecheck = function () {
        var mobileCheck = false;
        (function (a) {
          if (
            /(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino/i.test(
              a
            ) ||
            /1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(
              a.substr(0, 4)
            )
          )
            mobileCheck = true;
        })(navigator.userAgent || navigator.vendor || window.opera);
        return mobileCheck;
      }; 
    ```
- Detecting a mobile browser without regex expression
  - can detect mobile browsers by simply running through a list of devices and checking if the userAgent matches anything
  - ```js 
      function detectmob() {
        if (
          navigator.userAgent.match(/Android/i) ||
          navigator.userAgent.match(/webOS/i) ||
          navigator.userAgent.match(/iPhone/i) ||
          navigator.userAgent.match(/iPad/i) ||
          navigator.userAgent.match(/iPod/i) ||
          navigator.userAgent.match(/BlackBerry/i) ||
          navigator.userAgent.match(/Windows Phone/i)
        ) {
          return true;
        } else {
          return false;
        }
      }
    ```

- Detecting disabled JavaScript on the page
  - can use the tag to detect whether JavaScript is disabled or not
  - ```js
      <script type="javascript">
          // JS related code goes here
      </script>
      <noscript>
          <a href="next_page.html?noJS=true">JavaScript is disabled on the page. Enable it asap!</a>
      </noscript> 
    ```

- To get metadata of a module
  - can use the import.meta object which is a meta-property exposing context-specific metadata to a JavaScript module
  - It contains information about the current module, such as the module's URL. In browsers, you might get different metadata than NodeJS
  - ```js
      <script type="module" src="welcome-module.js"></script>;
      console.log(import.meta); // { url: "file:///home/user/welcome-module.js" } 
    ```