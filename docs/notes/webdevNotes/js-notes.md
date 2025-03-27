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

## [Airbnb style guide notes](https://github.com/airbnb/javascript)

### [11.1 Dont use iterators](https://github.com/airbnb/javascript?tab=readme-ov-file#iterators--nope)

like `for-in` / `for-of` / `for` loops

Use `map()` /` every()` / `filter()` / `find() `/ `findIndex()` / `reduce()` / `some(`) / `...` to iterate over arrays.

And `Object.keys()` / `Object.values()` / `Object.entries()` to produce arrays so you can iterate over objects.

```
const numbers = [1, 2, 3, 4, 5];

// bad
let sum = 0;
for (let num of numbers) {
  sum += num;
}
sum === 15;

// good
let sum = 0;
numbers.forEach((num) => {
  sum += num;
});
sum === 15;

// best (use the functional force)
const sum = numbers.reduce((total, num) => total + num, 0);
sum === 15;

// bad
const increasedByOne = [];
for (let i = 0; i < numbers.length; i++) {
  increasedByOne.push(numbers[i] + 1);
}

// good
const increasedByOne = [];
numbers.forEach((num) => {
  increasedByOne.push(num + 1);
});

// best (keeping it functional)
const increasedByOne = numbers.map((num) => num + 1);
```

### [Hoisting](https://github.com/airbnb/javascript?tab=readme-ov-file#hoisting)

the variable gets pushed up not the value (for `var`), not the case for `let` and `const`.
`let` and `const` are still hoisted but they are in a [Temporal Dead Zone](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz) where JavaScript knows they exist (declaration is hoisted) but they are not accessible (as they are not yet initialized).

```
// creating a variable declaration after you
// reference the variable will work due to
// variable hoisting. Note: the assignment
// value of `true` is not hoisted.
function example() {
  console.log(declaredButNotAssigned); // => undefined
  var declaredButNotAssigned = true;
}

// using const and let
function example() {
  console.log(declaredButNotAssigned); // => throws a ReferenceError
  console.log(typeof declaredButNotAssigned); // => throws a ReferenceError
  const declaredButNotAssigned = true;
}
```

Anonymous function expressions hoist their variable name, but not the function assignment.

```
function example() {
  console.log(anonymous); // => undefined

  anonymous(); // => TypeError anonymous is not a function

  var anonymous = function () {
    console.log('anonymous function expression');
  };
}
```

Variables, classes, and functions should be defined before they can be used.

### [Comparison Operators & Equality](https://github.com/airbnb/javascript?tab=readme-ov-file#comparison-operators--equality)

Objects evaluate to true

Strings evaluate to false if an empty string '', otherwise true

```
if ([0] && []) {
  // true
  // an array (even an empty one) is an object, objects will evaluate to true
}
```

The nullish coalescing operator (`??`) is a logical operator that returns its right-hand side operand when its left-hand side operand is `null` or `undefined`. Otherwise, it returns the left-hand side operand.

```
// bad
const value = 0 ?? 'default';
// returns 0, not 'default'

// bad
const value = '' ?? 'default';
// returns '', not 'default'

// good
const value = null ?? 'default';
// returns 'default'

// good
const user = {
  name: 'John',
  age: null
};
const age = user.age ?? 18;
// returns 18
```

### Blocks

If an `if` block always executes a `return` statement, the subsequent `else` block is unnecessary. A return in an `else if` block following an `if` block that contains a `return` can be separated into multiple `if` blocks.

```
// bad
function foo() {
  if (x) {
    return x;
  } else {
    return y;
  }
}

// good
function foo() {
  if (x) {
    return x;
  }

  return y;
}

// bad
function cats() {
  if (x) {
    return x;
  } else if (y) {
    return y;
  }
}

// good
function cats() {
  if (x) {
    return x;
  }

  if (y) {
    return y;
  }
}

// bad
function dogs() {
  if (x) {
    return x;
  } else {
    if (y) {
      return y;
    }
  }
}

// good
function dogs(x) {
  if (x) {
    if (z) {
      return y;
    }
  } else {
    return z;
  }
}
```

### [Comments](https://github.com/airbnb/javascript?tab=readme-ov-file#comments)

Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you’re pointing out a problem that needs to be revisited, or if you’re suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are `FIXME: -- need to figure this out` or `TODO: -- need to implement`.

Use `// FIXME:` to annotate problems.

Use `// TODO:` to annotate solutions to problems.




