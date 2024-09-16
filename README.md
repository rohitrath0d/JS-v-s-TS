#  JS-v-s-TS
#  main differences b/w JS and TS.

#  1. Type Annotations

JavaScript: No type annotations. All variables are dynamically typed.\
TypeScript: Supports explicit type annotations (string, number, boolean, any, null, etc.). This enables strong typing.

```ts
// Example
let age: number = 25;
```


#  2. Static Typing
JavaScript: Dynamically typed, meaning types are checked at runtime.\
TypeScript: Statically typed, meaning types are checked at compile time, helping catch errors earlier in the development process.

```ts
// Example
interface Car {
  make: string;
  model: string;
  year: number;
  start(): void;
}

let myCar: Car = {
  make: "Toyota",
  model: "Camry",
  year: 2021,
  start() {
    console.log("Car started");
  }
};

myCar.start();  // Outputs: Car started

// code explaination:
The Car interface defines the structure with properties (make, model, year) and a method (start()).
The myCar object implements this interface by providing values for these properties and defining the start method.
This example shows how interfaces enforce a consistent structure for objects and their behaviors.
```


#  3. Interfaces and Type Aliases
JavaScript: No native support for interfaces.\
TypeScript: Allows defining interfaces and type aliases to enforce structure in objects, function signatures, or classes.

```ts
// Example:
interface Person {
  name: string;
  age: number;
}
```


#  4. Compile-time Errors
JavaScript: Errors are detected only during execution (runtime).\
TypeScript: Errors are detected during the compilation phase, providing a safer development experience.

```ts
// Example
// Defining an interface
interface User {
  id: number;
  name: string;
  age: number;
}

let user: User = {
  id: 1,
  name: "Alice",
  age: "twenty-five"  // Error: Type 'string' is not assignable to type 'number'
};

// code explaination
Breakdown:
The User interface defines a structure where age must be of type number.
In the user object, we're assigning "twenty-five" (a string) to age, which is expected to be a number.
Compile-time Error: TypeScript will detect this type mismatch at compile time, and it will throw an error: "Type 'string' is not assignable to type 'number'".
This is the advantage of TypeScript's static type checking, as it catches errors early before the code is run. In JavaScript, this type of error would only be discovered during execution (runtime).
```


#  5. Type Inference
JavaScript: No type inference.\
TypeScript: Automatically infers types based on assigned values, though you can still explicitly declare them.

```ts
// Example
let name = 'John';  // inferred as string
```


#  6. Optional and Default Parameters
JavaScript: Supports default parameters but doesn't enforce checks for optional parameters.\
TypeScript: Provides both optional (?) and default parameters in function definitions.

```ts
// Example
function greet(name: string, age?: number): string { ... }
```


#  7. Classes and Object-oriented Programming (OOP)
JavaScript: ES6 introduced classes, but it's still loosely typed.\
ypeScript: Enhances OOP with features like access modifiers (public, private, protected), abstract classes, and interfaces.

```ts
//Example
class Person {
  private name: string;
  constructor(name: string) {
    this.name = name;
  }
}
```


#  8. Enums
JavaScript: No built-in support for enums.\
TypeScript: Supports enums, which allows you to define a set of named constants.

```ts
// Example
enum Direction {
  Up,
  Down,
  Left,
  Right
}
```


#  9. Generics
JavaScript: Doesn't natively support generics.\
TypeScript: Allows for writing reusable, type-safe components and functions using generics.

```ts
// Example
function identity<T>(arg: T): T {
  return arg;
}
```

#  10. Modules
JavaScript: Uses ES6 modules (import/export), but doesn't provide type-safe imports and exports.\
TypeScript: Supports modules with strong type-checking for imports/exports.

// more explaination on modules:
In TypeScript, modules allow you to break down your code into smaller, manageable files, which can be imported and exported between different parts of your application.\
TypeScript enhances JavaScript’s ES6 module system with type safety, ensuring that the data being shared between modules is used correctly.

