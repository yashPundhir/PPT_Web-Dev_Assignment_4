# Assignment 4 - JavaScript

---

**Ans1.**
Hoisting is a JavaScript behaviour where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed.

This means that regardless of where variables and functions are declared in the code, they are treated as if they were declared at the top of their scope.

In the case of variable hoisting, only the declaration is moved to the top, not the initialization. The variable is assigned the value undefined until the actual assignment is reached in the code.

**Eg.**

```javascript
console.log(x); // Output: undefined
var x = 10;
```

In the example above, the variable `x` is hoisted, so it exists within the scope. However, at the time of the `console.log` statement, it is declared but not yet assigned a value, resulting in `undefined` being printed.
Function declarations are fully hoisted, meaning that both the declaration and the function's code are moved to the top of the scope. As a result, functions can be called before they are declared in the code.

**For example:**

```javascript
hoist(); // Output: "Hello, world!"
function hoist() {
	console.log("Hello, world!");
}
```

In this example, the function hoist is hoisted, allowing it to be called before its actual declaration.

---

**Ans2.** The Temporal Dead Zone (TDZ) is a concept in JavaScript that refers to a specific behavior related to variables declared with the let and const keywords. It is a phase during the code execution where variables exist but are not yet accessible, resulting in a runtime error if you try to access them before their declaration.

When a block scope variable (declared with let or const) is created, it is moved to the top of its scope by the JavaScript engine during a process called hoisting. However, unlike variables declared with var, which are hoisted and initialized with a value of undefined, variables declared with let and const are not accessible until they are explicitly declared in the code.

The TDZ is the period between the start of the block scope and the actual declaration of a variable using let or const. During this phase, any attempt to access or reference the variable will result in a ReferenceError. Once the variable is declared in the code, it becomes accessible and can be used normally.

Here's an example to illustrate the Temporal Dead Zone:

```javascript
console.log(x); // Throws ReferenceError: x is not defined
let x = 10;
```

In the example above, when the console.log(x) statement is executed, it throws a ReferenceError because the variable x is in the TDZ. It is not yet declared, even though it exists due to hoisting. Only after the let x = 10; line is encountered does x become accessible.

---

**Ans3.** In JavaScript, both `var` and `let` are used to declare variables, but they have some key differences in terms of scope, hoisting, and redeclaration. Here are the main differences between `var` and `let`:

|               | `var`                                    | `let`                                                           |
| ------------- | ---------------------------------------- | --------------------------------------------------------------- |
| Scope         | Function scope or global                 | Block scope                                                     |
| Hoisting      | Hoisted and initialized with `undefined` | Hoisted but remains in the Temporal Dead Zone until declaration |
| Redeclaration | Allowed                                  | Not allowed                                                     |

Here's an example to illustrate these differences:

```javascript
function example() {
	console.log(x); // Outputs 'undefined' due to hoisting
	var x = 10;
	console.log(x); // Outputs 10

	console.log(y); // Throws ReferenceError: y is not defined
	let y = 20;
	console.log(y); // Outputs 20

	var x = 30; // No error, redeclaration of 'x' is allowed
	let y = 40; // Throws SyntaxError: Identifier 'y' has already been declared
}
```

In the example above, `var x` is hoisted to the top of the `example()` function, allowing it to be accessed before its actual declaration. However, `let y` is in the Temporal Dead Zone until its declaration, leading to a `ReferenceError` when accessed before that point. Additionally, redeclaring `var x` is allowed, but redeclaring `let y` causes a `SyntaxError`.

---

**Ans4.**
ECMAScript 6 (ES6), also known as ECMAScript 2015, introduced several major features and enhancements to the JavaScript language. Some of the key features introduced in ES6 are:

1. let and const: The `let` and `const` keywords were introduced to provide block scoping for variables. `let` allows the declaration of variables with block scope, while `const` is used for declaring constants with block scope.

2. Arrow functions: Arrow functions provide a more concise syntax for writing functions. They have implicit returns and lexically bind the value of `this`, making them useful for shorter function expressions.

3. Classes: ES6 introduced the `class` syntax for defining classes, providing a more structured and familiar way to work with object-oriented programming concepts in JavaScript.

4. Modules: ES6 introduced native support for modules, allowing developers to write modular code by using `import` and `export` statements. This enables better code organization, encapsulation, and dependency management.

