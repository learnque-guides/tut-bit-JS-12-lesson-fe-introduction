# Array/Object operators (ES6)

```js
const numbers = [1, 2, 3];
const oddNumber = numbers.find((x) => x % 2 === 1);
console.log(oddNumber); // 1
const oddNumberIndex = numbers.findIndex((x) => x % 2 === 1);
console.log(oddNumberIndex); // 0
let fruits = ['Apple', 'Orange', 'Banana'];
let newFruitArray = [...fruits]; // copy of array
let arr1 = ['A', 'B', 'C'];
let arr2 = ['X', 'Y', 'Z'];
let result = [...arr1, ...arr2]; // sum of arra􏰁s
const obj = { hello: '1', world: '2' };
const { hello, world } = obj; // destructed object
arr1.sort();
// etc.
```

In JavaScript operator `...` is called spread operator :)