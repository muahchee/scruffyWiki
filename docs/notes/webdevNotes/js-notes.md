:material-language-javascript: Javascript notes
========================

## Creating unique values with Symbol()

[MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)

A built-in object that returns a Symbol value that guarantees to be unique. Symbols are primitives (like strings or boolean).

> Symbols are often used to **add unique property keys** to an object that won't collide with keys any other code might add to the object, and which are hidden from any mechanisms other code will typically use to access the object.

This could be useful for the to-do list project! I could generate unique ids with this! 

---

## Closures

[The Odin Project lesson](https://www.theodinproject.com/lessons/node-path-javascript-factory-functions-and-the-module-pattern#closures-arent-scary)

[Javascript closure video by Bro Code](https://www.youtube.com/watch?v=80O6L2Ez3GM)

> Closures are functions with preserved data. 

> Gives you access to an outer function's scope from an inner function.

> State of variables in the outer scope is "saved"

> Variables in outer scope are considered "private" (i.e cannot be access from global scope)

```
//--outer function--
let score = (function(){

    let points = 0;
    
    //--inner function--
    return function(){
    
        points += 1;
        return points;
        
    }
    
})(); //iife
```

[Wes Bos' article on closures](https://wesbos.com/javascript/03-the-tricky-bits/closures)

You can also use closures to make "two layer function calls" (idk what to call it)

```
function createGreeting(greeting = "") {

  const myGreet = greeting.toUpperCase();
  
  return function(name) {
    return `${myGreet} ${name}`;
  };
  
}
```
First, invoke outer function and store the inner function in the variable `sayHello`.

`sayHello` has preserved the outer function's `myGreet` (which has the value of "HELLO")

Then, invoke the inner function that was stored in `sayHello`in the `console.log`

```
const sayHello = createGreeting('hello');

console.log(sayHello('wes')); //HELLO wes

const sayBye = createGreeting('bye');

console.log(sayBye('xuan')); //BYE xuan
```
---
