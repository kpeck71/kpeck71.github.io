---
layout: post
title:      "Hoisting and Scope"
date:       2018-08-06 19:12:28 -0400
permalink:  hoisting_and_scope
---


// Blog Post - What is hoisting and what is Scope?
// examples of how var, let, const hoist and their Scope
// function() vs function named()
// arrow functions -> this
 
 
** What is Hoisting?**
Hoisting is a default behavior in JavaScript that puts function/variable declarations in to memory before any code is executed. Hoisting is related to two phases that occur when a JavaScript file loads - **compilation** and **execution**.
When your code is **compiled**, your variable and function declarations are saved in memory. (Nothing is physically 'hoisted' to the top of your code, the declarations stay where they are, but they are being evaluated before the remainder of your code is executed.) During this first phase, initializations are *not* hoisted. 

Here is an example of this from [MDN web docs](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) 
```
var x = 1; // Initialize x
console.log(x + " " + y); // '1 undefined'
var y = 2; // Initialize y

// The above example is implicitly understood as this: 
var x = 1; // Initialize x
var y; // Declare y
console.log(x + " " + y); // '1 undefined'
y = 2; // Initialize y
```

**Why does hoisting matter?**

Hoisting matters because it allows variables, functions, and other datatypes to be **initialized and used before they are declared **. 

Here is an example:

```
cheeseName("muenster");  
// Here we are using our function, but it only gets declared in the following lines. Still, the code works

function cheeseName(name) {
  console.log("My favorite cheese  is " + name);
}
/*
The code above successfully writes "My favorite cheese is muenster" to the console
*/
```

To help avoid confusion and conflicts: 
* **declare your functions at the top of your code. **
* **Use let and const** (more on this below)


**What is Scope? **
 
Scope refers to the part of a program where a particular variable is accessible. The scope is determined by where you declare that variable. In JavaScript, there are two types of scope: global and local scope. If a variable is declared outside of a function or block (aka between curly braces, like an if/else statement), it has global scope, and can be accessed anywhere in your code. Within local scope, you can have function scope and block scope, and the variable will only be available within that function or block.

In JavaScript, variables declared with the keyword **var** have global scope, no matter where they are declared. This can lead to issues like naming collisions and make your code harder to debug. 
 
Declare variables with const as your default, and then adjust from there. As a newbie, I was using 'var' all over the place because, hey, it worked! But I now default to 'const' because it will throw an error if an attempt is made to change its value (**Note**: you *can* mutate the value of an array or object, but can't reassign it to something else [Link](https://hackernoon.com/why-you-shouldnt-use-var-anymore-f109a58b9b70))

**Why var and let are not equal**

Though var and let may seem to be interchangeable, they definitely are not:
```let``` declarations are not hoisted in a block scope. (A block scope is anything that falls between curly braces.)
```let``` and ```const``` have a block scope but ```var``` has a function scope.

Here is a good example from the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
```
function varTest() {
  var x = 1;
  if (true) {
    var x = 2;  // same variable!
    console.log(x);  // 2
  }
  console.log(x);  // 2
}

function letTest() {
  let x = 1;
  if (true) {
    let x = 2;  // different variable
    console.log(x);  // 2
  }
  console.log(x);  // 1
}
```

Another important hoisting difference between let and var, again from the same MDN docs, is:
> let bindings are created at the top of the (block) scope containing the declaration, commonly referred to as "hoisting". Unlike variables declared with var, which will start with the value undefined, let variables are not initialized until their definition is evaluated. Accessing the variable before the initialization results in a ReferenceError. The variable is in a "temporal dead zone" from the start of the block until the initialization is processed.

And here is one great visualization about var, let, and const from Mariko Kosaka @kosamari on Twitter: https://pbs.twimg.com/media/CzLVVjtXAAERmbc.jpg

![https://twitter.com/kosamari/status/806941856777011200](https://pbs.twimg.com/media/CzLVVjtXAAERmbc.jpg)


**Named and Anonymous Functions**

Function Declaration or Function Statement:
```
function myFunction() {
//code goes here
}
```

Functional Expression - this can be a named or an anonymous function:
```
var myFunction = function() {
// code goes here
}
```
Anonymous functions are often used for callbacks:
```
button.addEventListener('click', function(event) {
    console.log('button is clicked!')
})
```

The functional difference between function expression and function declaration? 
A **function declaration is hoisted** so you can use that function before it is declared.

A **function expression is not hoisted**, the variable will be hoisted but not the function. It won't know that the variable is pointing to a function at all.

One benefit of using a named function? They can make it easier to debug your code. 


**Arrow Functions**

From the MDN docs:
> An arrow function expression has a shorter syntax than a function expression and does not have its own this, arguments, super, or new.target. These function expressions are best suited for non-method functions, and they cannot be used as constructors.
> 

Arrow functions are a helpful shorthand to make anonymous functions, and can be used anywhere the `function` keyword is used

Here is how you would write an anonymous function and assign it to a variable:

```
var myFunction = function() {
// code goes here
}
```
And here is how you would sub in an arrow function:
```const myFunction = (arg1, arg2) => {/* code goes here */}```

You can use an anonymous function in a callback:
```
button.addEventListener('click', function() {
  // code goes here
})
```

Or, arrow-ize it like so:
```
button.addEventListener('click', () => { 
code goes here  
})
```

Arrow functions also, by default, create a return value if the code is one line long and isn't in a block. Here are some examples of this 'consice body syntax' with a implicit return value:

```const sum = (num1, num2) => num1 + num2```
```let moreThan20 = array.filter(num => num > 20)```
[Source](https://zellwk.com/blog/es6/#arrow-functions)

With these features, arrow functions let you write shorter and clearer code (once you understand the syntax) when used appropriately. 

**Arrow Functions and lexical ```this```**
The value of ```this``` is normally defined by the function that calls it. So if you have an object method, the ```this``` keyword inside the method would refer to the object.

Arrow functions, on the other hand, do not have their own ```this```; instead,  ```this``` refers to the current surrounding execution scope, and not to the object method or the object itself.

Thus, in the following code, the `this` within the function that is passed to setInterval has the same value as this in the enclosing function:
```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| properly refers to the Person object
  }, 1000);
}

var p = new Person();
```
[Source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

> The methods call(), apply(), and bind() will not change the value of this in arrow functions. (In fact, the value of this inside a function simply can’t be changed; it will be the same value as when the function was called.) If you need to bind to a different value, you’ll need to use a function expression.[Source](https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/)

Here is a handy [flowchart from Kyle Simpson](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20%26%20beyond/fig1.png) about when to use an arrow function.


