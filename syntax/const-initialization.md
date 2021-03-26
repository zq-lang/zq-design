# `const` variables do not need to be immediately initialized

In JavaScript, it is a syntax error to have a `const` declaration without an initializer. Java handles this gracefully by allowing you to assign a `final` variable at most one time in each branch. So the following code would work:

```java
final String result;
if (something) {
	result = "all good!";
} else if (somethingElse) {
	result = "still good!";
} else {
	throw new RuntimeException("this is not good!");
}
System.out.println(result);
```

Note that even though not every branch assigns a value to `result`, all branches that can reach the print statement do have a value in `result`.
