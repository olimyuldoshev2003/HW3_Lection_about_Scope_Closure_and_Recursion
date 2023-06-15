# HW3_Lection_about_Scope_Closure_and_Recursion


# Theme 1: Javascript Scope

Scope refers to the availability of variables and functions in certain parts of the code.

In JavaScript, a variable has two types of scope:

1. Global Scope
2. Local Scope

## Global Scope

A variable declared at the top of a program or outside of a function is considered a global scope variable.

Let's see an example of a global scope variable.

```js
// program to print a text 
let a = "hello";

function greet () {
    console.log(a);
}

greet(); // hello
```

In the above program, variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is declared at the top of a program and is a global variable. It means the variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> can be used anywhere in the program.

The value of a global variable can be changed inside a function.

<h2 style="color: red">Example:</h2>

```js
// program to show the change in global variable
let a = "hello";

function greet() {
    a = 3;
}

// before the function call
console.log(a);

//after the function call
greet();
console.log(a); // 3
```

In the above program, variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is a global variable. The value of <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">hello</h3>. Then the variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is accessed inside a function and the value changes to **3**.

>**Note**: It is a good practice to avoid using global variables because the value of a global variable can change in different areas in the program. It can introduce unknown results in the program.

In JavaScript, a variable can also be used without declaring it. If a variable is used without declaring it, that variable automatically becomes a global variable.

<h2 style="color: red">Example:</h2>

```js
function greet() {
    a = "hello"
}

greet();

console.log(a); // hello
```

In the above program, variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is a global variable.

If the variable was declared using <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let a = "hello"</h3>, the program would throw an error.

## Local Scope

A variable can also have a local scope, i.e it can only be accessed within a function.

## Example 1: Local Scope Variable

```js
// program showing local scope of a variable
let a = "hello";

function greet() {
    let b = "World"
    console.log(a + b);
}

greet();
console.log(a + b); // error
```

<h2 style="color: red">Output:</h2>

```js
helloWorld
Uncaught ReferenceError: b is not defined
```

In the above program, variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3> is a global variable and variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> is a local variable. The variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> can be accessed only inside the function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">greet</h3>. Hence, when we try to access variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> outside of the function, an error occurs.

## let is Block Scoped

The <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3> keyword is block-scoped (variable can be accessed only in the immediate block).

## Example 2: block-scoped Variable

```js
// program showing block-scoped concept
// global variable
let a = 'Hello';

function greet() {

    // local variable
    let b = 'World';

    console.log(a + ' ' + b);

    if (b == 'World') {

        // block-scoped variable
        let c = 'hello';

        console.log(a + ' ' + b + ' ' + c);
    }

    // variable c cannot be accessed here
    console.log(a + ' ' + b + ' ' + c);
}

greet();
```

<h2 style="color: red">Output:</h2>

```js
Hello World
Hello World hello
Uncaught ReferenceError: c is not defined
```

In the above program, variable

- <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3>  is a global variable. It can be accessed anywhere in the program.
- <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3>  is a local variable. It can be accessed only inside the function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">greet</h3> .
- <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3>  is a block-scoped variable. It can be accessed only inside the <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">if</h3>  statement block.

Hence, in the above program, the first two <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">console.log()</h3> work without any issue.

However, we are trying to access the block-scoped variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">c</h3> outside of the block in the third  <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">console.log()</h3> . This will throw an error.

>Note: In JavaScript, <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">var</h3> is function scoped and <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3> is block-scoped. If you try to use <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">var c = 'hello';</h3> inside the <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">if</h3> statement in the above program, the whole program works, as <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">c</h3> is treated as a local variable.

<br><br>

# Theme 2: JavaScript Hoisting

Hoisting in JavaScript is a behavior in which a function or a variable can be used before declaration.

<h2 style="color: red">Syntax:</h2>

```js
// using test before declaring
console.log(test);   // undefined
var test;
```

The above program works and the output will be <h3 style="display:inline-block; height:30px; border:1px solid gray; border-radius:5px;">undefined</h3>. The above program behaves as

```js
// using test before declaring
var test;
console.log(test); // undefined
```

Since the <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">variable</h3> test is only declared and has no value, <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">undefined</h3> value is assigned to it.

>**Note:** In hoisting, though it seems that the declaration has moved up in the program, the actual thing that happens is that the function and variable declarations are added to memory during the compile phase.

## Variable Hoisting

In terms of variables and constants, keyword <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">var</h3>  is hoisted and <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3>  and <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">const</h3>  does not allow hoisting.

<h2 style="color: red">Example:</h2>

```js
// program to display value
a = 5;
console.log(a);
var a; // 5
```

<h2 style="color: red">Output:</h2>

```js
undefined
```

The above program behaves as:

```js
var a;
console.log(a);
a = 5;
```

