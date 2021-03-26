# Three equals signs are too many

In JavaScript, there are two tests of equality. Double-equals (`==`) will convert types automagically, whereas triple-equals (`===`) will not. In a type-safe language, there is no need for automatic type conversion, so it should be safe to remove this operator entirely.

In zq, the double-equals operator will mirror JavaScript's triple-equals in general, comparing primitives by value, and comparing objects by reference equality. If value types are implemented (similar to C-style `struct`s), comparison could also be done by value, comparing each field of the value type.
