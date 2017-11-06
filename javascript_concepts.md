# JavaScript Concepts

## Pure Functions
- Given the same input, will always return the same output
- Produces no side effects

### Use Cases
- Form the foundation of functional programming
- Parallel processing across many CPU's and distributed computer clusters
  - Good for resource intensive computing tasks

#### Reference
[What is a Pure Function?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)

## Closures
- "A closure is the combination of a function and the lexical environment within which that function was declared." - MDN web docs
- Lexical environment - the surrounding state
- Closures give you access to the outer function's scope from the inner function.
- In javascript, you create a closure everytime you create a function.
- To use a closure, create a function inside another function and expose it by returning or passing to another function.
  - The inner function has access to the other functions variables even after the outer function returns.
### Use Cases
- Data Privacy 
  - Enclosed variables are only accesible within the containing outer function.
  - You can only get the data from an object's privileged methods.
    - **Priviledged method** - any exposed method defined within the closure scope
  - Stateful functions - return values may influenced by their internal state
- Partial Applications & Currying
  - **Partial Application** - The process of applying a function to some of its arguments.
    - Takes in a function multiple parameters and returns a function with fewer parameters
    - The partially applied function gets returned for later use
    - May or may not have predictable return type
  - **Currying** - Takes in a function with multiple parameters, return a function with just one parameter.
    - Lifts all arguments for function type uniformity - e.g. function composition
    - Built in iterator mechanism - apply only one argument at a time
  - Takes advantage of closure scope to *fix* parameters
- Practical Applications 
  - Callbacks - e.g. commonly used in web - define a behavior that is attached to some event, usually triggered by the user.
#### References
[What is a closure?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)

[Closures - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)

## Functional Programming
- Build software with pure functions -> avoids shared states, mutable data, side-effects
- Type of programming paradigm (e.g., OOP, procedural programming)
- Declarative over imperative
  - **Declarative programming** expresses logic, without specifying control flow. Looks at data flow. - WHAT
    - Uses expressions (piece of code that evaluates to value) over statements (if, for, switch) 
  - **Imperative programming** uses statements that change a program's state. - HOW
- Favors pure functions
### Key Concepts
- Avoids Shared State issues such as:
  - Race condition
  - Order of function calls matter, as functions are timing dependent
- Immutability over mutable data
  - `const` is not immutable
    - Can't change obj that binding refers to, but can change obj properties -> mutable
  - `Object.freeze` - freezes only one level
  - Trie data structures - deep frozen
    - Uses structural sharing to share reference memory locations
- Reduces Side Effects
  - Side effects are any app state change observable outside the function other than its return value.
    - Modifying external variable
    - Console logging
    - Writing to a file or network
    - Triggering any external process
    - Calling other functions with side effects
- Reusability Through Higher Order Functions
  - Higher order function - takes a function as an arg, returns a func, or both
    - Abstract or isolate actions -> callbacks, promises, monads
    - Create util for acting on multiple data types
    - Curried functions
    - Function composition
      - The process of combining two or more functions to produce a new function
  - Functor - something that can be mapped over
    - e.g. Array container
#### References
[What is Functional Programming?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)

[Curry or Partial Application?](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8)

[What is Function Composition?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0)

## Promises
- A promise is an object that may produce a single value in the future. It can be returned synchronously from an asynchronous function.
- ES6 adopted global `Promise` with Promises/A+ spec
### Features
- Promises are eager - starts doing given task as soon as promise constructor is invoked
  - For lazy - use observables or tasks
- Guarantee about future value - unlike callbacks or events
  - Immutable - No other registered handlers of that value can change it. Can't be resettled.
  - No race conditions - Guaranteed to receive the value, regardless of whether handler is registered
- Can help with unifying asynchronous APIs
### Drawbacks
- Can't determine state of a promise or progress in state
- For recurring values/events use **streams**.
### Terminology
- Three states:
  - Fulfilled: `onFulfilled()` will be called (e.g., `resolve()` was called)
  - Rejected: `onRejected()` will be called (e.g., `reject()` was called)
  - Pending: not fulfilled or rejected
  - Settled: fulfilled or rejected
- Creating a promise:
```javascript
var p = new Promise((resolve, reject) => {
  // do a thing, possibly async, then…

  if (/* everything worked */) {
    resolve("It worked!");
  }
  else {
    reject(Error("It broke"));
  }
});
```
- To consume the promise, attach `.then()` - returns a new Promise
```javascript
p.then((val) => console.log("fulfilled:", val),  
       (err) => console.log("rejected:", err));
```
- `Promise.catch()` takes a single handler to be called when a promise is rejected
  - More explicit than `.then(null, fn)`
```javascript
p.then((val) => console.log("fulfilled:", val))  
 .catch((err) => console.log("rejected:", err));

p.then((val) => console.log("fulfilled:", val))  
 .then(null, (err) => console.log("rejected:", err));
```

- `Promise.resolve()` creates an immediately resolved Promise
- `Promise.reject()` creates an immediately rejected Promise
- `Promise.all()` takes an array (or any iterable) of Promises. Once all the Promises are resolved, it then resolves. Or it rejects with reason of first rejected Promise.
- `Promise.race()` takes an array (or any iterable) of Promises. It returns a Promise that resolves with the value of the first resolved promise in the iterable. Or it rejects with the reason of the first rejected Promise.

### Cancelling a Promise
- Reject the Promise with cancelled as the reason
- Don't add `.cancel()`
  - Non-standard and violates rule that only the creating function should change promise

#### Reference
[What is a Promise?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)

[JavaScript Promises: an Introduction](https://developers.google.com/web/fundamentals/primers/promises)

[ES6 Promises](http://www.datchley.name/es6-promises/)