Only the declaration is moved to the memory in the compile phase. Hence, the value of variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3>  is <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">undefined</h3>  because <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">a</h3>  is printed without initializing it.

Also, when the variable is used inside the function, the variable is hoisted only to the top of the function.

<h2 style="color: red">Example:</h2>

```js
// program to display value
var a = 4;

function greet() {
    b = 'hello';
    console.log(b); // hello
    var b;
}

greet(); // hello
console.log(b);
```

<h2 style="color: red">Output:</h2>

```js
hello
Uncaught ReferenceError: b is not defined
```

In the above example, variable <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> is hoisted to the top of the function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">grret</h3> and becomes a local variable. Hence <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> is only accessible inside the function. <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">b</h3> does not become a global variable.

>**Note**: In hoisting, the variable declaration is only accessible to the immediate scope.

If a variable is used with the <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3> keyword, that variable is not hoisted.

<h2 style="color: red">Example:</h2>

```js
// program to display value
a = 5;
console.log(a);
let a; // error
```

<h2 style="color: red">Output:</h2>

```js
Uncaught ReferenceError: Cannot access 'a' before initialization
```

While using <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3>, the variable must be declared first.

## Function Hoisting

A function can be called before declaring it.

<h2 style="color: red">Example:</h2>

```js
// program to print the text
greet();

function greet() {
    console.log('Hi, there.');
}
```

<h2 style="color: red">Output:</h2>

```js
Hi, there
```

In the above program, the function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">greet</h3> is called before declaring it and the program shows the output. This is due to hoisting.

However, when a function is used as an **expression**, an error occurs because only declarations are hoisted.

<h2 style="color: red">Example:</h2>

```js
// program to print the text
greet();

let greet = function() {
    console.log('Hi, there.');
}
```

<h2 style="color: red">Output:</h2>

```js
Uncaught ReferenceError: greet is not defined
```

If <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">var</h3> was used in the above program, the error would be:

```js
Uncaught TypeError: greet is not a function
```

> Note: Generally, hoisting is not performed in other programming languages like Python, C, C++, Java.

>Hoisting can cause undesirable outcomes in your program. And it is best to declare variables and functions first before using them and avoid hoisting.

>In the case of variables, it is better to use <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">let</h3> than <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">var</h3>.

<br><br>

# Theme 3: JavaScript Recursion
Recursion is a process of calling itself. A function that calls itself is called a recursive function.

<h2 style="color: red">Syntax:</h2>

```js
function recurse() {
    // function code
    recurse();
    // function code
}

recurse();
```

A recursive function must have a condition to stop calling itself. Otherwise, the function is called indefinitely.

Once the condition is met, the function stops calling itself. This is called a base condition.

To prevent infinite recursion, you can use <p style="color:aqua; display:inline;">if...else statement </p> (or similar approach) where one branch makes the recursive call, and the other doesn't.

### So, it generally looks like this:

```js
function recurse() {
    if(condition) {
        recurse();
    }
    else {
        // stop calling recurse()
    }
}

recurse();
```

A simple example of a recursive function would be to count down the value to 1.

## Example 1: Print Numbers

```js
// program to count down numbers to 1
function countDown(number) {

    // display the number
    console.log(number);

    // decrease the number value
    const newNumber = number - 1;

    // base case
    if (newNumber > 0) {
        countDown(newNumber);
    }
}

countDown(4);
```

<h2 style="color: red">Output:</h2>

```js
4
3
2
1
```

In the above program, the user passes a number as an argument when calling a function.

In each iteration, the number value is decreased by 1 and function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">countDown()</h3> is called until the number is positive. Here, <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">newNumber > 0</h3> is the base condition.

This recursive call can be explained in the following steps:

```js
countDown(4) prints 4 and calls countDown(3)
countDown(3) prints 3 and calls countDown(2)
countDown(2) prints 2 and calls countDown(1)
countDown(1) prints 1 and calls countDown(0)
```

When the number reaches **0**, the base condition is met, and the function is not called anymore.

## Example 2: Find Factorial

```js
// program to find the factorial of a number
function factorial(x) {

    // if number is 0
    if (x === 0) {
        return 1;
    }

    // if number is positive
    else {
        return x * factorial(x - 1);
    }
}

const num = 3;

// calling factorial() if num is non-negative
if (num > 0) {
    let result = factorial(num);
    console.log(`The factorial of ${num} is ${result}`);
}
```

<h2 style="color: red">Output:</h2>

```js
The factorial of 3 is 6
```

When you call function <h3 style="display:inline-block; height:30px; border: 1px solid gray; border-radius:5px;">factorial()</h3> with a positive integer, it will recursively call itself by decreasing the number.

This process continues until the number becomes 1. Then when the number reaches 0, 1 is returned.