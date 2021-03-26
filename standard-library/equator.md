# Equality and Comparison schemes

In Java, the collections library relies heavily on the `Object.equals` method for equality comparison. The `HashMap` class also relies on the `Object.hashCode` method for hashing map keys. These methods should be extracted into interfaces and not present on all types. This also lets us define multiple comparison schemes per type, similar to how in Java we can compare `String`s by their natural case-sensitive order, or by using the built-in `String.CASE_INSENSITIVE_ORDER` comparator.

In zq, we should define several types for these operations: `Equator`, `Comparator`, and `Hasher`. Each of them will have a single abstract method to compare/hash values of a certain type. Additionally, `Comparator` and `Hasher` should extend the `Equator` type, as they naturally need to define a method to equate values of their target type.

```typescript
interface Equator<T> {
	equal: (a: T, b: T) => bool;
}

type Sign = "LESS" | "EQUAL" | "GREATER";

interface Comparator<T> extends Equator<T> {
	compare: (a: T, b: T) => Sign;

	@Override
	equal = (a, b) => this.compare(a, b) == "EQUAL";
}

interface Hasher<T> extends Equator<T> {
	hash: (x: T) => int;
}
```

And each of the above should have an associated interface to define a default scheme:

```typescript
interface Equatable<T> {
	equals: (that: T) => bool;
}

interface Comparable<T> extends Equatable<T> {
	compareTo: (that: T) => Sign;

	@Override
	equals = (that) => this.compareTo(that) == "EQUAL";
}

interface Hashable<T> extends Equatable<T> {
	get hashCode: int;
}
```

Using these types, we will be able to define collections that compare values based on alternative comparison schemes, similar to how `TreeMap` in Java accepts a `Comparator` instance. This behavior is simply expanded to all collection types, and will look something like:

```typescript
const hasher: Hasher<Person> = (person) => person.id;
const people = new HashSet(hasher);
```
