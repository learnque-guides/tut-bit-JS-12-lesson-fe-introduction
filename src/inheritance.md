# Object creation - function constructor pattern

Object creation and inheritance can be implemented by using *constructor invocation pattern*:

```js
// Constructor
function Mammal(name) {
    this.name = name;
}

// Getter method
Mammal.prototype.getName = function() {
    return this.name;
}

// Behiavour method
Mammal.prototype.says = function (  ) {
    return this.saying || '';
};

var myMammal = new Mammal('Herb the Mammal');
var name = myMammal.getName();

var Cat = function (name) {
    this.name = name;
    this.saying = 'meow';
};

// Replace Cat.prototype with a new instance of Mammal. 
// Something similiar to extends like in Java or C#?
Cat.prototype = new Mammal();

Cat.prototype.purr = function (n) {
    var i, s = '';
    for (i = 0; i < n; i += 1) {
        if (s) {
            s += '-';
        }
        s += 'r';
    }
    return s;
};

// Method overload
Cat.prototype.getName = function (  ) {
    return this.says() + ' ' + this.name + ' ' + this.says();
};

var myCat = new Cat('Henrietta');
var says = myCat.says(); // 'meow'
var purr = myCat.purr(5); // 'r-r-r-r-r'
var name = myCat.getName(); // 'meow Henrietta meow'
```
