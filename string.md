In JavaScript, both at() and charAt() are methods used to access a specific character in a string, but they have some key differences:

charAt(index)
-------------
Purpose: Returns the character at a specified index in a string.
Input: Takes a single argument, the index (position) of the character in the string.
Output: Returns a string containing the character at the specified index.
Index Handling: If the index is out of range (negative or greater than the length of the string), it returns an empty string ("").
Example:

```
let str = "Hello";
console.log(str.charAt(1));  // Output: "e"
console.log(str.charAt(10)); // Output: ""
//print in reverse order
for(i=1; i<=str.length; i++){
    console.log(str[i]);
    console.log(str.at(str.length - i));
}
for(i=str.length-1; i>= 0; i--){
   console.log(str[i]);
   console.log(str.charAt(i));
}
for (let i = -1; i >= -str.length; i--) {
    console.log(str.charAt(i)); // returns empty
}
```

at(index)
---------
Purpose: Also returns the character at a specified index in a string.
Input: Takes a single argument, the index of the character in the string.
Output: Returns a string containing the character at the specified index.
Index Handling: Supports negative indexing, where an index of -1 refers to the last character, -2 to the second-to-last, and so on. If the index is out of range, it returns undefined.
Example:
```
let str = "Hello";
console.log(str.at(1));   // Output: "e"
console.log(str.at(-1));  // Output: "o"
console.log(str.at(10));  // Output: undefined

//print in reverse order
for(i=1; i<=str.length; i++){
    console.log(str[i]);
    console.log(str.at(str.length - i));
}
for(i=str.length-1; i>= 0; i--){
   //console.log(i)
  console.log(str[i]);
    console.log(str.at(i));
}
for (let i = -1; i >= -str.length; i--) {
    console.log(str.at(i));
}
//Output
o
l
l
e
H
```
Key Differences:
Negative Indexing:

charAt() does not support negative indexing.
at() does support negative indexing.
Out-of-Range Behavior:

charAt() returns an empty string for out-of-range indices.
at() returns undefined for out-of-range indices.
Browser Support:

charAt() is an older method and is supported in all browsers.
at() is a newer addition (introduced in ECMAScript 2022) and may not be supported in very old environments.

charCodeAt()
-------------
The charCodeAt() method of String values returns an integer between 0 and 65535 representing the UTF-16 code unit at the given index.

```
let str = "Hello";
const index = 4;

console.log(
  `Character code ${str.charCodeAt(index)} is equal to ${str.charAt(
    index,
  )}`,
);
//print in reverse order
 for(i=str.length-1; i>= 0; i--){
   //console.log(i);
   console.log(str.charCodeAt(i));
}
//output
111
108
108
101
72
"Character code 111 is equal to o"
```

charCodeAt() and codePointAt()
------------------------------
are two methods used to obtain the numeric value (code point) of a character in a string, but they have some differences, especially when dealing with characters that are represented by surrogate pairs.

charCodeAt(index)
Purpose: Returns the UTF-16 code unit (a 16-bit number) at the specified index in a string.
Input: Takes an index as an argument.
Output: Returns an integer between 0 and 65535 (representing a UTF-16 code unit).
Limitations: For characters outside the Basic Multilingual Plane (BMP) (i.e., characters with code points above 65535), charCodeAt() only returns the first code unit of the surrogate pair, not the entire character.
Example:

````
let str = "A"; // U+0041
console.log(str.charCodeAt(0));  // Output: 65

let emoji = "💻"; // U+1F4BB (Laptop Emoji)
console.log(emoji.charCodeAt(0));  // Output: 55357 (First part of the surrogate pair)
console.log(emoji.charCodeAt(1));  // Output: 57019 (Second part of the surrogate pair)
codePointAt(index)
````
Purpose: Returns the full Unicode code point value at the specified index.
Input: Takes an index as an argument.
Output: Returns an integer representing the full Unicode code point.
Advantages: Handles characters outside the BMP properly, returning the full code point for characters represented by surrogate pairs.
Example:
```
let str = "A"; // U+0041
console.log(str.codePointAt(0));  // Output: 65

let emoji = "💻"; // U+1F4BB (Laptop Emoji)
console.log(emoji.codePointAt(0));  // Output: 128187 (Full code point)
```
Key Differences:
Handling of Surrogate Pairs:

charCodeAt() returns the code unit (part of a surrogate pair) and not the full code point for characters outside the BMP.
codePointAt() returns the full Unicode code point, even for characters represented by surrogate pairs.
Output:

