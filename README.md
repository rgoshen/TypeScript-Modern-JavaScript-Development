# TypeScript: Modern JavaScript Development

## Table of Contents

- [TypeScript: Modern JavaScript Development](#typescript-modern-javascript-development)
  - [Table of Contents](#table-of-contents)
  - [Introducing TypeScript](#introducing-typescript)
    - [The TypeScript Architecture](#the-typescript-architecture)
      - [TypeScript Components](#typescript-components)
    - [Types](#types)
      - [Optional Static Type Notation](#optional-static-type-notation)
    - [Variables, Basic Types, and Operators](#variables-basic-types-and-operators)
      - [var, let, and const](#var-let-and-const)
      - [Union Types](#union-types)
      - [Type Guards](#type-guards)
      - [Type Aliases](#type-aliases)
      - [Ambient Declarations](#ambient-declarations)
    - [Arithmetic Operators](#arithmetic-operators)
    - [Comparison Operators](#comparison-operators)
    - [Logical Operators](#logical-operators)

## Introducing TypeScript

### The TypeScript Architecture

#### TypeScript Components

Divided into 3 layers and each layer is divided into sublayers or components

Layer 1:

- Visual Studio (VS) Language Service
- VS Shim (shims.ts)

Layer 2:

- Language Service (service.ts)
- Core TypeScript Compiler (core.ts, program.ts, scanner.ts, parser.ts, checker.ts, emitter.ts)

Layer 3:

- Standalone TS Compiler (tsc.ts)

Each of these main layers has a different purpose:

- The language: it features the TS language elements
- The compiler: it performs the parsing, type checking, and transformation of your TS code to JS code
- The language services: it generates information that helps editors and other tools provide better assistance features such as IntelliSense or automated refactoring

### Types

TS added optional static type annotations to JS in order to transform it into a strongly typed language

- optional static type annotations are used to constraints on program entities such as functions, variable, and properties
- optional static type annotations allow compilers and other developer tools offer better verification and assistance (such as IntelliSense) during software development

Strong typing allows the programmer to express his intentions in his code

TS type analysis occurs entirely at compile time and adds no runtime overhead to program execution

#### Optional Static Type Notation

- TS is really good at inferring types, but there are certain cases where it is not able to automatically detect the type of an object or variable

_examples_

```ts
var counter; // unknown (any) type
var counter = 0; // number (inferred)
var counter: number; // number
var counter: number = 0; // number
```

- type of the variable is declared after the variable name
  - based on type theory and helps to reinforce the idea of types being optional

### Variables, Basic Types, and Operators

basic types:

- Boolean
- string
- array
- void types
- and all user defined Enum types

All types in TS are subtypes of a single top type called the **Any type**

| Data Type | Description                                                                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolean   | true or false `var isDone: boolean = false;`                                                                                                                                |
| Number    | floating point values `var height: number = 6;`                                                                                                                             |
| String    | represents text, use either `'` or `"` `var name: string = "bob";`                                                                                                          |
| Array     | types can be written in one of two ways: `var list: number[] = [1, 2, 3];` or `var list: Array<number> = [1, 2, 3];`                                                        |
| Enum      | a way of giving more friendly names to sets of numeric values. by default enums are 0-based `enum Color {Red, Green, Blue};` `var c: Color = Color.Green;`                  |
| Any       | used to represent any JS value, minimal static type checking `var notSure: any = 4;` `notSure = 'maybe a string instead';` `notSure = false; // okay, definitely a boolean` |
| Void      | opposite in some ways to any is `void`, the absence of having any type at all. you will see this as the return type of functions that do not return a value                 |

```ts
function warnUser(): void {
  alert('This is my warning message');
}
```

TS cannot use `null` or `undefined` as types

#### var, let, and const

```ts
var myNum: number = 1;
let isValid: boolean = true;
const apiKey: string = '0E5CE8BD-6341-4CC2-904D-C4A94ACD276E';
```

- variables declared with `var` are scoped to the nearest function block (or global, if outside a function block)
- variables declared with `let` are scoped to the nearest enclosing block (or global if outside any block), which can be smaller that a function block
- the `const` keyword creates a constant that can be global or local to teh block in which it is declared

#### Union Types

TS allows for the declaration of union types

```ts
var path: string[] | string;
path = '/temp/log.xml';
path = ['/temp/log.xml', '/temp/errors.xml'];
path = 1; // Error
```

Union types are used to declare a variable that is able to store a value of two or more types.

#### Type Guards

```ts
var x: any = { /* ... */ };

if(typeof x === 'string') {
  console,.log(x.splice(3, 1)); // Error, 'splice' does not exist on 'string'
}

// x is still any
x.foo(); // OK
```

#### Type Aliases

TS allows us to declare type aliases by using the `type` keyword

```ts
type PrimitiveArray = Array<strin | number | boolean>;
type MyNumber = number;
type NgScope = ng.IScope;
type Callback = () => void;
```

Type aliases are exactly the same type as their original types; they are simply alternative names.

#### Ambient Declarations

- allows you to create a variable in your TS code that will not be translated into JS at compilation time
- designed to facilitate integration with the existing JS code, the **DOM (Document Object Model)** and **BOM (Browser Object Model)**

```ts
customConsole.log('A log entry!'); //error

// Cannot fine name 'customConsole'
```

- sometimes we want to invoke an object that has not been defined, the console or window objects

```ts
console.log('Log Entry!');

var host = window.location.hostname;
```

- when we access DOM or BOM objects, we don't get an error because these objects have already been declared in a special TS file known as **declaration files**

```ts
interface ICustomConsole {
  log(arg: string): void;
}
declare var customConsole: ICustomConsole;

customConsole.log('A log entry!'); // ok
```

- TS includes, by default, a file named `lib.d.ts` that provides interface declarations for the built-in JS library as well as the DOM
- declaration files use the file extension `.d.ts` and are used to increase the TS compatibility with third-party libraries and run-time environments such as Node.js or a web browser

### Arithmetic Operators

| Operator | Description                                                          | Example          |
| -------- | -------------------------------------------------------------------- | ---------------- |
| +        | This adds two operands                                               | A + B = 30       |
| -        | This subtracts the second operand from the first                     | A - B = -10      |
| \*       | This multiplies both the operands                                    | A \* B = 200     |
| /        | This divides the numerator by the denominator                        | B / A = 2        |
| %        | This is the modulus operator and remainder after an integer division | B % A = 0        |
| ++       | This is the increment operator than increases the integer value by 1 | A++ will give 11 |
| --       | This is the decrement operator that decreases the integer value by 1 | A-- will give 9  |

### Comparison Operators

| Operator | Description                                                                                                                                            | Example                                |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------- |
| ==       | This checks whether the values of two operands are equal or not. If yes, then the condition becomes true                                               | (A == B) is false. A == "10" is true.  |
| ===      | This checks whether the value and type of the two operands are equal or not. If yes, then the condition becomes true.                                  | A === B is false. A === "10" is false. |
| !=       | This checks whether the values of two operands are equal or not. If the values are not equal, then the condition becomes true.                         | (A != B) is true                       |
| >        | This checks whether the value of the left operand is greater than the value of the right operand; if yes, then the condition becomes true.             | (A > B) is false                       |
| <        | This checks whether the value of the left operand is less than the value of the right operand; if yes, then the condition becomes true.                | (A < B) is true                        |
| >=       | This checks whether the value of the left operand is greater than or equal to the value of the right operand; if yes, then the condition becomes true. | (A >= B) is false                      |
| <=       | This checks whether the value of the left operand is less than or equal to the value of the right operand; if yes, then the condition becomes true.    | (A <= B) is true                       |

### Logical Operators

| Operator | Description                                                                                                                                                                | Example             |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- |
| &&       | This is called the logical AND operator. If both the operands are nonzero, then the condition becomes true                                                                 | (A && B) is true    |
| \|\|     | This is called the logical OR operator. If any of the two operands are nonzero, then the condition becomes true                                                            | (A \| \| B) is true |
| \!       | This is called the logical NOT operator. It is used to reverse the logical state of its operand. If a condition is true, then the logical NOT operator will make it false. | \!(A && B) is false |
