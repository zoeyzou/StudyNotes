# JS Learning Notes

[Study Material: EloquentJS](http://eloquentjavascript.net/)

## Chapter 1: Values, Types and Operators
- Values are chunks that represent pieces of information stored somewhere in the memory as *bits*
- Value has type that determines its role, e.g. number / pieces of text(string) / functions etc
- Once value is no longer used, the memory will be recycled for the next generation of values
- JS only uses 64 bits to store numbers, which means the 64th power of 2; when number does not fit into this, it'll *overflow*
- for very big or very small number, add *e* as exponent, e.g. 2.998e8 means 299,800,000
- Operators: +, -, *, /, % etc, and precedence of the operators is applied
- special numbers: infinite, -infinite, NaN
- To mark strings, one can use: single quotes / double quotes / backticks
- backslash "\\" in a string means escaping to convey special meanings, such as \n means newline
- when a string has "\\", include double backslash \\\ 
- if string is written inside backticks (usually called *template literals*), it can embed other values, such as "`half of 100 is ${100 / 2}`" will be shown as "half of 100 is 50"
- strings, numbers and boolean (true or false) are immutable; in the case of string, it cannot be divided, multiplied or subtracted
- *Concatenate" can glue strings together so produce a new string (different location than the glued strings in memory)
- *Unary* Operator takes only **1** value (e.g. *typeof*); *binary* operator uses **2** values (e.g. (10-2)); *ternary* operator, operating on **3** values (e.g. true? 1 : 2)
- Minus operator can be both unary and binary operator (e.g. (10-2), -8)
- Boolean values evaluates between two possibilities, either *true* or *false*
- When strings are compared, JS goes over the characters from left to right, comparing Unicode one by one, not exactly alphabetic
- in JS, only one value is *not equal* to itself: **NaN**
- && represents logical *and* whereas || represents logical *or*; *not* is written as "!", it flips true to false or vice verse
- Empty values include *null* and *undefined* are values but carry no information
- null and undefined can be mostly treated *interchangeable*
- *Type coersion* happens when an operator is applied to the "wrong" type of values and JS convert the value to the types it needs, but may not be something you expect (e.g. true + false = 1)
- A good reading on [type coersion](https://medium.freecodecamp.org/js-type-coercion-explained-27ba3d9a2839)
- When comparing with "==", you get true when both values are same (except for NaN); however, when types differ, type coersion will occur (type conversion)
- When null or undefined occurs on either side, it produces true only if both sides are either null or undefined; this is useful when you want to test whether a value has a real value by comparing it to null with "=="
- To avoid type coersion, use "===" to test whether a value is *precisely* equal to the other or "!==" of the opposite
- && and || handles value of different types this way: convert the value on left side to Boolean value, return either *original* left-hand value or right-hand value
- || returns left-hand value when it can be converted to *true* and otherwise right-hand, && returns left-hand value when it can be converted to *false*; both of them **only** evaluate the right-hand value when necessary


