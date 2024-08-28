In JavaScript, both at() and charAt() are methods used to access a specific character in a string, but they have some key differences:

charAt(index)
Purpose: Returns the character at a specified index in a string.
Input: Takes a single argument, the index (position) of the character in the string.
Output: Returns a string containing the character at the specified index.
Index Handling: If the index is out of range (negative or greater than the length of the string), it returns an empty string ("").
Example:

javascript
Copy code
let str = "Hello";
console.log(str.charAt(1));  // Output: "e"
console.log(str.charAt(10)); // Output: ""
at(index)
Purpose: Also returns the character at a specified index in a string.
Input: Takes a single argument, the index of the character in the string.
Output: Returns a string containing the character at the specified index.
Index Handling: Supports negative indexing, where an index of -1 refers to the last character, -2 to the second-to-last, and so on. If the index is out of range, it returns undefined.
Example:

javascript
Copy code
let str = "Hello";
console.log(str.at(1));   // Output: "e"
console.log(str.at(-1));  // Output: "o"
console.log(str.at(10));  // Output: undefined
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
