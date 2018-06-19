# JS Learning Notes

## Outline
### 1. Eloquent JS
  - [1.1 Chapter 1: Values, Types and Operators](#chapter1)
  - [1.2 Chapter 2: Program structure](#chapter2)
  - [1.3 Chapter 3: Functions](#chapter3)
### 2. You Don't Know JS: Scope & Closures
  - [2.1 Chapter 1: What is Scope](#scope)
  - [2.2 Chapter 2: Lexical Scope](#l-scope)
---
# [Eloquent JS](http://eloquentjavascript.net/)
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
---
## <a name="chapter3"></a>Chapter 3: Functions
* **General objective of functions**
  - Structure larger program
  - Reduce repetition
  - Associate names with subprograms
  - Isolate subprograms from each other
  - Defining new vocabulary
* **Defining a function**
  - A function definition is a regular binding of which the value is a function
  - A function can have a set of parameters (or none at all) and a body that must be wrapped in brackets even if there is only one line of code
  - Some functions provide value, some don't but only side effect 
  - `return` determines the value function provides, and end the function as well
  - functions that don't have `return` simply return undefined
  - Parameters to a function are like regular bindings, but their initial values are given by the *caller* instead of code in functions itself
* [**Scope**](#scope)
  - Bindings have scopes, means its visibility in which part of program
  - Global bindings are defined outside of functions, and are visible in the whole program
  - Local bindings are declared as function parameter or inside functions, thus can only be seen by such functions
  - Everytime function is called, new instances of local bindings are created; in other words, each function has its own "world"
  - `let` and `const` bindings are local to *block* they are declared in, but `var`(pre ES6) is visible throughout whole function that they appear in or throughout global if they are not in functions
    ```Javascript
    let x = 10;
    if (true) {
      let y = 20;
      var z = 30;
      console.log(x + y + z);
      // → 60
    }
    // y is not visible here
    console.log(x + z);
    // → 40
    ```
  - JS does not only distinguishes *local* and *global* bindings, but also allows to create functions and scopes inside other blocks and functions, produces multiple degrees of locality
  - when multiple binding have same name, code can see **only innermost** one
  - [*lexical scoping*](#l-scope): The set of bindings visible inside a block is determined by the place of that block in the program text. Each local scope can also see all the local scopes that contain it, and all scopes can see the global scope. 
  - **Function as a value** is different than defined function with `const`. A function value can do everything the latter can do, but it can also be assigned new value as other bindings.
  - **Function declareation** is a shorter way to create a function binding and it doesn't require a semicolon after it. It is **not** a part of top to bottom flow, so it can be called before it is declared.
  - **Arrow function** has the syntax of:
    ```javascript
    const someFunction = (a, b) => {do nothing};
    const otherFunction = a => a * 2;
    //or shorter version if there is only one line
    ```
  * **Call stack** is the place where computer store the function context. When the stack grows too big, "stack over flow".
  * JavaScript is extremely broad-minded about the number of arguments you pass to a function. If you pass too many, the extra ones are ignored. If you pass too few, the missing parameters get assigned the value `undefined`.
  * **Closure** is a feature of being able to reference a specific instance of a local binding in an enclosing scope. A function that references bindings from local scopes around it is called a *closure*.
    ```javascript
    function multiplier (factor) {
      return number => number * factor;
    } 
    let twice = multiplier(2);
    console.log(twice(5));
    // -> 10
    ```
  









---
# [You Don't Know JS: Scope & Closures](https://github.com/getify/You-Dont-Know-JS)

## <a name="scope"></a>Chapter 1: Scope & Closures
* **Scope** is a well-defined set of rules for storing variables in some location and for finding those variables at a later time
* **JS is a compiled language**, there are three steps in a traditional compiled language before code gets executed:

  1. **Tokenizing/Lexing**: breaking up a string of characters into meaningful chunks. e.g. `var a = 2` will be broken into `var`, `a`, `=`, `2`
  2. **Parsing**: taking an array of tokens and turning it into a tree(Abstract Syntax Tree) of nested elements, which represents grammatical structure e.g. `var a = 2` starts with a top-level node called `VariableDeclaration`(var), with a child node called `Identifier`(a) and another child called `AssignmentExpression`(=)which itself has a child called `NumericLiteral`(2)
  3. **Code-generation**: the process of taking AST and turn it into executable code. e.g. take AST for `var a = 2` and turn it into machine instruction which creates a variable called `a`, reserve memory for it and then store a value `2` into `a`
* **JS engine** is vastly more complex than the above three steps, it doesn't have plenty of time to optimize because its compilation happens mostly mere miliseconds before the code executed. To simplify it, JS compile the code that it's about to execute just before its execution
* **Three characters to interact to process the program**:

  1. *Engine*: responsible for compilation and execution, say a 'soldier'
  2. *Compiler*: all the parsing and code-generation, say a 'translator'
  3. *Scope*: collect all the declared Identifier in its list and ensure rules how these are accesible by currently executing code, say a 'commander'
* As for `var a = 2`, engine sees it as two statements -- one for itself to handle during execution, one for compiler to handle during compilation

  -> *Compiler* encounter the code
  -> *Compiler* asks *Scope* to check if variable `a` already exists
  -> if yes, *Compiler* will ignore and move on
  -> if no, *Compiler* asks *Scope* to declare a new variable 
  -> *Compiler* produces code for *Engine*
  -> *Engine* asks *Scope* if variable `a` exist in current scope
  -> if yes, *Engine* uses that variable
  -> if not, *Engine* looks elsewhere
  -> if found something, *Engine* then assign value to it
  -> if nothing has been found, *Engine* reports error
* *Engine* needs to consult *Scope* to see if variable was declared, there are two types of 'consult': LHS(Left-hand Side) and RHS(Right-hand Side).
  ```Javascript
  console.log(a); 
  // this is RHS because nothing is assigned to a here and we are retrieving the value of a
  a = 2;
  // this is LHS because we find the variable a and assign a value to it
  ```
* LHS is about 'who's the target of the assignment' while RHS is about 'who's the source of the assignment'
* **Nested scope**: *Engine* starts at the currently executing *Scope*, look for the variable there; if not found, keeps going up one level till it gets to global scope, either found or error
* When RHS fails to find a variable `ReferenceError` will be thrown; however, if LHS fails to find a variable, the global *Scope* will create such variable in the global scope and hand it back to *Engine*
* If a variable is found by RHS but you try to do something impossible with it, such as calling it as a function when it actually is not or referece on a `null` or `undefined` value, the *Engine* will throw `TypeError`

* `ReferenceError` is *Scope* resolution-failure related, whereas `TypeError` implies that *Scope* resolution was successful, but that there was an illegal/impossible action attempted against the result

---
## <a name="l-scope"></a>Chapter 2: Lexical Scope
* JavaScript employs *Lexical Scope*
* The first phase of compiler is called *lexing*(tokenizing), it examines a string of source code characters and assigns semantic meaning 
* *Lexical Scope* is scope that is defined at lexing time, thus is based on where variables and block of scope are written
* **Scope look-up stops once it finds the first match**. The same identifier names can be specified at multiple layers of nested scope, this is called **shadowing**
* No matter where a function is invoked from, or even how it is invoked, its lexical scope is **only** defined by where the function was declared
* `eval(...)` or `with` can somehow cheat lexical scope, but it is bad practise because code runs slow because of them. If the Engine finds an `eval(..)` or `with` in the code, it essentially has to assume that all its awareness of identifier location may be invalid, because it cannot know at lexing time exactly what code you may pass to `eval(..)` to modify the lexical scope, or the contents of the object you may pass to `with` to create a new lexical scope to be consulted. In other words, in the pessimistic sense, most of those optimizations it would make are pointless if `eval(..)` or `with` are present, so it simply doesn't perform the optimizations at all.