5. Template literals: Template literals allow for easier string interpolation and multiline strings by using backticks (\`) as delimiters. They also support expression interpolation and tagged template functionality.

6. Destructuring assignment: Destructuring assignment provides a convenient way to extract values from arrays or objects into individual variables, making it easier to work with complex data structures.

7. Spread syntax: The spread syntax (using `...`) allows for the expansion of arrays, objects, or iterable elements into other arrays, objects, or function calls. It simplifies array concatenation, object cloning, and function argument handling.

8. Default parameters: ES6 introduced the ability to define default parameter values for function parameters. If a parameter is not provided or is explicitly set to `undefined`, the default value is used.

9. Promises: Promises provide a standardized way to handle asynchronous operations in JavaScript. They simplify asynchronous code by representing the eventual completion (or failure) of an operation and allow for better error handling and chaining of operations.

10. Enhanced object literals: ES6 introduced enhancements to object literals, including shorthand property and method syntax, computed property names, and the ability to define methods directly within object literals.

---

**Ans5.**
The main differences between let and const in JavaScript are as follows:

|                | `let`                                 | `const`                                        |
| -------------- | ------------------------------------- | ---------------------------------------------- |
| Assignment     | Can be reassigned                     | Cannot be reassigned                           |
| Initialization | Optional; can be initialized later    | Required; must be initialized upon declaration |
| Scope          | Block scope                           | Block scope                                    |
| Redeclaration  | Not allowed within the same scope     | Not allowed within the same scope              |
| Mutability     | Mutable                               | Immutable                                      |
| Hoisting       | Hoisted to the top of the block scope | Hoisted to the top of the block scope          |

---

**Ans6.** Template literals, introduced in ECMAScript 2015 (ES6), are a way to create strings in JavaScript that allows for easier string interpolation and multiline strings. Template literals are enclosed by backticks (\` \`) instead of single or double quotes.

To use template literals, you can include expressions within `${}` inside the backticks. The expressions are evaluated and interpolated into the resulting string. Here's an example:

```javascript
const name = "Alice";
const age = 25;

const greeting = `Hello, my name is ${name} and I am ${age} years old.`;

console.log(greeting);
// Output: Hello, my name is Alice and I am 25 years old.
```

In the example above, the variables `name` and `age` are interpolated into the string using `${}` within the template literal. The resulting string is stored in the `greeting` variable and printed to the console.

Template literals also support multiline strings without the need for manual line breaks. Here's an example:

```javascript
const message = `
  This is a multiline string
  that spans across multiple lines.
  It makes formatting easier and more readable.
`;

console.log(message);
/*
Output:
  This is a multiline string
  that spans across multiple lines.
  It makes formatting easier and more readable.
*/
```

In the multiline string example, the template literal preserves the line breaks and indentation, resulting in a visually formatted output.

Additionally, you can use tagged template literals to create custom string interpolation behavior. Tagged templates allow you to define a function that processes the template literal and its expressions. The function, known as a tag function, is invoked with the interpolated values and can perform custom logic or formatting on the string.

Here's a simple example of a tagged template literal:

```javascript
function upper(strings, ...values) {
	let result = "";
	for (let i = 0; i < strings.length; i++) {
		result += strings[i];
		if (i < values.length) {
			result += values[i].toUpperCase();
		}
	}
	return result;
}

const name = "Alice";
const age = 25;

const greeting = upper`Hello, my name is ${name} and I am ${age} years old.`;

console.log(greeting);
// Output: Hello, my name is ALICE and I am 25 years old.
```

In the tagged template literal example, the `upper` function processes the template literal. It combines the strings with the uppercase versions of the interpolated expressions.

Template literals provide a convenient and readable way to work with strings in JavaScript, especially when incorporating variables or creating multiline text. They enhance the expressiveness and flexibility of string manipulation in the language.

---

**Ans7.** Both `map()` and `forEach()` are array methods in JavaScript used for iterating over arrays and performing operations on their elements. However, there are some key differences between the two:

1. Return value: The `map()` method returns a new array containing the results of applying a provided function to each element of the original array. It creates a new array by transforming each element of the original array. On the other hand, the `forEach()` method does not return anything. It simply iterates over the array and executes a provided function for each element.

Example using `map()`:

```javascript
const numbers = [1, 2, 3, 4];

const doubled = numbers.map((num) => num * 2);

console.log(doubled); // Output: [2, 4, 6, 8]
```

Example using `forEach()`:

```javascript
const numbers = [1, 2, 3, 4];

numbers.forEach((num) => console.log(num * 2));
// Output:
// 2
// 4
// 6
// 8
```

2. Transformation vs. side effects: Since `map()` returns a new array, it is often used when you want to transform the original array into a new array of the same length. It is a pure function that does not modify the original array. On the other hand, `forEach()` is typically used when you want to perform side effects, such as logging to the console or modifying variables outside the loop. It is not intended for transforming the array.

3. Ability to chain: Because `map()` returns a new array, it can be easily chained with other array methods like `filter()`, `reduce()`, and `sort()`. This allows for more expressive and concise code. However, `forEach()` does not return a value, so it cannot be directly chained with other array methods.

Example using `map()` and chaining:

```javascript
const numbers = [1, 2, 3, 4];

const doubledEvenNumbers = numbers
	.filter((num) => num % 2 === 0)
	.map((num) => num * 2);

console.log(doubledEvenNumbers); // Output: [4, 8]
```

In the example above, we first filter the even numbers and then use `map()` to double them. This is possible due to the ability to chain methods.

---

**Ans8.** In ECMAScript 6 (ES6), you can use destructuring assignment to extract values from objects and arrays into individual variables. Destructuring allows for a more concise and expressive way of working with complex data structures. Here's how you can destructure objects and arrays in ES6:

1. Destructuring Objects:
   To destructure an object, you use curly braces `{}` and provide the variable names that correspond to the object's property names.

   ```javascript
   const person = {
   	name: "Alice",
   	age: 30,
   	city: "New York",
   };

   const { name, age, city } = person;

   console.log(name); // Output: 'Alice'
   console.log(age); // Output: 30
   console.log(city); // Output: 'New York'
   ```

   In the example above, the variables `name`, `age`, and `city` are created and assigned the corresponding values from the `person` object using destructuring.

2. Destructuring Arrays:
   To destructure an array, you use square brackets `[]` and provide variable names in the desired order.

   ```javascript
   const numbers = [1, 2, 3, 4];

   const [a, b, c, d] = numbers;

   console.log(a); // Output: 1
   console.log(b); // Output: 2
   console.log(c); // Output: 3
   console.log(d); // Output: 4
   ```

   In the example above, the variables `a`, `b`, `c`, and `d` are created and assigned the corresponding values from the `numbers` array using destructuring.

3. Destructuring with Default Values:
   You can also assign default values to variables in case the value being destructured is `undefined`.

   ```javascript
   const person = {
   	name: "Alice",
   	age: 30,
   };

   const { name, age, city = "New York" } = person;

   console.log(name); // Output: 'Alice'
   console.log(age); // Output: 30
   console.log(city); // Output: 'New York'
   ```

   In the example above, the `city` variable is assigned a default value of `'New York'` in case the `person` object does not have a `city` property.

Destructuring can also be used in function parameters and nested structures.

---

**Ans9.** In ECMAScript 6 (ES6), you can define default parameter values for function parameters. Default parameter values allow you to specify a default value that will be used if an argument is not provided or is `undefined` when the function is called. Here's how you can define default parameter values in ES6 functions:

```javascript
function greet(name = "Anonymous", message = "Hello") {
	console.log(`${message}, ${name}!`);
}

greet(); // Output: Hello, Anonymous!
greet("Alice"); // Output: Hello, Alice!
greet("Bob", "Hi"); // Output: Hi, Bob!
```

In the example above, the `greet()` function has two parameters: `name` and `message`. The default values `'Anonymous'` and `'Hello'` are assigned to `name` and `message`, respectively. If no argument is passed or if the argument is `undefined` for a parameter, the default value is used.

You can define default values for any or all of the function's parameters. It's important to note that default parameter values are evaluated at the time of function execution, not at the time of function definition. This means that expressions or functions can be used as default values.

```javascript
function multiply(a, b = 2) {
	return a * b;
}

console.log(multiply(5)); // Output: 10
console.log(multiply(5, 3)); // Output: 15
```

In the example above, the `multiply()` function has a default value of `2` for the `b` parameter. When the function is called with only one argument (`multiply(5)`), the default value of `2` is used for `b`, resulting in a multiplication of `5 * 2 = 10`.

---

**Ans10.** The spread operator (`...`) in ECMAScript 6 (ES6) is a versatile feature that allows for the expansion of iterable elements, such as arrays, strings, or objects, into various contexts. The spread operator serves multiple purposes:

1. Array Spreading: The spread operator can be used to "spread" the elements of an array into another array, function arguments, or other iterable contexts.

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5, 6];

console.log(arr2); // Output: [1, 2, 3, 4, 5, 6]
```

In the example above, the spread operator `...arr1` spreads the elements of `arr1` into `arr2`, resulting in a new array `[1, 2, 3, 4, 5, 6]`. This is helpful when you want to concatenate arrays or pass array elements as individual arguments to a function.

2. Function Argument Spreading: The spread operator can be used to spread an array into individual arguments when calling a function.

```javascript
function add(a, b, c) {
	return a + b + c;
}

const numbers = [1, 2, 3];
const sum = add(...numbers);

console.log(sum); // Output: 6
```

In the example above, the spread operator `...numbers` spreads the elements of the `numbers` array into individual arguments when calling the `add()` function. This is equivalent to `add(1, 2, 3)`, resulting in a sum of `6`.

3. Object Spreading: The spread operator can be used to create new objects by merging the properties of existing objects.

```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", country: "USA" };

const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj);
// Output: { name: 'Alice', age: 30, city: 'New York', country: 'USA' }
```

In the example above, the spread operators `{ ...obj1, ...obj2 }` merge the properties of `obj1` and `obj2` into a new object `mergedObj`. This is a concise way to create a new object with the combined properties of existing objects.

4. String Spreading: The spread operator can be used to convert a string into an array of characters.

```javascript
const str = "Hello";
const chars = [...str];

console.log(chars); // Output: ['H', 'e', 'l', 'l', 'o']
```

In the example above, the spread operator `...str` spreads the characters of the string `str` into an array `chars`, resulting in `['H', 'e', 'l', 'l', 'o']`.

---
