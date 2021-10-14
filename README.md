# javascript-cheatsheet


1. [Literals](#literals)
1. [Constants](#constants)
1. [Declarations](#declarations)
1. [Statements](#statements)
1. [Functions](#functions)
1. [Promises](#promises)
1. [AsyncAwait](#asyncawait)
1. [Classes](#classes)
1. [String](#string)
1. [Examples](#examples)


## Literals
JavaScript provides seven different data types:

| Data Types  | Examples                                                              |
| ----------- | --------------------------------------------------------------------- |
| `undefined` | A variable that has not been assigned a value is of type `undefined`. |
| `null`      | no value.                                                             |
| `string`    | `'a', 'aa', 'aaa', 'Hello!', '11 cats'`                               |
| `number`    | `12, -1, 0.4`                                                         |
| `boolean`   | `true, false`                                                         |
| `object`    | A collection of properties.                                           |
| `symbol`    | Represents a unique identifier.                                       |

```javascript
255, 0377, 0xff             // Numbers (decimal, octal, hex)
123.0, 1.23e2               // double (real) numbers
'a', '\141', '\x61'         // String (literal, octal, hex)
'\n', '\\', '\'', '\"'      // Newline, backslash, single quote, double quote
"string\n"                  // String ending with newline and \0
true, false                 // bool constants 1 and 0
{type:"Fiat", model:"500"}  // object literal
```

## Constants

```javascript
Number.MAX_SAFE_INTEGER     // (2^53 - 1)
Number.MIN_SAFE_INTEGER     // -(2^53 - 1)
Number.MAX_VALUE            // Largest positive representable number
Number.MIN_VALUE            // Smallest positive representable number
```

## Declarations

ES6 var, let and const
Unlike var, let throws an error if you declare the same variable twice.
Variables declared with let inside a block, statement, or expression, its scope is limited to that block, statement, or expression.
Variables declared with const are read-only and cannot be reassigned.
Objects (including arrays and functions) assigned to a variable using const are still mutable and only prevents the reassignment of the variable identifier.
To ensure your data doesn't change, JavaScript provides a function Object.freeze to prevent data mutation.

```javascript
var x;                      // Declare undefined var
let x=255;                  // Declare and initialize x to 255 (block scoped)
const x=255;                // Declare and initialize x to 255 (function scoped)
const ourDecimal = 255.5;   // float
const c='a';                // Usually 8 bit character
const b=true;               // true or false
const a, b, c;              // Multiple declarations
const x = new Array(10);    // array of size 10, all elements undefined
const y = new Array(10, 5); // array of size 2: [10, 5]
const x = [];               // array of size 0
x[2] = 12;                  // x is now size 3: [undefined, undefined, 12]
const x = [10];             // array of size 1: 10
const PI = 3.141;           // const number 3.141
const cars = ["Saab", "Volvo", "BMW"]; // You can create a constant array
cars[0] = "Toyota";         // You can change an element
cars.push("Audi");          // You can add an element
cars = ["Toyota", "Volvo", "Audi"];    // ERROR, cannot reassign array
const car = {type:"Fiat", model:"500"} // Const car object
const sum = function(x, y)  // Declare function as var
{ return x + y; };
sum(2,3)                    // Would return 5
var operations = [sum];     // Store function in array
operations[0](2,3)          // Would return 5
var student = {             // Declare Object
  name: "Mary",
  age: 10
}
student.name                // Return "Mary"
student["name"]             // Return "Mary"
student.gender = "female"   // Add gender member to object
delete student.gender       // Delete gender member from object
student.prototype.hat="red";// Create hat member of object student
```
## Statements

```javascript
x=y;                        // Every expression is a statement
var x;                      // Declarations are statements
;                           // Empty statement
{                           // A block is a single statement
    var x;                  // Scope of x is from declaration to end of block
}
if (x) a;                   // If x is true (not 0), evaluate a
else if (y) b;              // If not x and y (optional, may be repeated)
else c;                     // If not x and not y (optional)

while (x) a;                // Repeat 0 or more times while x is true

for (x; y; z) a;            // Equivalent to: x; while(y) {a; z;}

for (x : y) a;              // Range-based for loop e.g.
                            // for (auto& x in someList) x.y();

for (key in object)         // For in iterates through keys
const numbers = [45, 4, 9, 16, 25];
for (let x in numbers) { console.log(numbers[x]);}

for (value of object)       // For of iterates through values
const numbers = [45, 4, 9, 16, 25];
for (let x of numbers) { console.log(x);}

function myFunction(value, index, array) {console.log(value);}
numbers.forEach(myFunction);// Iterate through numbers

do a; while (x);            // Equivalent to: a; while(x) a;

switch (x) {                // x must be int
    case X1: a;             // If x == X1 (must be a const), jump here
    case X2: b;             // Else if x == X2, jump here
    default: c;             // Else jump here (optional)
}
break;                      // Jump out of while, do, or for loop, or switch
continue;                   // Jump to bottom of while, do, or for loop
try { a; }
catch (T t) { b; }          // If a throws a T, then jump here
catch (...) { c; }          // If a throws something else, jump here
```
## Functions

```javascript
function f(x, y)            // f is a function returning x*y
{return x*y;};
let x = f(2,2);             // x will be 4
const f = (x, y) =>         // Array function syntax
{return x*y}
const f = (x, y) => x*y;    // Implicit return
function f(x=1,y=2)         // f() is equivalent to f(1,2)
```

## Promises

Promise guarantees it will run upon success or failure of a task (downloading file, etc)

```javascript
let p = new Promise((resolve, reject) => {  // This runs immediately
	let a = 1 + 1;
  if (a == 2){
  	resolve('success');
  } else {
  	reject('failed');
  }
})

p.then((message) => {       // Runs upon completetion
console.log("this is in the then " + message);    // Called from Resolve
}).catch((message) => {
	console.log('This is in the catch ' + message); // Called from Failed
})

const prmOne = new Promise((resolve, reject) => {resolve('1 Done')})
const prmTwo = new Promise((resolve, reject) => {resolve('2 Done')})
Promise.all([               // Runs when all promises are completed
  prmOne,
  prmTwo
]).then((message) => {
  console.log(message)
})

Promise.race([               // Runs when the first promise is completed
  prmOne,
  prmTwo
]).then((message) => {
  console.log(message)
})
```

## AsyncAwait

Calling an async function always results in a promise.

```javascript
const getFruit = async name => { return "banana" }
const makeSmoothie = async() => {
	const a = await getFruit()
  console.log(a)
}
makeSmoothie()                // banana
```
Await waits for a promise to be fulfilled, then returns its value


## Classes

```javascript
class SomeClass {           // A new type
  constructor(a, b) {       // Constructor
    this.a = a;             // Member var
  }
  someMethod() {            // Method
    console.log('do thing');
  }
}
const someClass = new SomeClass('a','b'); // Declare new instance
class OtherClass extends SomeClass{ // Inheritance
  constructor(a, b) {
    super(a,b);                     // Parent Constructor
  }
  static utilMethod(){}             // Static Method
}

```


## String

```javascript
const str = "my string";    // Create string
str.indexOf("my");          // Position of first occurance
str.slice(0, 2);            // Pulls a specified part of a string
str.toUpperCase();          // turns characters of string to uppercase
str.startsWith("my");       // returns true if string starts with value
str.startsWith("my", 2);    // returns true if string starts with value from position
str.endsWith("my");         // true if string ends with value
str.includes("string");     // true if string includes value passed in
str.repeat(2);              // returns the repeated string
```

## Examples

These are a simple set of examples for teaching and learning basic javascript
and web fundamentals.

1. [this](https://github.com/peterlamar/javascript-cheatsheet/tree/master/this)
1. [arrow functions](https://github.com/peterlamar/javascript-cheatsheet/tree/master/arrow)
1. [app cues](https://github.com/peterlamar/javascript-cheatsheet/tree/master/appcues)
1. [firebase](https://github.com/peterlamar/javascript-cheatsheet/tree/master/firebase)
1. [pwa](https://github.com/peterlamar/javascript-cheatsheet/tree/master/your-first-pwapp-master)
