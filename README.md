# zq-design

This is the repository for design decisions regarding the (currently hypothetical) programming language zq.

Most of my professional career, I've been cultivating opinions about the languages I work in (generally Java, JavaScript, and TypeScript). The idea for the zq language came from my search for the "the perfect programmling language". Please open issues against this repository if you have any opinions to add, or if you disagree with one of my design decisions.

## Syntax

- ✅ _Unlike JavaScript_: [three equals signs are too many](syntax/triple-equals.md) (`===` and `!==`)
- ❌ _Unlike JavaScript_: [functions should all be "lambda" style](syntax/lambdas.md) (`() => {}`)
- ❌ _Unlike Java and JavaScript_: [parameter reassignment should be opt-in, not the default](syntax/parameter-reassignment.md)
- ❌ _Like TypeScript_: [variable type specifiers should be after a colon](syntax/type-after-colon.md) (`name: string`)
- ❌ _Unlike JavaScript_: [lines of code must end in a semicolon](syntax/semicolon.md)
- ❌ _Like Scala_: [lazy values should have a simple syntax](syntax/lazy-values.md)
- ✅ _Unlike JavaScript_: [`const` variables do not need to be immediately initialized](syntax/const-initialization.md)

## Type System

- ❌ _Unlike TypeScript_: [**the type system should exist at runtime**](type-system/runtime-checks.md) (in addition to compile-time)
- ❌ _Unlike Java_: [generics should be known at runtime](type-system/runtime-generics.md)
- ✅ _Unlike JavaScript_: [there is no need for `undefined` and `null`](type-system/undefined-or-null.md) (get rid of `undefined`)
- ✅ _Unlike JavaScript_: [there is no need for `instanceof` and `typeof`](type-system/instanceof-or-typeof.md) (get rid of `typeof`)
- ❌ _Like TypeScript_: [union types should be supported](type-system/union-types.md) (`string | number`)
- ❌ _Like TypeScript_: [primitive literals should be supported as types, and may make enum types unnecessary](type-system/primitive-literals.md) (`type MyEnum = "VALUE1" | "VALUE2"`)
- ❌ _Like TypeScript_: [anonymous types should be supported](type-system/anonymous-types.md) (`{ field: string }`)
- ❌ _Like TypeScript_: [tuple types should be supported](type-system/tuple-types.md) (`[number, string]`)
- ❌ _Partially-Unlike Java_: [type variance should be supported](type-system/type-variance.md) (note: the TypeScript docs [mention](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-6.html) that variance naturally emerges due to its structural type system)
- ❌ _Unlike JavaScript_: [floating-point should be one of many options for numeric primitives](type-system/floating-point.md)
- ❌ _Unlike Java_: [fixed-size integer types should have unsigned counterparts](type-system/unsigned-integers.md) (`int`/`uint`, `byte`/`ubyte`, etc.)
- ❌ _Unlike Java_: [variables should explicitly state whether they allow `null` values](type-system/nullable-types.md) (`SomeType | null`)
- ✅ _Unlike Java_: [comparing comparables with `<`/`>`/`<=`/`>=` should be allowed](type-system/comparable-operators.md)
- ❌ _Like TypeScript_: [interfaces should not need to be explicitly implemented](type-system/interfaces-as-guards.md) (they are just type guards)
- ❌ _Unlike JavaScript_: [automatic type coercion is not supported](type-system/type-coercion.md) (i.e. `if (notABool)` and `notABool && ...` are not allowed)

## Standard Library

- ❌ _Unlike JavaScript (and Java)_: [arbitrary-precision integers and decimals should be included](standard-library/arbitrary-precision.md) (as primitives)
- ❌ _Unlike JavaScript_: [comprehensive date/time library should be built in, with nanosecond precision](standard-library/date-time.md)
- ❌ _Partially-Like Java_: [collections library should be very extensive](standard-library/collections.md) (and include arrays as part of the main collection types)
- ❌ _Like Java_: [reflection should be available to analyze types at runtime](standard-library/reflection.md)
- ✅ _Unlike Java_: [types should be able to define multiple equality or comparison schemes](standard-library/equator.md)
- ❌ _Like Java and JavaScript_: [anything can be converted to a string](standard-library/to-string.md) (and the default behavior can be overridden with `toString()`)
- ❌ _Like JavaScript (`toJSON`)_: [anything can be converted to a primitive](standard-library/to-primitive.md) (and the default behavior can be overridden with `toPrimitive()`)

## Package Manager

- ❌ _Unlike Java_: [a package manager should be a first-class citizen](package-manager/built-in.md) (or at least central package repository)
- ❌ _Unlike npm_: [each project should not have its own package repository](package-manager/central-repo.md) (it should be centralized on the machine)
- ❌ _Like Node.js_: [files should be the base unit of code, with exports](package-manager/file-based.md) (not classes)
- ❌ _Unlike Node.js_: [only named exports should be allowed in a file](package-manager/named-exports.md)

## Misc.

- ❌ _Like Node.js_: [single-threaded languages are easier to grasp and less error-prone](misc/single-threaded.md)
- ❌ _Unlike Java_: [it would be ideal to compile down to native code](misc/native-code.md) (fastest execution should be the goal)
