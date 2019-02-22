# Arrow Function Shorthand

## Introduction

The original style for declaring functions in JavaScript is the _function
declaration_.

```js
function foo() {
  return 'bar';
}
```

But JavaScript has two other ways to write functions: the _function expression_
and the _arrow function_. None of these is more correct or better than others,
but learning to recognize the correct situation in which to use each is a useful
skill for a programmer.

## Learning Goals

- Declare a function using a function expression
- Declare a function using an arrow function
- Describe situations where arrow functions are used

## Declare a Function Using a Function Expression

Thus far we've only ever used a _function declaration_:

```js
function foo() {
  return 'bar';
}
```

A function can also be written:

```js
let foo = function() {
  return 'bar';
}
```

The `function() {...}` to the right of the assignment operator (`=`) is called
a _function expression_. The best way to understand what a function expression
is is by analogy.

```js
let sum = 1 + 1
```

Evaluate the expression `1 + 1`, returning `2` and assign it to the variable `sum`

```js
let difference = 10 - 1;
```

Evaluate the expression `10 - 1`, returning `9` and assign it to the variable
`difference`.

```js
let foo = function() {
  return 'bar';
}
```

Evaluate the expression `function() { return 'bar' }`, returning a thing that
can be called and assign it to the variable `foo`. The function expression
(again, the thing to the right of `=`) is known as "an anonymous
function." It doesn't have a name associated with it like you see in a
_function declaration_.

However, when we assign an anonymous function to a name (that is, a variable),
we have name that points to a callable thing. We could call this anonymous
function by invoking `foo()`. That anonymous function is now, for all
reasonable purposes, named `foo`.

There are a few subtle differences between _function declarations_ and
_function expressions_, but they are very minute. Neither is really better than
the other. JavaScript supports variety, and you can use whichever one you
prefer. In advanced usage (in React, in particular) some subtle differences
will become important, but for the time being you don't need to consider those
differences.

Try thinking about the following code. Will this work? Does it work? Try to
explain to yourself what's happening using the words "anonymous function" and
"`call`." If you need help, see [Immediately Invoked Function Expression][IIFE]
in the Resources section below.

```js
(function() { console.log("Hello world") })()
```

## Declare a Function Using An Arrow Function

Around 2015, developers got tired of typing `f-u-n-c-t-i-o-n` over and over.
They lobbied the ECMAScript body for a way to write functions in a very short
way. Here is the result, the "Arrow Function."

```js
let add = (parameter1, parameter2) => parameter1 + parameter2
add(2,3) //=> 5
```

It seems like it wouldn't work, but it does. This builds on the syntax of the _function expression_
just covered. The arrow syntax just lets you cut out some typing.

`add` is the name to which the following _anonymous function_ is assigned, same
as in the previous section:

```js
(parameter1, parameter2) => parameter1 + parameter2
```

This is a very short function! It defines two parameters inside of `()`. It defines
a function body after the "arrow" (`=>`). If the _function body_ is only one line,
the function **automatically returns** the value of the single evaluated expression.
In this function body, it returns the result of adding adds `parameter1` and
`parameter2`.

It is equivalent to:

```js
function (parameter1, parameter2) {
  return parameter1 + parameter2;
}
```

Functions like this are very common in JavaScript's _iterator_ methods. An
iterator is a method that allows you to deal with a set of data one at a time.
For example, if you had a group of student's essays, you could only grade
them one at a time. An iterator method would allow you to do just that.

You'll be working with iterator methods a lot in later exercises in this
module.

If your arrow function has only one parameter, the `()` become optional around the parameter:

```js
let twoAdder = (x) => x + 2;
// is the same as
let twoAdder = x => x + 2;
```
Almost all developers will drop the parentheses in this case.

If we need to do more work than return a mere single expression, we'll need
`{}` to wrap the multiple lines of code, and we'll have to declare a
`return`.

```js
let sum = (parameter1, parameter2) => {
  console.log(`Adding ${parameter1}`);
  console.log(`Adding ${parameter2}`);
  return parameter1 + parameter2;
}
sum(1,2) //=> 3
```

## Describe Situations Where Arrow Functions Are Used

As a preview of advanced iteration in JavaScipt, we'll show the `.map()`
method.  `.map()` iterates through one `Array`, passes each element to a
function that's passed in as an argument, takes that functions return value, and
stacks it into a new array. Don't worry if you don't completely follow
everything that goes on here - we haven't covered iterators quite yet, so it's
totally ok if the finer details feel a bit murky.

```js
const nums = [1,2,3];
const squares = nums.map(x => x ** 2); //=> [2,4,6]
const doubles = nums.map(x => x * 2); //=> [1,4,9]
```

If all this math stuff seems a bit too textbook-y, be reassured that we can
iterate through anything, not just numbers. We can do something similar with DOM
elements:

```js
finishedItems = overdueTodoItems.map( item => item.className = "complete" );
header.innerText = `You finished ${finishedItems.length} items!`;
```

Or billing software:

```js
lapsedUserAccounts.map( u => sendBillTo(u.address) );
```

## Instructions
You are going to write several methods. Write your code in the `index.js` file.
Let the tests guide you through the process.


## Conclusion

In this lesson you saw two different styles for declaring functions: function
expressions and arrow functions. Neither is "better" than the standard function
declaration we've been using. Arrow functions excel when a simple change or
operation needs to be used repeatedly. But they're certainly used to write long,
full functions too! As you continue through the course, you'll see all three
methods used to write functions, and develop a sense of when to use each
yourself.

## Resources

* [MDN: Arrow Functions][Arrow functions]
* [IIFE][]

[Arrow functions]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
[IIFE]: https://developer.mozilla.org/en-US/docs/Glossary/IIFE