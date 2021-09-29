# Objects

Objects are used to describe a real life object by combining its properties and methods:
* Properties - define characteristics of object.
* Methods - define operations with current object.

The easiest way to define object in JavaScript is to use object literal:
* Object literal is defined using curly brackets {}

```js
const myHonda = {
    color: 'red',
    wheels: 4,
    engine: {
        cylinders: 4,
        size: 2.2 
    },
    getColor: function() { return this.color; }
};
console.log(myHonda.getColor());
```

Functions in JavaScript are objects. So it possible to create an object by using functions:

```js
function Game(level) {
    this.level = level;
}

Game.prototype.getLevel = function() {
    return this.level;
}
```