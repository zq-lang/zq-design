# There is no need for `undefined` and `null`

In JavaScript, the values `undefined` and `null` are their own types. This arises from variables having the `undefined` value until they are set explicitly, but this should not be necessary when using a strongly typed language.

It is also a lesser-known fact that the global `undefined` value can be reassigned. For example, the following code prints `EEK!`:

```javascript
function badCode(undefined) {
	const assumption = undefined;
	if (assumption) {
		console.log("EEK!");
	} else {
		console.log("I'm fine everything is fine");
	}
}
badCode({ what: "is going on?" });
```
