# Javascript ES6

## Introduction

-   Basically ECMAScript is just the result of Microsoft and Netscape banging their heads together many many moons ago to try and come up with a standard for their scripting languages which they were using.
-   Microsoft was using what's known as a `JScript` and Netscape we're using `JavaScript`
-   So ECMAScript is just a standard for scripting languages and ECMAScript 6 is just the latest standardized version of ECMAScript and includes tons of new features.
-   It's not fully supported in all browsers, so if you were going to use this in a live project then you're probably going to want to use something called a `transpiler` which will essentially take your `es6` code and transpile it into `es5` so that it works in browsers.
-   Now one exaplle of transpiler you could use is a `Babel`.

## Constants

-   For creating constants we use `const`

```js
const pi = 3.14;
```

-   If we don't want this value to be overridden by mistake any point we declare it as `const`

## The let keyword

-   There's a few different ways we can make a variable the first way to create one is by using the `let` keyword

```js
let age = 12;
console.log(age); // prints 12
```

-   So this let keyword creates us a variable and if we want to override the value of those variables later on we can do so

```js
age = 30;
console.log(age); // prints 30
```

## Scope of variable

-   Scope of a variable means the area in which a variable value is relevant.
-   When we define a variable using `let` or `const` in the root of the document, meaning not inside any code block, it's in the root of the document, then that will have `global scope` and that means it can be accessed anywhere in the file.
-   We are allowed to do declare a variable with same name as a global variable declared using `let` inside a code block even though it's got the same name.

```js
let age = 40;
{
    let age = 30;
    console.log(age); // 30
}
console.log(age); // 40
```

-   In above eg, When we redefine the variable, what it does is recreate this variable but it gives it a local scope. Now we can only access this version of age inside this code block.
-   Once we define a constant we can't change them. But the same rules of scope apply to `const` as they do to let variables.
-   So this idea of block scope is one of the main advantages of using `let` in `const` instead of the older `var` keyword.
-   When we make a variable using `var` it ignores block scope

## Default Parameters

-   Default parameters are basically parameters that a function can rely on as a backup if parameters aren't explicitly declared or pass through to the function when we call it.

```js
function logData(name = "Tom") {
    console.log("Name: " + name);
}

logData("Shaun"); // prints - Name: Shaun
logData(); //ptints - Name: Tom
```

## The Spread Operator

-   The spread operator is this nifty new feature in es6 that can basically take an array and just spread them into individual elements.
-   This is achieved using the three dots `...`, known as spread operator

```js
const numArray1 = [1, 2, 3];
const numArray2 = [numArray1, 4, 5];
const numArray3 = [...numArray1, 4, 5];

console.log(numArray2); // [ [ 1, 2, 3 ], 4, 5 ]
console.log(numArray3); // [ 1, 2, 3, 4, 5 ]
```

## Template Strings

-   Template strings are pretty similar to normal strings except they've got a few extra features baked in which are pretty cool.
-   We would normally define a `string` using quotes like that either double or single, but with `template strings` we have to use `backticks`.

```js
function logData(name) {
    console.log(`Name: ${name}`);
}

logData("Shaun"); // prints - Name: Shaun
```

## New String Methods

-   `repeat`: The repeat method basically lets us just repeat a string over and over.

```js
const str = "Great";
console.log(str.repeat(5)); // Great Great Great Great Great
```

-   `startsWith`: We can check whether a string starts with a certain series of characters. We can also pass a second parameter as to where to check that string from.

```js
const str = "goodbye";
console.log(str.startsWith("good")); // true
console.log(str.startsWith("i")); // false
console.log(str.startsWith("bye", 4)); // false
```

-   `endsWith`: We can check whether a string ends with a certain series of characters. We can also pass a second parameter as to where to check that string from backwards.

```js
const str = "goodbye";
console.log(str.endsWith("bye")); // true
console.log(str.endsWith("good", str.length - 3)); // true
```

