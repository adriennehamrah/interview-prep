# Javascript Concepts

## Functional Programming
- Build software with pure functions -> avoids shared states, mutable data, side-effects
- Type of programming paradigm (e.g., OOP, procedural programming)
- Declarative over imperative
  - Declarative programming expresses logic, without specifying control flow. Looks at data flow. - WHAT
    - Uses expressions (piece of code that evaluates to value) over statements (if, for, switch) 
  - Imperative programming uses statements that change a program's state. - HOW
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
  - Side effects are any app state change observable outside the function other than its return value
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
  - Functor - something that can be mapped over
    - e.g. Array container


#### Reference

[What is Functional Programming?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)
