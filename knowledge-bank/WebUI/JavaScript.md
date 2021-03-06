# Java Script

#### Navigation
- [Basics](JavaScript.md#basics)
  - [Fundamental Examples](JavaScript.md#fundamental-examples)
  - [JS Types](JavaScript.md#js-types)
  - [Undefined and Null Types](JavaScript.md#undefined-and-null-types)
  - [NaN Value](JavaScript.md#nan-value)
  - [JS Arrays](JavaScript.md#js-arrays)
  - [Specific Operators](JavaScript.md#specific-operators)
  - [Conversion Methods](JavaScript.md#conversion-methods)
  - [Date Object](JavaScript.md#date-object)
  - [Typical Loops](JavaScript.md#typical-loops)
  - [JS Events](JavaScript.md#js-events)
- [JSON, AJAX](JavaScript.md#json-ajax)
  - [JSON](JavaScript.md#json)
  - [AJAX](JavaScript.md#ajax)
- [JS Regular Expressions](JavaScript.md#js-regular-expressions)
  - [Regular Expression Patters](JavaScript.md#regular-expression-patters)
  - [RegExp Object Methods](JavaScript.md#regexp-object-methods)
- [Function, Class, Object, Prototype and Closure](JavaScript.md#function-class-object-prototype-and-closure)
  - [Function, Class and Object Example](JavaScript.md#function-class-and-object-example)
  - [Prototype](JavaScript.md#prototype)
  - [Closure](JavaScript.md#closure)
- [JS Classes and Modules](JavaScript.md#js-classes-and-modules)
- [JS Security](JavaScript.md#js-security)
- [JS Performance and Memory Management](JavaScript.md#js-performance-and-memory-management)
- [JS Code Quality](JavaScript.md#js-code-quality)
- [JQuery Basics](JavaScript.md#jquery-basics)
  - [Common JQuery Functions](JavaScript.md#common-jquery-functions)

#### Basics
- JavaScript is case-sensitive
- JavaScript is based on ECMAScript standard. Latest version of this standard (ECMAScript6, ES6, ES 2015) includes new capabilities such as classes, modules, iterators, arrow functions, collections, etc. Other realizations of ECMAScript: ActionScript, JScript, etc.
- JavaScript isn't strongly typed language

###### Fundamental Examples

```js
var x = 16 + 4 + "v"; // 20v
var y = "v" + 16 + 4; // v164
document.getElementById("myDiv").innerHtml = "<span>some stuff</span>" // set custom html into #myDiv
```

###### JS Types
- Available JS types are:

```js
var length = 16; // Number
var lastName = "Johnson"; // String
var cars = [ "Saab", "Volvo", "BMW" ]; // Array
var x = { firstName: "John", lastName: "Doe" }; // Object
var flag = true; // Boolean
var a; // Undefined
var b = null; // Null
```

###### Undefined and Null Types
- `var person; // Undefined (value and type is undefined)`
- `var person = undefined; // Undefined (value and type is undefined)`
- `var person = null; // Null (value is null, type is an object)`
- Undefined vs Null gives the following results:
  - `typeof undefined // undefined`
  - `typeof null // object`
  - `null === undefined // false`
  - `null == undefined // true`

###### NaN Value
- NaN means *not a number*
- Use `isNaN()` function to check if your value is an illegal number

```js
isNaN(5 / 0); // returns false, result = Infinity, typeof = number
isNaN(0 / 0); // returns true, result = NaN, typeof = number
isNaN(true); // returns false, result = true, typeof = boolean
isNaN(""); // returns false, result = "", typeof = string
isNaN("Hello"); // returns true, result = Hello, typeof = string
```

###### JS Arrays
- JS arrays can contain anything you want - `var myArray = ["1", 2, true];`
- Use `myArray.length` property to get array's length

###### Specific Operators
- `typeof` operator - checks data type
- `==` operator - checks value only
- `===` operator - checks value and type

###### Conversion Methods
- `String(123)`, `(123).toString()` - convert numbers to strings
- `String(false)`, `true.toString()` - convert booleans to strings
- `String(Date())`, `Date().toString()` - convert dates to strings
- `Number("3.14")`, `Number("")` - convert strings to numbers
- `parseInt()`, `parseFloat()` - parse strings to numbers

###### Date Object
- There are four ways of instantiating a date:

```js
var d = new Date();
var d = new Date(milliseconds);
var d = new Date(dateString);
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);
```

- Date object methods
  - `getDate()`, `getYear()`, `getDay()`, `getMonth()`, `getHours()`, `getMinutes()`, `getSeconds()`
  - `setDate()`, `setFullYear()`, `setMonth()`, `setHours()`, `setMinutes()`, `setSeconds()`
  - UTC versions of methods above, etc.

###### Typical Loops
- `for`
- `for-in` (used to go through object properties)
- `while`
- `do-while`

###### JS Events
- Typical events:
  - `onchange`
  - `onclick`
  - `onmouseover`
  - `onmouseout`
  - `onkeydown`
  - `onload`, etc.
- To attach an event:

```js
// 3rd parameter: true - capturing phase, false (default) - bubbling phase
document.getElementById("myDiv").addEventListener("mousemove", myFunction, false);
```

- To remove an event:

```js
document.getElementById("myDiv").removeEventListener("mousemove", myFunction);
```

#### JSON, AJAX

###### JSON
- JSON example:

```js
{"employees":[
    {"firstName":"John", "lastName":"Doe"},
    {"firstName":"Anna", "lastName":"Smith"},
    {"firstName":"Peter", "lastName":"Jones"}
]}
```

- JSON construction,  parsing and usage:

```js
// construct JSON object
var text = '{ "employees" : [' +
'{ "firstName":"John" , "lastName":"Doe" },' +
'{ "firstName":"Anna" , "lastName":"Smith" },' +
'{ "firstName":"Peter" , "lastName":"Jones" } ]}';
// convert JSON into JavaScript object
var obj = JSON.parse(text);
// use the new JavaScript object in your page
document.getElementById("myDiv").innerHTML = obj.employees[1].firstName +
                                             " " + obj.employees[1].lastName; 
```

###### AJAX
- AJAX (Asynchronous JavaScript and XML) is a technology which allows you to reload some parts of your page after page has been loaded by making async requests and receiving async responses
- XMLHttpRequest object is used to make AJAX requests and receive responses

```js
var asyncRequest = new XMLHttpRequest();
// attach response handler
asyncRequest.onreadystatechange = handler();
// prepare and send request
asyncRequest.open("post", "https://mysite.com/api/");
asyncRequest.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
asyncRequest.send();

// the handler which receives async response
function handler() {
 var readyState = asyncRequest.readyState;
 if (readyState === 4) {
  var response = asyncRequest.responseText;
  // do something with response here...
 }
};
```

#### JS Regular Expressions
- Pattern example: `var regExp1 = /ab[a-zA-Z]+/i`
- Regular expression modifiers:
  - `i` - case insensitivity
  - `g` - global match
  - `m` - multiline

###### Regular Expression Patters

| Pattern | Description |
| --- | --- |
| . | Any character |
| * | 0+ repeats |
| + | 1+ repeats |
| ? | 0 or 1 repeats |
| \w | A word |
| \W | Not a word |
| \d | A digit |
| \D | Not a digit |
| \s | A whitespace |
| \S | Not a whitespace |
| \b | Beginning and end of a word |
| \B | Not beginning or end of a word |
| \0 | Null character |
| ^ | Beginning of an expression |
| $ | End of an expression |
| [0-9] | Any digit from a range |
| [a-z] | Any letter from a range |
| n(5) | Repeat `n` five times |
| m(3, 7) | Repeat `m` from three to seven times |
| (x `\|` y) | Any alternative separated with `\|` |

###### RegExp Object Methods
- `test()` method returns `true` or `false`

```js
var patt = /life/;
var res = patt.test("The best things in life are free!"); // res === true
```

- `exec()` method returns matched object

```js
var res = /life/.exec("The best things in life are free!"); // res === "life"
```

- `toString()` method returns the string value of the regular expression

#### Function, Class, Object, Prototype and Closure

###### Function, Class and Object Example

```js
// 1. Function example
function myFunction(a, b) {
 // any code here
 return a * b;
};
myFunction(3, 4); // call the function (result is 12)

// 1.1. Call the function via `call` method
var myObject = myFunction.call(myObject, 10, 2); // myObject = 20

// 1.2. Call the function via `apply` method
var myArray = [10, 2];
var myObject = myFunction.apply(myObject, myArray);  // myObject = 20

// 2. Class example
var person = function(name, age) {
 this.name = name;
 this.age = age;
};
var david = new person("David Wolf", 26); // instantiate person class
var name = david.name; // access class' property

// 3. Object example
var person = {
 firstName: "David",
 lastName: "Wolf"
};
var fn = person.firstName; // access object's property
person.Age = 26; // add new property to that particular object
```

###### Prototype
- Every object has a prototype
- Prototype is also an object
- You can add more functionality to existing classes via their prototypes

```js
// this is person class
var person = function(firstName, lastName) {
 this.firstName = firstName;
 this.lastName = lastName;
};
// here we instantiate person class
var myFather = new person("David", "Joe");
// here we add new method to this class via its prototype
person.prototype.fullName = function() {
 return this.firstName + " " + this.lastName; // here we can access existing class' properties or methods
};
// here we access new method from earlier instantiated instance
myFather.fullName();
```

###### Closure
- Closure can be used to create private variables inside a function

```js
// create add() closure with private counter
var add = (function() {
 var counter = 0; // this is private variable, which can be accessed via add() call only
 return function() {
  return counter += 1;
 };
})();
add(); // counter = 1
add(); // counter = 2
add(); // counter = 3
```

#### JS Classes and Modules

#### JS Security

#### JS Performance and Memory Management

#### JS Code Quality

#### JQuery Basics
- Basic jQuery script

```js
$(document).ready(function()() {
    // any jQuery code here
});
```

- Compatibility issues with other JS libraries

```js
// Option 1 (standard)
$.noConflict(); // use `jQuery` instead of `$
// Option 2 (named)
var jq = $.noConflict(); //  use `jq` instead of `$
```

- Common jQuery selectors (examples)
  - `*` - select all
  - `this` - select current HTML element
  - `p.intro` - select all `<p class="intro">` elements
  - `ul li:first-child` - select first `<li>` element of every `<ul>` list
  - `tr:even` - select all even `<tr>` blocks, `tr:odd` - select all odd `<tr>` blocks
- Common jQuery events
  - `ready`
  - `mouseenter`
  - `focus`
  - `click`
  - `blur`
  - `hover`
  - `on`, etc.

###### Common JQuery Functions
- Effects
  - `hide()`, `show()`, `animate()`, `fadein()`, `fadeout()`, `stop()`
- HTML/DOM
  - `text()`, `val()`, `attr()`, `html()`, `append()`, `after()`, `before()`, `addClass()`, `removeClass()`, `css()`
- Dimensions
  - `width()`, `height()`, `innerWidth()` (includes padding), `outherWidth()` (includes border), `outherWidth(true)` (includes margin), and the same functions for height
- Ancestors
  - `parent()`, `childer()`, `find()`, `siblings()`, `next()`, `prev()`, `first()`, `last()`
- Ajax
  - `$.ajax()`, `$.get()`, `$.post()`
