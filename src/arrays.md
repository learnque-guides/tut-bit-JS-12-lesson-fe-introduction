# Arrays

*An array is a linear allocation of memory in which elements are accessed by integers that are used to compute offsets. Arrays can be very fast data structures. Unfortunately, JavaScript does not have anything like this kind of array.*

* Array stores a data list to a single variable. You can create empty array with a straight braces: []
* Arrays are list-like objects. You can perform traversal operations against them to add, filter or modify it’s data.
* Strings cannot be used as array indexes. Instead each element of array is indexed by numbers.
* Indexes do count from 0. First element has index 0, second - 1, third - 2 etc.
 
```js
var numberList = [1, 2, 3, 4, 5];
var letterList = ['H', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd'];
console.log(numberList.length) // Result: 5.
console.log(letterList.length) // Result: 11.
console.log(numberList[1]) // Result 2.
numberList.push(6) // Adds element to array.
console.log(numberList) // Result: [1, 2, 3, 4, 5, 6].
numberList.pop() // Removes last item from array.
console.log(numberList) // Result: [1, 2, 3, 4, 5].
console.log(letterList.join('')); // Result: Hello world
```