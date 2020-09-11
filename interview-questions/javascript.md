---
description: >-
  https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/src/questions/javascript-questions.md
---

# JavaScript

### Explain event delegation

Event delegation is when a group of HTML tags _delegate/give_  to their parent the responsibility of listening for events fired from them. For example, a bunch of `li` inside a `ul` can fire events that are listened by an event listener in the `ul` tag. This is particular important if the items in the group will keep changing. Also, it's cleaner, and maybe more performance, because we don't have a lot of event listeners registered. It can also be easier to test. 

* [https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building\_blocks/Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
* [https://davidwalsh.name/event-delegate](https://davidwalsh.name/event-delegate)

### Describe event capturing & Describe event bubbling

When an event is fired in the browser it starts a _lifecycle_ with 2 phases: capturing and bubbling. Capturing is a top-down phase. The browser starts from the HTML tag and check if there's an event listener registered for the event, if there's one, then the browser invokes it. Then the browser goes to the first child tag of the HTML tag, and so on until it reaches the tag that fired the event.

The bubbling phase is the inverse of the capturing phase. The browser starts with the element that fired the event, checks if there's an event handler registered, it invokes it, then it goes to the immediate parent tag and does the some. All the up to the HTML tag.

The two phases exist for historical reasons.

When event listeners are registered the default behaviour is to run then on the bubbling phase. In order to run event handlers in the capturing phase, we need to use `addEventListener` and pass true as the third argument.

`stopPropagation` method of the event object is used to stop the bubbling phase of the event, which means that only the event handler where stopPropagation is called will be invoked. Event handlers in parent tags will run. 



### Explain how prototypal inheritance works.

JavaScript has only one construct that can be used for inheritance and this construct is an object. Each object in JavaScript has a special property called prototype. This property is a link to the object used to create another object. For example:

```text
const myFunc = function() {};

const anInstance = new myFun();

// anInstance.prototype --> myFunc.prototype --> Object.prototype --> null
```

Here `anInstace` was create from `myFun`, therefore its prototype "points" to myFunc. In turn, `myFunc`'s prototype points to Object which sits on the top of the prototype chain. By convention, Object has prototype null. When a property of an object is accessed, JavaScript will first check if the property is present in the object itself, if not, it will use the prototype property of the object and check its "parent", if it's not there it will use the prototype property of the parent to go to the grand-parent object and so on until the property is found or the chain is finished. 

* `[[Prototype]]` is the standard notation to describe the prototype of an object.
* _own properties:_ are properties that belong to the object and not to one of its prototypes, i.e., properties that were defined when the object was created and not in one of its ancestor's
* functions can be properties of objects and behave in the same way as other properties. When an inherited function is executed the value of the `this` keyword refers to the inheriting object and not its prototype.
* All functions have a property called prototype, except arrow functions. It specifies the`[[Prototype]]` to be assigned to all instances of the function created by the new keyword. 
* `__proto__` is non-standard but it's a property that browsers have implemented to access the prototype of objects. 
* Methods to create objects
  * with a constructor
    * a constructor is a function that is called with the new operator
  * Object.created
    * introduced in ES5. 
    * It creates a new object and set the prototype to the object passed as an argument
  * with the class keyword



* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance\_and\_the\_prototype\_chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

### --------------------------------

### TODO:

* Explain how `this` works in JavaScript.
  * Can you give an example of one of the ways that working with `this` has changed in ES6?
* Explain how prototypal inheritance works.
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
* What language constructions do you use for iterating over object properties and array items?
* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
* What's a typical use case for anonymous functions?
* What's the difference between host objects and native objects?
* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
* Explain `Function.prototype.bind`.
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain "hoisting".
* What's the difference between an "attribute" and a "property"?
* What are the pros and cons of extending built-in JavaScript objects?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
* What is strict mode? What are some of the advantages/disadvantages of using it?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* What are the differences between variables created using `let`, `var` or `const`?
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
* Can you give an example of generating a string with ES6 Template Literals?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
* What is the difference between `while` and `do-while` loops in JavaScript?
* What is a promise? Where and how would you use promise?



