# TypeScript: Modern JavaScript Development

## Table of Contents

- [TypeScript: Modern JavaScript Development](#typescript-modern-javascript-development)
  - [Table of Contents](#table-of-contents)
  - [Introducing TypeScript](#introducing-typescript)
    - [The TypeScript Architecture](#the-typescript-architecture)
      - [TypeScript Components](#typescript-components)
      - [TypeScript Language Features](#typescript-language-features)

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

#### TypeScript Language Features
