

### js Notes
### JavaScript Fundamentals
<details>
<summary>External scripts</summary>

If we have a lot of JavaScript code, we can put it into a separate file.

Script files are attached to HTML with the src attribute:

```
<script src="/path/to/script.js"></script>
Here, /path/to/script.js is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, src="script.js", just like src="./script.js", would mean a file "script.js" in the current folder.
```
We can give a full URL as well. For instance:
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
To attach several scripts, use multiple tags:

<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
```

### Please note:
As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its cache.

Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once.

That reduces traffic and makes pages faster.

If src is set, the script content is ignored.
A single <script> tag can’t have both the src attribute and code inside.

This won’t work:
```
<script src="file.js">
  alert(1); // the content is ignored, because src is set
</script>
```
We must choose either an external <script src="…"> or a regular <script> with code.

The example above can be split into two scripts to work:
```
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
</details>
# Use hotkeys for comments!
In most editors, a line of code can be commented out by pressing the Ctrl+/ hotkey for a single-line comment and something like Ctrl+Shift+/ – for multiline comments (select a piece of code and press the hotkey). For Mac, try Cmd instead of Ctrl and Option instead of Shift.

Nested comments are not supported!
There may not be /*...*/ inside another /*...*/.

Such code will die with an error:

```
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
### The modern mode, "use strict"
For a long time, JavaScript evolved without compatibility issues. New features were added to the language while old functionality didn’t change.

That had the benefit of never breaking existing code. But the downside was that any mistake or an imperfect decision made by JavaScript’s creators got stuck in the language forever.

This was the case until 2009 when ECMAScript 5 (ES5) appeared. It added new features to the language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: "use strict".

“use strict”
The directive looks like a string: "use strict" or 'use strict'. When it is located at the top of a script, the whole script works the “modern” way.

For example:
```
"use strict";

// this code works the modern way
```

We can declare variables to store data by using the var, let, or const keywords.

let – is a modern variable declaration.
var – is an old-school variable declaration. Normally we don’t use it at all,
const – is like let, but the value of the variable can’t be changed.
#Uppercase const?
importance: 4
Examine the following code:
```
const birthday = '18.04.1982';

const age = someCode(birthday);
```
Here we have a constant birthday for the date, and also the age constant.

The age is calculated from birthday using someCode(), which means a function call that we didn’t explain yet (we will soon!), but the details don’t matter here, the point is that age is calculated somehow based on the birthday.

Would it be right to use upper case for birthday? For age? Or even for both?
```
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
```

In JavaScript, there are 3 types of quotes.

Double quotes: "Hello".
Single quotes: 'Hello'.
Backticks: `Hello`.
Double and single quotes are “simple” quotes. There’s practically no difference between them in JavaScript.

Backticks are “extended functionality” quotes. They allow us to embed variables and expressions into a string by wrapping them in ${…}, for example:
```
let name = "John";

// embed a variable
alert( `Hello, ${name}!` ); // Hello, John!

// embed an expression
alert( `the result is ${1 + 2}` ); // the result is 3
```

###There are 8 basic data types in JavaScript.

Seven primitive data types:
number for numbers of any kind: integer or floating-point, integers are limited by ±(253-1).
bigint for integer numbers of arbitrary length.
string for strings. A string may have zero or more characters, there’s no separate single-character type.
boolean for true/false.
null for unknown values – a standalone type that has a single value null.
undefined for unassigned values – a standalone type that has a single value undefined.
symbol for unique identifiers.
And one non-primitive data type:
object for more complex data structures.
The typeof operator allows us to see which type is stored in a variable.

Usually used as typeof x, but typeof(x) is also possible.
Returns a string with the name of the type, like "string".

## Terms: “unary”, “binary”, “operand”

An operator is unary if it has a single operand. For example, the unary negation - reverses the sign of a number:
```
let x = 1;

