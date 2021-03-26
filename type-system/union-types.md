# Union Types

In TypeScript, we have the ability to define union types. These represent a variable that can have several different types of values, for example, strings or numbers: `stringOrNumber: string | number`. This syntax is simple and understandable.

Scala attempts to handle this problem with its `Either` type, which works for its functional monadic style. But using the union type syntax, we are able to handle each case in a branch of an `if` statement, which is more friendly to an object-oriented programmer:

```typescript
const someFunction = (stringOrNumber: string | number): void => {
	if (stringOrNumber instanceof string) {
		console.log("Length:", stringOrNumber.length); // this is safe here, because the compiler knows it is a string
	} else {
		console.log("Math'd:", stringOrNumber - 10); // this is safe here, because the compiler knows it is a number
	}
};
```
