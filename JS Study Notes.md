# JS Learning Notes

[Study Material: EloquentJS](http://eloquentjavascript.net/)

## Outline
1. [Chapter 1: Values, Types and Operators](#chapter1)
2. [Chapter 2: Program structure](#chapter2)

## <a name="chapter1"></a>Chapter 1: Values, Types and Operators 
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
- strings, numbers and boolean (true or false) are immutable; in the case of stKvring, it cannot be divided, multiplied or subtracted
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
---

## <a name="chapter2"></a>Chapter 2: Program structure
* **Expressions**
  - Like a small part in natural language, such as a word or any unfinished part
  - A fragment of code / a sentence fragment
  - In between parentheses is also expression (such as if statement, for loop)
  - Because of its language-based interface nature, expression can contain other expression just like human's nested language
  - Can be content to just produce a value used by enclosing code
* **Statement**
  - Correspond to a full sentence, and a program is a list of statement
  - Simplest statement is an expression with semicolon after it: 
      
    `1;` 
    
    `!false;`
  - Stands on its on, amounts to "change the world", e.g. *display something on the screen*, *change the internal state of the machine that will affect the statement after it*(this is called [***side effect***](#side-effect))

* The **importance of semicolon**: although in some cases, JS allows ommiting of semicolon; however, in some cases, ommiting semicolon will cause the next lines of code being considered as the same line of which ommit a semicolon. The **best practice** is to always write semicolon for each statement.
* **Variables/bindings**
  - Used for catch and hold values
  - After binding initiated, its name can be used as an expression
  - when this binding points at a value, it is **NOT** tied to that value forever, namely you can alway bind a new value to this binding
  - Bindings/variables are more like tentacles rather than boxes because they *do not* contain but rather *grasp* values; thus, two bindings can point to the same value
  - A program can only access values that they have reference to, you always need to grow a tentacle or assign an existing tentacle to hold on to the value you will need
  - When you define a binding without giving a value, the tentacle has nothing to grasp therefore it is **undefined**
  - Bindings can be declared in three expressions: `var`(pre ES-6), `let`(reassignable variables), `const`(constant binding)
  - Binding names can be any word, but only symbles as `$` or `_` can be used
  - There are words with special meaning such as `let`, they are called *keywords* that are preserved for JS language itself
* **Function**  
  - It is a piece of program wrapped in a value
  - Executing a function is called *invoking*, *calling* or *applying*
  - Values given to functions are called *arguments*
  - `console.log` is a function used to output values
  - Showing a dialog box or writing text to screen is a <a name="side-effect"></a>**Side effect** of some functions.
  - Function may produce(**return**) values so they don't need side effect to be useful
  - Anything that produces value is an expression, which means funciton can be used within larger expressions
* **Control flow**: When program contains multiple statements, they run from top to bottom
* **conditional execution**
  - We may create programs that has branches and needs to decide which branch to go based on situation, which is conditional execution: `if` statement
  - After `if`, statement is wrapped in `{ }`, this can group multiple statements in to one statement, which is called a *block*
  - Follow `if`, to add one more branch, you may use `else` to create the second and only branch
  - If the branches are more than two, then you use `if...else if...else...`
* **While and doo loops**
  - When we need to run a piece of code multiple times, it is called a *loop*
  - `while(statement)` is a loop that it keeps entering this statement unless the statement is no longer true
  - A `do` loop is very similar to `while` loop, the differece is that `do` loop always execute at least once
* **For loops**
  - General format: `for(let i = 0; i < length; i++) {}`
  - first `let i = 0` initialize the loop by defining a binding; `i < length` checks if the loop continues or not; `i++` updates the state of the loop after every iteration
* **Breaking out a loop**: exept for having the condition `false` to jump out of the loop, you can simply add `break` to do the same thing; if you write a program that alway produce `true` in a loop,your program will stuck in a *infinite loop*. In such scenario, the browser will take too long time to run and will end up asking you if you want to close the page even the browser itself.
* **Switch**
  - Syntax: 
  
    ```Javascript
    switch(somecondition){
      case "rainy":
        console.log("It is going to rain.");
        break;
      case "sunny":
        console.log("It is going to be sunny.");
        break;
      default:
        console.log("Unknown weather type.");
        break;
    }
    ```
  - This piece of program will check if giving value meets any giving case and `break`, otherwise it is going to default.
  - It is easy to forget adding break, which would cause unwanted code to be run
  - Using `if...else if...else...` is still better and cleaner in some way
* **Naming convention - camelCase**: when you name a function or variable, the format of the name should follow camel case: the first letter lowercase and every first letter of a character should be captalized, e.g. thisIsACamelCaseName
* **Comment**
  - Syntax: `//` for single line of comments; `/*  */`for multiple lines of comments
  - A comment is a piece of text that is part of the program but is completely ignored by the computer, thus it is mainly written for human reader
  - A good habit for a developer is to write comments between the code to explain the thoughts and idea, so other developers can understand his code


