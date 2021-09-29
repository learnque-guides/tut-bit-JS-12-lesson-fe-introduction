# Object creation - prototypal pattern

In a purely prototypal pattern, we dispense with classes. We focus instead on the objects. Prototypal inheritance is conceptually simpler than classical inheritance: a new object can inherit the properties of an old object. This is perhaps unfamiliar, but it is really easy to understand.

```js
var myMammal = {
    name : 'Herb the Mammal',
    getName : function (  ) {
        return this.name;
    },
    says : function (  ) {
        return this.saying || '';
    }
};

// Inheritance
var myCat = Object.create(myMammal);
myCat.name = 'Henrietta';
myCat.saying = 'meow';
myCat.purr = function (n) {
    var i, s = '';
    for (i = 0; i < n; i += 1) {
        if (s) {
            s += '-';
        }
        s += 'r';
    }
    return s;
};
myCat.getName = function (  ) {
    return this.says() + ' ' + this.name + ' ' + this.says();
};
```