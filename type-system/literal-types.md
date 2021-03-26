# Literal Types

Expanding upon [union types](union-types.md), it often makes sense to define specific values that a variable can be. For example:

```typescript
type HttpMethod = "GET" | "POST" | "PUT" | "DELETE";

const handleRequest = (url: string, method: HttpMethod): void => {
	// ...
};

handleRequest("/some-url", "GET"); // allowed
handleRequest("/some-other-url", "something else!"); // compilation error!
```

This will likely negate the need for explicit `enum` types in zq. Although, we would not have the ability to add instance method to `enum` values (like in Java):

```java
enum HttpMethod {
	GET, POST, PUT, DELETE;

	public void doSomethingCrazy(Request req) {
		switch (this) {
			case GET: // ...
			case POST: // ...
		}
	}
}
```