-   `includes`: That's very similar to start with or ends with except you don't need to check the start or the end of the sentence or the string we just check the entire string to see if it contains that series of letters that you're specifying

```js
const str = "My name is Tom";
console.log(str.includes("name")); // true
```

## Object Literal Enhancement

-   In es6 we don't need to explicitly define the key value pair if the `key` and the variable storing that keys data has same name as the `key`.
-   Also there is a new cleaner way to define our methods on these objects in `es6`.

```js
let name = "Tom";
let age = 20;

let ninja = {
    name: name,
    age: age,
    chop: function (x) {
        console.log("You chopped the ememy " + x + " times.");
    },
};
// Also allowed
let ninja = {
    name,
    age,
    chop(x) {
        console.log(`You chopped the ememy ${x} times.`);
    },
};
```

## Arrow Functions

-   In `es6` we can write our functions and a slightly different using `arrow functions`

```js
const greet = (name) => {
    console.log(`Good Day ${name}!`);
};
greet("Sahil"); // Good Day Sahil!
```

## Sets

* So sets are a new data structure that we can use in `es6` and we can use them to store a set of unique values of whatever type you want.
```js
let names = new Set();

// add elements to set
names.add("Tom").add("Tony").add("Steve");
console.log(names); // Set {"Tom", "Tony", "Steve"}

// delete a element
names.delete("Tom"); //returns true if success

// to check size of set
names.size;

// to check if set has a element
names.has("Tony"); // returns true

// to clear set
names.clear();
```
* Sets can be used to remove duplicates in arrays
```js
let names = ["Tom", "Tony", "Steve", "Tom", "Tony"] //array with duplicates
let filteredNames = new Set(names);
names = [...filteredNames];
console.log(names); // ["Tom", "Tony", "Steve"]
```

## Generetors

* Generators are basically just functions which we can play and pause whenever we want so that we can have ultimate control over the flow of them.
```js
// normal functions
function gen() {
    console.log("Pear");
    console.log("Banana");
    console.log("Apple");
}
gen(); // Pear Banana Apple
```

```js
// generator function
function* gen() {
    console.log("Pear");
    console.log("Banana");
    console.log("Apple");
}
gen(); // logs nothing
```
* So in above example when can create a generator function by using `*` after the function keyword - `function*`
* When we first call it it is not actually firing the code all it's doing is setting up the generator. And what that does to us is returns us an `iterator`. So what we can do is store that iterator in a variable.
 ```js
// generator function
function* gen() {
    console.log("Pear");
    console.log("Banana");
    console.log("Apple");
}
let myGen = gen();
```
* We can iterate through a cycle of things by using the `next` method. So this now has the next method which we can use and that's what we're going to do to start playing this function.
 ```js
// generator function
function* gen() {
    console.log("Pear");
    console.log("Banana");
    console.log("Apple");
}
let myGen = gen();
myGen.next() // Pear Banana Apple 
```
* So `next()` is essentially the play button for us.
* We can also pause these generator functions. We do that using the `yield` keyword and we just place the `yield` keyword anywhere in the generator where we want to pause execution of the code.
 ```js
// generator function
function* gen() {
    yield console.log("Pear");
    console.log("Banana");
    console.log("Apple");
}
let myGen = gen();
myGen.next() // Pear
myGen.next() // Banana Apple 
```

 ```js
// generator function
function* gen() {
    let x = yield "Pear";
    let y = yield "Banana";
    let z = yield "Apple";
    return x+y+z;
}
let myGen = gen();
console.log(myGen.next());  // calls yield "Pear" and pauses, 
                            // Note at this  stage x is still undefined
console.log(myGen.next(10)); // here we pass 10 in next
                            // so it resumes the code where it was paused
                            // also sets x = 10
console.log(myGen.next(5)); // here we pass 5 in next
                            // so it resumes the code where it was paused
                            // also sets y = 5
console.log(myGen.next(3)); // here we pass 3 in next
                            // so it resumes the code where it was paused
                            // also sets y = 3
```
