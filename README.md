# JavaScript Comparisons

## Overview
In addition to performing arithmetic and assigning value to variables, JavaScript has additional operators for comparing values. The value returned by a comparison is **always** `true` or `false`.

## Objectives
1. Compare values with `===` and `!==` to test for equality.
2. Understand the difference between loose and strict equality and why `==` and `!=` should never be used.
3. Test how values relate to one another with `>`, `>=`, `<`, and `<=`.
4. Explain why it's best to only compare numbers with the relational operators.

## Equality operators

### `==`
The **loose equality operator** returns `true` if two values are equal:
```js
42 == 42
// => true
```

However, it will _also_ return `true` if it can perform a type conversion (e.g., changing the string `'42'` into the number `42`) that makes the two values equal:
```js
42 == '42'
// => true

true == 1
// => true

'0' == false
// => true

null == undefined
// => true

' ' == 0
// => true
```

This is confusing and bad! It makes no sense that the string `'0'` is equal to the boolean `false` or that `null` and `undefined` — two **completely different** primitive data types — are equivalent. ***Never use `==` for comparisons***.

### `===`
The **strict equality operator** returns `true` if two values are equal _without performing type conversions_. That is, even if the values on both sides of the operator look similar (e.g., `'42' === 42`), the `===` operator will only return `true` if the data types also match:
```js
42 === 42
// => true

42 === '42'
// => false

true === 1
// => false

'0' === false
// => false

null === undefined
// => false

' ' === 0
// => false
```

This is logical and good! ***Always use `===` for comparisons***.

### `!=`
The **loose inequality operator** is the opposite of `==`. It returns `true` if two values are _not_ equal, performing type conversions as necessary:
```js
9000 != 9001
// => true

9001 != '9001'
// => false

[] != ''
// => false
```

Once again, ***never use `!=` for comparisons***.

### `!==`
The **strict inequality operator** returns `true` if two values are _not_ equal and does not perform type conversions:
```js
9000 !== 9001
// => true

9001 !== '9001'
// => true

[] !== ''
// => true
```

***Always use `!==` for comparisons***.

## Relational operators
The **greater than** (`>`), **greater than or equals** (`>=`), **less than** (`<`), and **less than or equals** (`<=`) operators are pretty self-explanatory:
```js
88 > 9
// => true
```

However, beware of type conversion when comparing non-numbers against numbers. For instance, when a string is compared with a number, the JavaScript engine tries to convert the string to a number:
```js
88 > '9'
// => true
```

If the engine can't convert the string into a number, the comparison will always return `false`:
```js
88 >= 'hello'
// => false

88 <= 'hello'
// => false
```

Strings are compared with other strings lexicographically, meaning character-by-character from left-to-right. The following returns `false` because the Unicode value of `8`, the first character in `88`, is less than the Unicode value of `9`.
```js
'88' > '9'
// => false
```

***Top Tip***: Stick to comparing numerical values with the relational operators and you'll be golden.

## Resources
- MDN
  + [Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)
  + [Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
- [JavaScript Equality Table](http://dorey.github.io/JavaScript-Equality-Table/)
- [freeCodeCamp Forum — JavaScript Comparison Operators](https://forum.freecodecamp.org/t/javascript-comparison-operators/14660)
