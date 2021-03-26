# Comparable Operators

In Java, we can implement the `Comparable` interface to indicate that a type has a defined ordering. We can then use the `compareTo` method to compare instances of the type, leading to a syntax like the following:

```java
if (a.compareTo(b) > 0) {
	// a is greater than b
} else {
	// b is greater than (or equal to) a
}
```

This `compareTo` method returns an `int` value that is positive if `this` is greater than `that`, zero if equal, and negative if less. Since the types of both variables are known at compile-time, it should be safe to provide a shorter syntax for comparison:

```java
if (a > b) {
	// a is greater than b
} else {
	// b is greater than (or equal to) a
}
```

See [Equality and Comparison schemes](../standard-library/equator.md) for more information on `Comparable` and its related concepts.