```ts
# Example of Modules in TypeScript
1. Creating and Exporting a Module
You can define a module by creating a file and using export to expose parts of that file to other parts of your application.

# File: mathUtils.ts
code:
// Exporting functions from this module
export function add(a: number, b: number): number {
  return a + b;
}  
export function subtract(a: number, b: number): number {
  return a - b;
}
export const PI = 3.14159;

In this example:
mathUtils.ts contains two functions (add and subtract) and a constant (PI) that are being exported so they can be used in other files.
```
2. Importing the Module
To use the exported functions and constants in another file, you can use the import statement.

```ts
# File: app.ts
code:
// Importing the functions and constants from mathUtils.ts
import { add, subtract, PI } from './mathUtils';
let result1 = add(5, 3);        // Outputs: 8
let result2 = subtract(9, 4);   // Outputs: 5
console.log(`Value of PI: ${PI}`);  // Outputs: Value of PI: 3.14159

In this example:
We use the import statement to bring in the add, subtract, and PI from the mathUtils.ts module.
We can then use the imported functions and constant in the current file (app.ts).
```
3. Default Export and Import
TypeScript, like JavaScript, also supports default exports, where a single item is exported by default from a module. Here's an example

```ts
# File: defaultUtils.ts
code:
export default function multiply(a: number, b: number): number {
  return a * b;
}
# File: app.ts
// Importing the default exported function
import multiply from './defaultUtils';

let result = multiply(4, 5);    // Outputs: 20

Here:
We use export default to export the multiply function as the default export.
When importing, we can name the function whatever we like (since it is a default export).
```
# General Explaination:
# Why Use Modules?
1. Modularity: Modules help in organizing your code into reusable and manageable pieces, making your codebase more maintainable.\
2.Reusability: Code can be shared across different parts of an application or even across different projects.\
3. Type Safety: TypeScript ensures that you’re importing and using the correct types and functions, reducing errors.\
This modular approach makes it easy to scale projects, like your FinWise application, by separating different functionalities (e.g., handling finance logic, managing user inputs, or displaying data) into distinct modules.


#  11. Decorators
JavaScript: No native support for decorators (still in proposal stage).\
TypeScript: Provides experimental support for decorators, which allows adding metadata or modifying classes, methods, or properties.

```ts
// example:
@sealed
class Greeter { ... }
```

# detailed explaination of decorators:
Decorators are a special feature in TypeScript that allow you to modify or enhance classes, methods, properties, or parameters at design time (before execution). Decorators can be used to add metadata, change behavior, or augment the functionality of the code they are applied to.
They are similar to annotations in other languages like Java or Python, and are mainly used in scenarios such as dependency injection, logging, and validation.

# Why Are Decorators Used?
1. Code Reusability: Decorators allow you to apply common logic (e.g., validation, logging, security checks) across multiple classes, methods, or properties.
2. Separation of Concerns: By moving cross-cutting concerns like logging or security into decorators, you keep the core business logic clean and focused.
3. Enhanced Readability: They make the code more readable by annotating classes or methods with decorators, indicating their purpose directly in the code.

# Types of Decorators:
1. Class Decorators: Applied to a class to modify its behavior or metadata.
2. Method Decorators: Applied to methods to alter their functionality.
3. Property Decorators: Applied to properties to modify how they behave or store values.
4. Parameter Decorators: Applied to method parameters to modify how they are processed.

# How Decorators Are Used?
To use decorators, you must enable the experimental decorator feature by adding "experimentalDecorators": true to your "tsconfig.json."
```
Example of a Class Decorator:
// Class decorator
function sealed(constructor: Function) {
  Object.seal(constructor);
  Object.seal(constructor.prototype);
}
@sealed
class Greeter {
  greeting: string;
  constructor(message: string) {
    this.greeting = message;
  }
  greet() {
    return `Hello, ${this.greeting}`;
  }
}
const greeter = new Greeter("World");
console.log(greeter.greet());  // Outputs: Hello, World

Breakdown:
--> @sealed is a class decorator that "seals" the class. This means no new properties can be added to the class or its prototype after the decorator is applied.
--> The decorator is applied by using the @ symbol, followed by the decorator name (sealed) above the class declaration.
```