charCodeAt() returns a value between 0 and 65535, corresponding to a single UTF-16 code unit.
codePointAt() can return values greater than 65535, corresponding to the full code point of a character.
When to Use:
Use charCodeAt() when dealing with strings within the BMP or when only the UTF-16 code unit value is needed.
Use codePointAt() when you need to accurately get the full Unicode code point of any character, especially for characters outside the BMP, such as many emojis and less common symbols

String.prototype.concat()
----------------------------
The concat() method of String values concatenates the string arguments to this string and returns a new string.
```
const str1 = 'Hello';
const str2 = 'World';

console.log(str1.concat(' ', str2));
// Expected output: "Hello World"

console.log(str2.concat(', ', str1));
// Expected output: "World, Hello"


const hello = "Hello, ";
console.log(hello.concat("Kevin", ". Have a nice day."));
// Hello, Kevin. Have a nice day.

const greetList = ["Hello", " ", "Venkat", "!"];
"".concat(...greetList); // "Hello Venkat!"

"".concat({}); // "[object Object]"
"".concat([]); // ""
"".concat(null); // "null"
"".concat(true); // "true"
"".concat(4, 5); // "45"

let str = ["Hello", "World", "Welcome"];
let str1 = ["to", "the", "javascript"];
console.log(str.concat(str1))


let obj = {
name:"hello",
type: "javascript"
}
let obj1 = {
name:"hello",
type: "javascript"

}
console.log(obj.concat(obj1)) //error

```

The concat method is not available for objects in JavaScript. The concat method is specifically used for arrays and strings, not for objects.


For Objects
To merge objects, you should use methods such as:

Object Spread Syntax: { ...obj1, ...obj2 }
Object.assign(): Object.assign(target, source1, source2, ...)
Here's an example using Object.assign() for merging objects:

Example:
```
let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };

let merged = Object.assign({}, obj1, obj2);

console.log(merged);
// Output: { a: 1, b: 2, c: 3, d: 4 }

let obj1 = { a: 1 };
let obj2 = { b: 2 };
let obj3 = { c: 3 };

let merged = { ...obj1, ...obj2, ...obj3 };

console.log(merged);
// Output: { a: 1, b: 2, c: 3 }

````

Handling Property Overwrite
When merging objects, if there are properties with the same name, the values from the latter objects will overwrite those from the earlier ones.

Example:
```
let obj1 = { a: 1, b: 2 };
let obj2 = { b: 3, c: 4 };

let merged = { ...obj1, ...obj2 };

console.log(merged);
// Output: { a: 1, b: 3, c: 4 }
```
In this example, the property b from obj2 overwrites the property b from obj1.

In summary, while concat is not applicable for objects, you can use the spread syntax or Object.assign() to achieve similar results when working with objects.



String.prototype.endsWith()
------------------------------
The endsWith() method of String values determines whether a string ends with the characters of this string, returning true or false as appropriate.
```
const str1 = 'Cats are the best!';

console.log(str1.endsWith('best!'));
// Expected output: true

console.log(str1.endsWith('best', 17));
// Expected output: true

const str2 = 'Is this a question?';

console.log(str2.endsWith('question'));
// Expected output: false

const str = "To be, or not to be, that is the question.";

console.log(str.endsWith("question.")); // true
console.log(str.endsWith("to be")); // false
console.log(str.endsWith("to be", 19)); // true

```

endsWith(searchString)
endsWith(searchString, endPosition)


String.prototype.includes()
------------------------------
The includes() method of String values performs a case-sensitive search to determine whether a given string may be found within this string, returning true or false as appropriate.

```
const sentence = 'The quick brown fox jumps over the lazy dog.';

const word = 'fox';

console.log(
  `The word "${word}" ${
    sentence.includes(word) ? 'is' : 'is not'
  } in the sentence`,
);
// Expected output: "The word "fox" is in the sentence"
"Blue Whale".includes("blue"); // returns false
"Blue Whale".toLowerCase().includes("blue"); // returns true
const str = "To be, or not to be, that is the question.";

console.log(str.includes("To be")); // true
console.log(str.includes("question")); // true
console.log(str.includes("nonexistent")); // false
console.log(str.includes("To be", 1)); // false
console.log(str.includes("TO BE")); // false
console.log(str.includes("")); // true


```
includes(searchString)
includes(searchString, position)



