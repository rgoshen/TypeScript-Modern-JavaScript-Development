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
