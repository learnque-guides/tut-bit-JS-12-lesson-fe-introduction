# Scope, closure partial apply and scope binding

*Scope* in a programming language controls the visibility and lifetimes of variables and parameters.

When we are talking about sope it is important to understand:
* Closure of scope.
* Scope binding.

Closure can be defined as pass of outer function scope to inner function scope:

```js
function increment(a) {
    function add(a, b) {
        return a + b;
    }

    return add(a, 1);
}
```

or even better:

```js
function incrementBy(a) {
    // Function without a name is called anonymous function
    return function add(b) {
        return a + b;
    }
}

// Such form of function arguments applying is called partial apply
// Process when a function produce a new one is also called currying.
incrementBy(5)(2);
```

*Functions are values, and we can manipulate function values in interesting ways. Currying allows us to produce a new function by combining a function and and argument.*

It is possible to pass `this` (or any other outer) scope to function by using `Function.prototype.bind` function:

```js
function Game({ level = 0, mode = 'demo' }) {
  this.level = level;
  this.mode = mode;
}

function inspectGame() {
  console.log(this.level + " - " + this.mode);
}

console.log(inspectGame());

var bindGame = inspectGame.bind(new Game({ level: 1, mode: 'demo' }));

console.log(bindGame());
```