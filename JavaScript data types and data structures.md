# Null and Undefined
The Null type is inhabited by exactly one value: [`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/null).
The Undefined type is inhabited by exactly one value: [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Conceptually, `undefined` indicates the absence of a _value_, while `null` indicates the absence of an _object_ (which could also make up an excuse for [`typeof null === "object"`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#typeof_null)).

# Boolean
The [`Boolean`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) type represents a logical entity and is inhabited by two values: `true` and `false`.

# Number 
- The [`Number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) type is a [double-precision 64-bit binary format IEEE 754 value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#number_encoding).
	- Positive floating-point numbers between 2^-1074 ([`Number.MIN_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_VALUE)) and 21024 ([`Number.MAX_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_VALUE))
	- Negative floating-point number between -2^-1074 and -2^1024
	-  it can only safely store integers in the range -(2^53 − 1) ([`Number.MIN_SAFE_INTEGER`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_SAFE_INTEGER)) to 2^53 − 1 ([`Number.MAX_SAFE_INTEGER`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER)). Outside this range, JavaScript can no longer safely represent integers; they will instead be represented by a double-precision floating point approximation.

Values outside the range ±(2^-1074 to 2^1024) are automatically converted:

-   Positive values greater than [`Number.MAX_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_VALUE) are converted to `+Infinity`.
-   Positive values smaller than [`Number.MIN_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_VALUE) are converted to `+0`.
-   Negative values smaller than -[`Number.MAX_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_VALUE) are converted to `-Infinity`.
-   Negative values greater than -[`Number.MIN_VALUE`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_VALUE) are converted to `-0`.

```
console.log(42/ +0); //Infinity
console.log(42 / -0); //-Infinity
```
[`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) ("**N**ot **a** **N**umber") is a special kind of number value that's typically encountered when the result of an arithmetic operation cannot be expressed as a number. It is also the only value in JavaScript that is not equal to itself.

# BigInt
The [`BigInt`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) type is a numeric primitive in JavaScript that can represent integers with arbitrary magnitude. With BigInts, you can safely store and operate on large integers even beyond the safe integer limit ([`Number.MAX_SAFE_INTEGER`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER)) for Numbers.

```
const x = BigInt(Number.MAX_SAFE_INTEGER); // 9007199254740991n
X + 1n === x + 2n // false because 9007199254740992n and 9007199254740993n are unequal
```

```
Number.MAX_SAFE_INTEGER + 1 === Number.MAX_SAFE_INTEGER + 2; 
// true because both are 9007199254740992
```

You can use most operators to work with BigInts, including `+`, `*`, `-`, `**`, and `%` — the only forbidden one is [`>>>`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift). A BigInt is not [strictly equal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) to a Number with the same mathematical value, but it is [loosely](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Equality) so.

# String
JavaScript strings are immutable. This means that once a string is created, it is not possible to modify it. String methods create new strings based on the content of the current string:
- A substring of the original using [`substring()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring).
- A concatenation of two strings using the concatenation operator (`+`) or [`concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat).

# Symbol
A [`Symbol`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) is a **unique** and **immutable** primitive value and may be used as the key of an Object property (see below). In some programming languages, Symbols are called "atoms". The purpose of symbols is to create unique property keys that are guaranteed not to clash with keys from other code.

# Objects
>In computer science, an object is a value in memory which is possibly referenced by an [identifier](https://developer.mozilla.org/en-US/docs/Glossary/Identifier). In JavaScript, objects are the only [mutable](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) values. [Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions) are, in fact, also objects with the additional capability of being _callable_.

## Properties
In JavaScript, objects can be seen as a collection of properties. With the [object literal syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#object_literals), a limited set of properties are initialized; then properties can be added and removed. 
	- Object properties are equivalent to key-value pairs. Property keys are either [strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#string_type) or [symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#symbol_type).
	- Property values can be values of any type, including other objects.

There are two types of object properties: The [_data_ property](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#data_property) and the [_accessor_ property](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#accessor_property).

### Data property
`value`

`writable`

`enumerable`

`configurable`

### Accessor property
Associates a key with one of two accessor functions (`get` and `set`) to retrieve or store a value.

# Dates
When representing dates, the best choice is to use the built-in [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) utility in JavaScript.

# Arrays and typed Arrays
[Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) are regular objects for which there is a particular relationship between integer-keyed properties and the `length` property.