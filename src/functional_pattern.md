# Object creation - functional pattern

One weakness of the inheritance patterns we have seen so far is that we get no privacy. All properties of an object are visible. We get no private variables and no private methods. Sometimes that doesn't matter, but sometimes it matters a lot.

We start by making a function that will produce objects in 4 steps:
* It creates a new object. There are lots of ways to make an object. It can make an object literal, or it can call a constructor function with the new prefix, or it can use the Object.create method to make a new instance from an existing object, or it can call any function that returns an object.
* It optionally defines private instance variables and methods. These are just ordinary vars of the function.
* It augments that new object with methods. Those methods will have privileged access to the parameters and the vars defined in the second step.
* It returns that new object.

```js
var constructor = function (spec, my) {
    var that, other private instance variables;
    my = my || {};

    Add shared variables and functions to my

    that = a new object;

    Add privileged methods to that

    return that;
};
```

Example:

```js
var mammal = function (spec) {
    var that = {};

    that.getName = function (  ) {
        return spec.name;
    };

    that.says = function (  ) {
        return spec.saying || '';
    };

    return that;
};

var myMammal = mammal({ name: 'Herb' });


Functional
One weakness of the inheritance patterns we have seen so far is that we get no privacy. All properties of an object are visible. We get no private variables and no private methods. Sometimes that doesn't matter, but sometimes it matters a lot. In frustration, some uninformed programmers have adopted a pattern of pretend privacy. If they have a property that they wish to make private, they give it an odd-looking name, with the hope that other users of the code will pretend that they cannot see the odd looking members. Fortunately, we have a much better alternative in an application of the module pattern.

We start by making a function that will produce objects. We will give it a name that starts with a lowercase letter because it will not require the use of the new prefix. The function contains four steps:

It creates a new object. There are lots of ways to make an object. It can make an object literal, or it can call a constructor function with the new prefix, or it can use the Object.create method to make a new instance from an existing object, or it can call any function that returns an object.

It optionally defines private instance variables and methods. These are just ordinary vars of the function.

It augments that new object with methods. Those methods will have privileged access to the parameters and the vars defined in the second step.

It returns that new object.

Here is a pseudocode template for a functional constructor (boldface text added for emphasis):

var constructor = function (spec, my) {
    var that, other private instance variables;
    my = my || {};

    Add shared variables and functions to my

    that = a new object;

    Add privileged methods to that

    return that;
};
The spec object contains all of the information that the constructor needs to make an instance. The contents of the spec could be copied into private variables or transformed by other functions. Or the methods can access information from spec as they need it. (A simplification is to replace spec with a single value. This is useful when the object being constructed does not need a whole spec object.)

The my object is a container of secrets that are shared by the constructors in the inheritance chain. The use of the my object is optional. If a my object is not passed in, then a my object is made.

Next, declare the private instance variables and private methods for the object. This is done by simply declaring variables. The variables and inner functions of the constructor become the private members of the instance. The inner functions have access to spec and my and that and the private variables.

Next, add the shared secrets to the my object. This is done by assignment:

my.member = value;
Now, we make a new object and assign it to that. There are lots of ways to make a new object. We can use an object literal. We can call a pseudoclassical constructor with the new operator. We can use the Object.create method on a prototype object. Or, we can call another functional constructor, passing it a spec object (possibly the same spec object that was passed to this constructor) and the my object. The my object allows the other constructor to share the material that we put into my. The other constructor may also put its own shared secrets into my so that our constructor can take advantage of it.

Next, we augment that, adding the privileged methods that make up the object's interface. We can assign new functions to members of that. Or, more securely, we can define the functions first as private methods, and then assign them to that:

var methodical = function (  ) {
    ...
};
that.methodical = methodical;
The advantage to defining methodical in two steps is that if other methods want to call methodical, they can call methodical( ) instead of that.methodical( ). If the instance is damaged or tampered with so that that.methodical is replaced, the methods that call methodical will continue to work the same because their private methodical is not affected by modification of the instance.

Finally, we return that.

Let's apply this pattern to our mammal example. We don't need my here, so we'll just leave it out, but we will use a spec object.

The name and saying properties are now completely private. They are accessible only via the privileged get_name and says methods:

var mammal = function (spec) {
    var that = {};

    that.get_name = function (  ) {
        return spec.name;
    };

    that.says = function (  ) {
        return spec.saying || '';
    };

    return that;
};

var myMammal = mammal({name: 'Herb'});

var cat = function (spec) {
    spec.saying = spec.saying || 'meow';
    var that = mammal(spec);
    that.purr = function (n) {
        var i, s = '';
        for (i = 0; i < n; i += 1) {
            if (s) {
                s += '-';
            }
            s += 'r';
        }
        return s;
    };
    that.getName = function () {
        return that.says() + ' ' + spec.name + ' ' + that.says();
    };
    return that;
};

var myCat = cat({name: 'Henrietta'});
```