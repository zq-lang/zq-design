# zq-design

This is the repository for design decisions regarding the (currently hypothetical) programming language zq.

Most of my professional career, I've been cultivating opinions about the languages I work in (generally Java, JavaScript, and TypeScript). The idea for the zq language came from my search for the "the perfect programmling language". Please open issues against this repository if you have any opinions to add, or if you disagree with one of my design decisions.

---

## Language Features

### Syntax

- _Unlike JavaScript_: [three equals signs are too many](language-features/syntax/triple-equals.md): `===`/`!==`
- _Unlike JavaScript_: [functions should all be "lambda" style](language-features/syntax/lambdas.md): `() => {}`
- _Unlike Java and JavaScript_: [parameter reassignment should be opt-in, not the default](language-features/syntax/parameter-reassignment.md)
- _Like TypeScript_: [variable type specifiers should be after a colon](language-features/syntax/type-after-colon.md): `name: string`
- _Unlike JavaScript_: [lines of code must end in a semicolon](language-features/syntax/semicolon.md)
- _Like Node.js_: files should be the base unit of code, with exports (not classes)
- _Unlike Node.js_: only named exports should be allowed in a file

### Type System

- _Unlike TypeScript_: **runtime type checks should be comprehensive**
- _Unlike Java_: generics should be known at runtime
- _Unlike JavaScript_: there is no need for `undefined` and `null`
- _Unlike JavaScript_: there is no need for `instanceof` and `typeof`
- _Like TypeScript_: union types should be supported (`string | number`)
- _Like TypeScript_: primitive literals should be supported as types, and may make enum types unnecessary (`type MyEnum = "VALUE1" | "VALUE2"`)
- _Like TypeScript_: anonymous types should be supported (`{ field: string }`)
- _Like TypeScript_: tuple types should be supported (`[number, string]`)
- _Partially-Unlike Java_: type variance should be supported (note: the TypeScript docs [mention](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-6.html) that variance naturally emerges due to its structural type system)
- _Unlike JavaScript_: floating-point should be one of many options for numeric primitives
- _Unlike Java_: fixed-size integer types should have unsigned counterparts (`int`/`uint`, `byte`/`ubyte`, etc.)
- _Unlike Java_: variables should explicitly state whether they allow `null` values (`SomeType | null`)
- _Unlike Java_: comparing comparables with `<`/`>`/`<=`/`>=` should be allowed
- _Like TypeScript_: interfaces should not need to be explicitly implemented; they are just type guards

### Standard Library

- _Unlike JavaScript (and Java)_: arbitrary-precision integers and decimals should be included (as primitives)
- _Unlike JavaScript_: comprehensive date/time library should be built in, with nanosecond precision
- _Partially-Like Java_: collections library should be very extensive, and include arrays as part of the main collection types

### Misc.

- _Like Node.js_: single-threaded languages are easier to grasp and less error-prone
- _Unlike Java_: it would be ideal to compile down to native code; fastest execution should be the goal

---

## Package Manager

- _Unlike Java_: a package manager (or at least central package repository) should be a first-class citizen
- _Unlike npm_: each project should not have its own package repository; it should be centralized on the machine