# Method Decorator Example:
```
function log(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  
  descriptor.value = function (...args: any[]) {
    console.log(`Method ${propertyKey} called with arguments: ${args.join(", ")}`);
    return originalMethod.apply(this, args);
  };
}

class Calculator {
  @log
  add(a: number, b: number): number {
    return a + b;
  }
}

const calculator = new Calculator();
calculator.add(5, 3);  // Outputs: Method add called with arguments: 5, 3

Breakdown:
--> @log is a method decorator that logs the method's name and arguments every time it is called.
--> It wraps the original add method, adding logging functionality without changing the method's logic.

Decorators are a powerful feature in TypeScript that allow developers to write cleaner, reusable code by abstracting cross-cutting concerns. They are particularly useful in scenarios like logging, validation, and dependency injection, making them a popular choice in frameworks like Angular.
```


#  12. Strict Mode
JavaScript: You can use "use strict"; for stricter rules.\
TypeScript: Strict mode in TypeScript (strict: true in tsconfig.json) enforces rigorous checks across various type rules, ensuring higher code safety.\

Strict Mode in TypeScript
In TypeScript, you enable strict mode by setting "strict": true in your tsconfig.json file. This enables various strict type-checking options, which help catch potential errors during development.

1. Without Strict Mode (JavaScript-like behavior)
```ts
let value;
value = 5;
console.log(value.toFixed(2));  // Outputs: 5.00

value = "hello";
console.log(value.toUpperCase());  // Outputs: HELLO

Here:
Without strict mode, TypeScript allows value to change types from a number to a string.
This is similar to how JavaScript works, where variables can dynamically change types without any errors or warnings.
```
2. With Strict Mode (TypeScript strict behavior)
   --> Enable strict mode in tsconfig.json:
```ts 
{
  "compilerOptions": {
    "strict": true
  }
}
```
  --> Now, TypeScript will enforce stricter rules:
```
let value: number;
value = 5;
console.log(value.toFixed(2));  // Outputs: 5.00

value = "hello";  // Error: Type 'string' is not assignable to type 'number'

```
# Breakdown:
Without strict mode: TypeScript allows the variable value to hold different types (number and string) without errors.\
With strict mode: TypeScript raises an error when you try to assign a string to a variable that has already been declared as a number.

# Why Use Strict Mode in TypeScript?
1. Type Safety: Ensures that variables stick to their assigned types, reducing potential bugs.\
2. Code Robustness: Prevents unintended behavior by enforcing clear type definitions and checks.\
3.  Early Error Detection: Catches potential runtime errors during development, improving code quality and maintainability.\
In strict mode, TypeScript enforces better coding practices, helping you avoid errors that could occur due to type mismatches, such as in dynamically typed JavaScript.


#  13. Type Guards
JavaScript: Doesn't have built-in type guards.\
TypeScript: TypeScript allows for type guards to narrow down types during runtime checks.

```ts
function isString(x: any): x is string {
  return typeof x === "string";
}
```


#  14. Utility Types
JavaScript: No native utility types.\
TypeScript: Offers built-in utility types like Partial, Pick, Omit, Readonly, and more to modify or work with existing types.
```ts
type PartialPerson = Partial<Person>;
```


#  15. Union and Intersection Types
JavaScript: No built-in union or intersection types.
TypeScript: Allows defining types using unions (|) and intersections (&).

```ts
let value: string | number;
```

#  16. Non-null Assertion Operator
JavaScript: Does not have a way to assert a value is non-null.
TypeScript: The non-null assertion operator (!) tells TypeScript that a variable is not null or undefined.
```ts
let element = document.getElementById("myDiv")!;
```


#  17. TypeScript Configuration File
JavaScript: No configuration file needed.
TypeScript: Uses tsconfig.json to configure the TypeScript compiler and project settings.


#  18. Compatibility with JavaScript
JavaScript: Native to browsers and runs without any compilation.
TypeScript: Needs to be compiled (transpiled) to JavaScript, but is backward-compatible with JavaScript. You can use any valid JavaScript in a TypeScript file.




