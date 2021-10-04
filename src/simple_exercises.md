# Simple exercises

**Exercise 1**

1. Create an array that consist of numbers: [1, 2, 3, 4, 5, 6];
2. Write a function that takes given array as an argument;
3. By using one of the loop inside function write a logic that will double every element in array;
4. Print all elements of a newly created array;

**Exercise 2**

1. By using one of the object creation pattern in JS implement Game object that will take map as array and name as string in constructor;
2. Write a methods for getting map and name (getMap, getName);
3. Implement method toString that will display map and name in console in nicely formatted way;

**Exercise 3**

1. Write a function that will solve quadratic equation: https://en.wikipedia.org/wiki/Quadratic_equation
2. The standard form of a quadratic equation is:

```
ax2 + bx + c = 0, where
a, b and c are real numbers and
a ≠ 0
```

3. To find the roots of such equation, we use the formula:

```
(root1,root2) = (-b ± √b2-4ac)/2
```

4. The term `b2-4ac` is known as the **discriminant** of a quadratic equation. It tells the nature of the roots.

* If the discriminant is greater than **0**, the roots are **real** and **different**.
* If the discriminant is equal to **0**, the roots are **real** and **equal**.
* If the discriminant is less than **0**, the roots are **complex** and **different**.

5. Use such statements for getting input:

```javascript
// take input from the user
let a = prompt("Enter the first number: ");
let b = prompt("Enter the second number: ");
let c = prompt("Enter the third number: ");
```

Tips: You need to use *Math.sqrt* for getting square root and *Number.prototype.toFixed(2)* if you want to round a number.

6. Example of execution:

```
Enter the first number: 1
Enter the second number: 6
Enter the third number: 5
The roots of quadratic equation are -1 and -5
```

**Exercise 4**

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*. You may assume that each input would have ***exactly\* one solution**, and you may not use the *same* element twice. You can return the answer in any order.

Example 1:

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

Example 2:

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

Example 3:

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
const twoSum = function(nums, target) {
    
};
```

Hint:

If we fix one of the numbers, say

```
x
```

, we have to scan the entire array to find the next number

```
y
```

which is

```
value - x
```

where value is the input parameter. 
