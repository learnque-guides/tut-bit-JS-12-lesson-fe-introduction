# Object creation - modern way by using class keywoard

Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics.

```js
class Mammal {
  constructor(name) {
    this.name = name;
  }

  getName() {
    return this.name;
  }

  says() {
    return this.saying || '';
  }
}

class Cat extends Mammal {
  constructor(name) {
    super(name);
    this.saying = 'meow';
  }

  getName() {
    return this.says() + ' ' + this.name + ' ' + this.says();
  }

  purr() {
    let i, s = '';
    for (i = 0; i < n; i += 1) {
      if (s) {
          s += '-';
      }
      s += 'r';
    }
    return s;
  }
}

const cat = new Cat("Henrieta");

console.log(cat.getName());
```