x = -x;
alert( x ); // -1, unary negation was applied
```
An operator is binary if it has two operands. The same minus exists in binary form as well:
```
let x = 1, y = 3;
alert( y - x ); // 2, binary minus subtracts values
```
Formally, in the examples above we have two different operators that share the same symbol: the negation operator, a unary operator that reverses the sign, and the subtraction operator, a binary operator that subtracts one number from another.

```
let sum = a + b; // here a and b or operands  
```

The following math operations are supported:

Addition +,
Subtraction -,
Multiplication *,
Division /,
Remainder %,
Exponentiation **.

The first four are straightforward, while % and ** need a few words about them.

Remainder %
The remainder operator %, despite its appearance, is not related to percents.

The result of a % b is the remainder of the integer division of a by b.

For instance:

alert( 5 % 2 ); // 1, the remainder of 5 divided by 2
alert( 8 % 3 ); // 2, the remainder of 8 divided by 3
alert( 8 % 4 ); // 0, the remainder of 8 divided by 4
Exponentiation **
The exponentiation operator a ** b raises a to the power of b.

In school maths, we write that as ab.

For instance:

alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
Just like in maths, the exponentiation operator is defined for non-integer numbers as well.

For example, a square root is an exponentiation by ½:

alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root)
alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)

String concatenation with binary

Here’s a more complex example:

alert(2 + 2 + '1' ); // "41" and not "221"
Here, operators work one after another. The first + sums two numbers, so it returns 4, then the next + adds the string 1 to it, so it’s like 4 + '1' = '41'.

alert('1' + 2 + 2); // "122" and not "14"

Here, the first operand is a string, the compiler treats the other two operands as strings too. The 2 gets concatenated to '1', so it’s like '1' + 2 = "12" and "12" + 2 = "122".

The binary + is the only operator that supports strings in such a way. Other arithmetic operators work only with numbers and always convert their operands to numbers.

Here’s the demo for subtraction and division:

alert( 6 - '2' ); // 4, converts '2' to a number
alert( '6' / '2' ); // 3, converts both operands to numbers

umeric conversion, unary +
The plus + exists in two forms: the binary form that we used above and the unary form.

The unary plus or, in other words, the plus operator + applied to a single value, doesn’t do anything to numbers. But if the operand is not a number, the unary plus converts it into a number.

For example:

// No effect on numbers
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

// Converts non-numbers
alert( +true ); // 1
alert( +"" );   // 0
It actually does the same thing as Number(...), but is shorter.

The need to convert strings to numbers arises very often. For example, if we are getting values from HTML form fields, they are usually strings. What if we want to sum them?

The binary plus would add them as strings:

let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", the binary plus concatenates strings
If we want to treat them as numbers, we need to convert and then sum them:

let apples = "2";
let oranges = "3";

// both values converted to numbers before the binary plus
alert( +apples + +oranges ); // 5

// the longer variant
// alert( Number(apples) + Number(oranges) ); // 5

Operator precedence
If an expression has more than one operator, the execution order is defined by their precedence, or, in other words, the default priority order of operators.

From school, we all know that the multiplication in the expression 1 + 2 * 2 should be calculated before the addition. That’s exactly the precedence thing. The multiplication is said to have a higher precedence than the addition.

Parentheses override any precedence, so if we’re not satisfied with the default order, we can use them to change it. For example, write (1 + 2) * 2.

Chaining assignments
Another interesting feature is the ability to chain assignments:

let a, b, c;

a = b = c = 2 + 2;

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
Chained assignments evaluate from right to left. First, the rightmost expression 2 + 2 is evaluated and then assigned to the variables on the left: c, b and a. At the end, all the variables share a single value.
Once again, for the purposes of readability it’s better to split such code into few lines:

c = 2 + 2;
b = c;
a = c;
That’s easier to read, especially when eye-scanning the code fast.

Modify-in-place
We often need to apply an operator to a variable and store the new result in that same variable.

For example:

let n = 2;
n = n + 5;
n = n * 2;
This notation can be shortened using the operators += and *=:

let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert( n ); // 14

Short “modify-and-assign” operators exist for all arithmetical and bitwise operators: /=, -=, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

let n = 2;

n *= 3 + 5; // right part evaluated first, same as n *= 8

alert( n ); // 16


Increment/decrement
Increasing or decreasing a number by one is among the most common numerical operations.

So, there are special operators for it:

Increment ++ increases a variable by 1:

let counter = 2;
counter++;        // works the same as counter = counter + 1, but is shorter
alert( counter ); // 3
Decrement -- decreases a variable by 1:

let counter = 2;
counter--;        // works the same as counter = counter - 1, but is shorter
alert( counter ); // 1
Important:
Increment/decrement can only be applied to variables. Trying to use it on a value like 5++ will give an error.


Is there any difference? Yes, but we can only see it if we use the returned value of ++/--.

Let’s clarify. As we know, all operators return a value. Increment/decrement is no exception. The prefix form returns the new value while the postfix form returns the old value (prior to increment/decrement).

To see the difference, here’s an example:

let counter = 1;
let a = ++counter; // (*)

alert(a); // 2
In the line (*), the prefix form ++counter increments counter and returns the new value, 2. So, the alert shows 2.

Now, let’s use the postfix form:

let counter = 1;
let a = counter++; // (*) changed ++counter to counter++

alert(a); // 1
In the line (*), the postfix form counter++ also increments counter but returns the old value (prior to increment). So, the alert shows 1.

To summarize:

If the result of increment/decrement is not used, there is no difference in which form to use:

let counter = 0;
counter++;
++counter;
alert( counter ); // 2, the lines above did the same
If we’d like to increase a value and immediately use the result of the operator, we need the prefix form:

let counter = 0;
alert( ++counter ); // 1
If we’d like to increment a value but use its previous value, we need the postfix form:

let counter = 0;
alert( counter++ ); // 0
Increment/decrement among other operators
The operators ++/-- can be used inside expressions as well. Their precedence is higher than most other arithmetical operations.

For instance:

let counter = 1;
alert( 2 * ++counter ); // 4
Compare with:

let counter = 1;
alert( 2 * counter++ ); // 2, because counter++ returns the "old" value
Though technically okay, such notation usually makes code less readable. One line does multiple things – not good.

While reading code, a fast “vertical” eye-scan can easily miss something like counter++ and it won’t be obvious that the variable increased.

We advise a style of “one line – one action”:

let counter = 1;
alert( 2 * counter );
counter++;

Bitwise operators
Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:

AND ( & )
OR ( | )
XOR ( ^ )
NOT ( ~ )
LEFT SHIFT ( << )
RIGHT SHIFT ( >> )
ZERO-FILL RIGHT SHIFT ( >>> )

String comparison
To see whether a string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order.

In other words, strings are compared letter-by-letter.

For example:

alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
The algorithm to compare two strings is simple:

Compare the first character of both strings.
If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
Repeat until the end of either string.
If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.
In the first example above, the comparison 'Z' > 'A' gets to a result at the first step.

The second comparison 'Glow' and 'Glee' needs more steps as strings are compared character-by-character:

G is the same as G.
l is the same as l.
o is greater than e. Stop here. The first string is greater.

Not a real dictionary, but Unicode order
The comparison algorithm given above is roughly equivalent to the one used in dictionaries or phone books, but it’s not exactly the same.

For instance, case matters. A capital letter "A" is not equal to the lowercase "a". Which one is greater? The lowercase "a". Why? Because the lowercase character has a greater index in the internal encoding table JavaScript uses (Unicode). We’ll get back to specific details and consequences of this in the chapter Strings.

Nullish coalescing operator '??'
A recent addition
This is a recent addition to the language. Old browsers may need polyfills.
The nullish coalescing operator is written as two question marks ??.

As it treats null and undefined similarly, we’ll use a special term here, in this article. For brevity, we’ll say that a value is “defined” when it’s neither null nor undefined.

The result of a ?? b is:

if a is defined, then a,
if a isn’t defined, then b.
In other words, ?? returns the first argument if it’s not null/undefined. Otherwise, the second one.

The nullish coalescing operator isn’t anything completely new. It’s just a nice syntax to get the first “defined” value of the two.

We can rewrite result = a ?? b using the operators that we already know, like this:

result = (a !== null && a !== undefined) ? a : b;
Now it should be absolutely clear what ?? does. Let’s see where it helps.

The common use case for ?? is to provide a default value.

For example, here we show user if its value isn’t null/undefined, otherwise Anonymous:

let user;

alert(user ?? "Anonymous"); // Anonymous (user is undefined)
Here’s the example with user assigned to a name:

let user = "John";

alert(user ?? "Anonymous"); // John (user is not null/undefined)

We can also use a sequence of ?? to select the first value from a list that isn’t null/undefined.

Let’s say we have a user’s data in variables firstName, lastName or nickName. All of them may be not defined, if the user decided not to fill in the corresponding values.

We’d like to display the user name using one of these variables, or show “Anonymous” if all of them are null/undefined.

Let’s use the ?? operator for that:

let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// shows the first defined value:
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder

The important difference between them is that:

|| returns the first truthy value.
?? returns the first defined value.

In other words, || doesn’t distinguish between false, 0, an empty string "" and null/undefined. They are all the same – falsy values. If any of these is the first argument of ||, then we’ll get the second argument as the result.

In practice though, we may want to use default value only when the variable is null/undefined. That is, when the value is really unknown/not set.

For example, consider this:

let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
The height || 100 checks height for being a falsy value, and it’s 0, falsy indeed.
so the result of || is the second argument, 100.
The height ?? 100 checks height for being null/undefined, and it’s not,
so the result is height “as is”, that is 0.

Using ?? with && or ||
Due to safety reasons, JavaScript forbids using ?? together with && and || operators, unless the precedence is explicitly specified with parentheses.

The code below triggers a syntax error:

let x = 1 && 2 ?? 3; // Syntax error

The limitation is surely debatable, it was added to the language specification with the purpose to avoid programming mistakes, when people start to switch from || to ??.

Use explicit parentheses to work around it:

let x = (1 && 2) ?? 3; // Works

alert(x); // 2


Defining functions
Function declarations:
A function definition (also called a function declaration, or function statement) consists of the function keyword followed by:

The name of the function.
A list of parameters to the function, enclosed in parentheses and separated by commas.
The JavaScript statements that define the function, enclosed in curly braces, { /* … */ }.
For example, the following code defines a simple function named square:

JS
```
Copy to Clipboard
function square(number) {
  return number * number;
}
```

Function expressions
While the function declaration above is syntactically a statement, functions can also be created by a function expression.

Such a function can be anonymous; it does not have to have a name. For example, the function square could have been defined as:



```
const square = function (number) {
  return number * number;
};
```
console.log(square(4)); // 16
However, a name can be provided with a function expression. Providing a name allows the function to refer to itself, and also makes it easier to identify the function in a debugger's stack traces:
```
const factorial = function fac(n) {
  return n < 2 ? 1 : n * fac(n - 1);
};

console.log(factorial(3)); // 6
```
Function expressions are convenient when passing a function as an argument to another function. The following example shows a map function that should receive a function as first argument and an array as second argument:
```
function map(f, a) {
  const result = new Array(a.length);
  for (let i = 0; i < a.length; i++) {
    result[i] = f(a[i]);
  }
  return result;
}
```
In the following code, the function receives a function defined by a function expression and executes it for every element of the array received as a second argument:

const cube = function (val) {
  return val*val*val;
}
let res = map(cube(3),[1,2,3,4,5]);

```
<script async src="//jsfiddle.net/srinivasgundale/fntoyu5r/14/embed/"></script>
```
