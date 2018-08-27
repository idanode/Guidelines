# Contents

 - [Variable declarations](#variable-declarations-pencil)

     - [Variables](#variables-speech_balloon)
     - [Constants](#constants-triangular_flag_on_post)
     - [Globals](#globals-earth_africa)

 - [Semicolons](#semicolons-pencil2)
 - [Method and property definitions](#method-and-property-definitions-paperclip)
 - [Deleting properties](#deleting-properties-x)
 - [`eval()`](#eval)
 - [Iterating objects and arrays](#iterating-objects-and-arrays)
 - [Multiline strings](#multiline-strings-guitar)
 - [Modifying prototypes of built-in objects](#modifying-prototypes-of-built-in-objects-shit)
 - [Naming things](#naming-things-thought_balloon)
 - [Curly braces](#curly-braces-curly_loop)
 - [Array and Object Initializers](#array-and-object-initializers-file_folder)
 - [Commas](#commas)
 - [Blank lines](#blank-lines)
 - [Binary and Ternary operators](#binary-and-ternary-operators)
 - [Quotes](#quotes-speech_balloon)
 - [Comments](#comments-notes)
 - [Project naming](#project-naming)

## Variable declarations :pencil:

### Variables :speech_balloon:


Using `var` in general or `let` when they should be accesible only in specific blocks (e.g. `if`).

```js
// One declaration
var foo = 1;

// Multiple declarations
var foo = 1
  , bar = "Hello World"
  , anotherOne = [{ foo: "bar" }]
  ;

if (...) {
   let baz = 42;
  /* do something with baz */
}
```

### Constants :triangular_flag_on_post:


Using `const`. The constant names are written with UPPERCASE letters. Please also use `const` when including libraries using `require` and when they should not be changed. In this case, the names will not be with caps.

```js
// Dependencies
const http = require("http")
   , fs = require("fs")
   , EventEmitter = require("events").EventEmitter
// Constants
const PI = Math.PI
    , MY_CONSTANT = 42
    ;
```

### Globals :earth_africa:


Please define globals when there is no commonjs environment (this is actually handled by [`dist-it`](https://github.com/IonicaBizau/dist-it). When Please manually define globals, Please do that using `window.MyGlobal` (on the client) and `global.MyGlobal` (on the server).

## Semicolons :pencil2:


Please *use* semicolons. Almost always.

```js
var foo = 1;
function bar (x) {
    var someMethod = function (m) {
        console.log(m);
    };
    return { y: x, foo: someMethod };
}
class Foo {
    ...
}
```

## Method and property definitions :paperclip:


Please use the ES6 `class` for creating classes.

```js
class Person {
    constructor (name, age) {
        this.name = name;
        this.age = age;
    }
    getName () {
        return this.name;
    }
}
```

## Deleting properties :x:


Please nullify the properties when that's fine:

```js
var foo = {
    bar: 42
};
foo.bar = null;
```


However, Please use the `delete` keyword when Please really want to delete them.

```js
delete foo.bar;
```

## `eval()`


`eval` is evil. :rage: Do not use it. However Please use it in some test files and in places where Please have to execute the JavaScript code provided by the user.


For converting strings to JSON, use `JSON.parse(strObj)`.

## Iterating objects and arrays


For arrays, most of times, Please use the `forEach` function:

```js
arr.forEach(c => {
    // do something
});
```


However, using `for` loops is fine too:

```js
for (var i = 0; i < arr.length; ++i) {
    for (var ii = 0; ii < arr[i].length; ++ii) {
        ...
    }
    ...
}
```


For objects, Please use the following style:

```js
Object.keys(obj).forEach(k => {
    var cValue = obj[k];
    // do something
});
```


To simplify this, Please created [`iterate-object`](https://github.com/IonicaBizau/iterate-object), which abstracts this functionality:

```js
const iterateObject = require("iterate-object");
iterateObject(obj, (value, key) => {
    // do something
});
```

## Multiline strings :guitar:


Please use backticks to create multiline strings:

```js
var multiLineStr = `Lorem ipsum dolor sit amet, consectetur adipisicing elit
sed do eiusmod tempor incididunt ut labore et dolore magna
aliqua. Ut enim ad minim veniam, quis nostrud exercitation
ullamco laboris nisi ut aliquip ex ea commodo consequat
New line again...`;
```

## Modifying prototypes of built-in objects :shit:


Just don't, unless that's the scope of the library.

## Naming things :thought_balloon:


Using camel case notation for variables, in general. For constructors Please capitalize the variable name (e.g. `EventEmitter`).

```js
// Node.JS require
const fs = require("fs")
    , events = require("events")
    , EventEmitter = events.EventEmitter
    ;

// Local variables
var x = 1
  , twoWords = "Hello World"
  ;

// Functions
function fooBar () {...}

// Classes
class Person {
    constructor (name, age) {
        this.name = name;
        this.age = age;
    }
    getName () {
        return this.name;
    }
}
// Object fields
var obj = {
    full_name: "Johnny B."
  , age: 20
};
obj.methodA = function () {...};
```

## Curly braces :curly_loop:


Open the curly brace at the end of the line. Always put the instructions between curly braces, even there is only one instruction.

```js
if (expr) {
    instr;
} else {
    instr2;
    instr3;
}
```

## Array and Object Initializers :file_folder:


See examples.

```js
// Arrays
var arr = [1, 2, 3, 4];

var lotOfElms = [
    1, 2, 3, 4, 5, 6, 7
  , 8, 9, 10, 11, 12, 13
  , 14, 15, 16, 17, 18
];

var bigElms = [
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod."
  , "Tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim."
  , "Veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea."
  , "Commodo consequat. Duis aute irure dolor in reprehenderit in voluptate"
];

// Objects
var obj = { a: 1 };

var obj1 = {
    full_name: "Johnny B."
  , age: 20
};
```

## Commas


Put commas at the beginning of the line, not at the end.

```js
var x = 1
  , y = 2
  ;

const C_1 = 42
    , C_2 = -42
    ;

var obj = {
    x: 1
  , y: 2
};
```

## Blank lines


Group the instructions inserting some blank lines where it's needed.

```js
foo(x);
bar(x);

foo(y);
bar(y);
```

## Binary and Ternary operators


See examples.

```js
var foo = someObj
    .method()
    .method2()
    .method3()
    ;

var a = cond ? v1 : v2;

var b = long_condition_here
        ? v1 : v2
        ;

var c = another_long_condition_here
        ? with_some_long_value
        : or_another_some_long_value
        ;
```

## Quotes :speech_balloon:


Double quotes, with some exceptions when single quotes are used.

```js
var foo = "\"Hello\", he said.";
var jQuerySelector = "div.myClass[data-foo='bar']";
```

## Comments :notes:


Put relevant comments. The comments start with uppercase letter.

```js
// Dependencies
const lib1 = require("lib1")
    , lib2 = require("lib2")
    ;

// Constants
const FOURTY_TWO = 42;
```


Use JSDoc comments for functions and methods.

```js
/**
* sum
* Calculates the sum of two numbers.
*
* @name sum
* @function
* @param {Number} a The first number,
* @param {Number} b The second number.
* @return {Number} The sum of the two numbers.
*/
function sum (a, b) {
  return a + b;
};
```
