# Array literals, element deletion, enumaration

Array literals provide a very convenient notation for creating new array values. An array literal is a pair of square brackets surrounding zero or more values separated by commas.

```js
var empty = [];
var numbers = [
    'zero', 'one', 'two', 'three', 'four',
    'five', 'six', 'seven', 'eight', 'nine'
];

empty[1]          // undefined
numbers[1]        // 'one'

empty.length      // 0
numbers.length    // 10
```

You can remove element from array by using:

```js
var numbers = [
    'zero', 'one', 'two', 'three', 'four',
    'five', 'six', 'seven', 'eight', 'nine'
];

numbers.splice(2, 1);

console.log(numbers);
```

You can enumerate elements of array:

```js
var i;
for(i = 0; i < numbers.length; i += 1) {
    console.log(numbers[i]);
}

numbers.forEach(function(item, index) {
  console.log(item, index);
});

for(const idx in numbers) {
  console.log(numbers[idx]);
}

for(const number of numbers) {
  console.log(number);
}
```

Let's play around with `shift`, `unshift`, `slice`, `join`, `indexOf`, `sort` methods.