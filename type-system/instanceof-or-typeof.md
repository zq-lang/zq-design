# There is no need for `instanceof` and `typeof`

In JavaScript, runtime type checking falls into two categories. The `typeof` operator is lower level and determines what primitive type something is:

```javascript
typeof 123 === "number";
typeof "text" === "string";
typeof { an: "object" } === "object";
typeof ["an", "array"] === "object";
typeof /.*/ === "object";
typeof null === "object";
typeof anUnsetVariable === "undefined";
```

The `instanceof` operator is just for classes:

```javascript
new Person("Jeff") instanceof Person; // true
/.*/ instanceof RegExp; // true
123 instanceof Number; // false
Number(123) instanceof Number; // false
new Number(123) instanceof Number; // true
```

In zq, we should consolidate these runtime checks to a single `instanceof` operator that handles all types.
