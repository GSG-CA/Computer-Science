# Recursion 

## What is Recursion?
The process in which a function calls itself directly or indirectly.

## What is the difference between direct and indirect recursion?
- Direct Recursion: A function calls itself directly.
Example:
```js=
function A() {
  A();
}
```
- Indirect Recursion: A function calls another function that calls the first function again.
Example:
```js=
function A() {
  B();
}
function B() {
  A();
}
```
if we call A(), it will call B() and then B() will call A() again and so on.
the function calls itself indirectly through another function until it reaches the base case
(terminating condition / stopping condition) but becuase there is no base case in the above example, the function will cause a stack overflow error.


## What is the base case?
The base case is the condition that allows the function to stop recursing. Without a base case, the function would recurse infinitely and cause a stack overflow error.

## What is Stack Overflow Error?
A stack overflow error occurs when the stack memory is full. Since every recursive call needs extra space in the stack memory, a stack overflow error is very likely to happen if the base case is not reached.

> Review: [Stacks](./StacksAndQueues.md)

<hr>

So , basically Recursion consists of two parts:
- Base Case
- Recursive Call

## What is the difference between recursion and iteration?
| Recursion                                  | Iteration                       |
|--------------------------------------------|---------------------------------|
| Terminates when the base case becomes true | Terminates when the condition becomes false |
| Used with functions                        | Used with loops                 |
| Every recursive call needs extra space in the stack memory | Every iteration does not require any extra space |
| Smaller code size                          | Larger code size                |


## How to write recursive functions?
A recursive function is a function that calls itself during its execution. This enables the function to repeat itself several times, outputting the result and the end of each iteration.

### Example
```js=
function factorial(n) {
  if (n === 0) {
    return 1;
  }
  return n * factorial(n - 1);
}
```
The above function is a recursive function that calculates the factorial of a given number. The factorial of a number is the product of all integers from 1 up to that number. For example, the factorial of 5 is 1 * 2 * 3 * 4 * 5 = 120.

Mathematically, we can define the factorial of a number n as follows:
```
n! = 1                  if n = 0
n! = n * (n - 1)!       if n > 0
```

the above function is equivalent to the following:
```js=
function factorial(n) {
  let result = 1;
  for (let i = 1; i <= n; i++) {
    result *= i;
  }
  return result;
}
```

### Example
```js=
function sum(arr) {
  if (arr.length === 0) {
    return 0;
  }
  return arr[0] + sum(arr.slice(1));
}
```
The above function is a recursive function that calculates the sum of an array of numbers. The sum of an array of numbers is the addition of all its elements. For example, the sum of [1, 2, 3, 4, 5] is 1 + 2 + 3 + 4 + 5 = 15.

Mathematically, we can define the sum of an array of numbers as follows:
```
sum([]) = 0
sum([x, ...rest]) = x + sum(rest)
```

the above function is equivalent to the following:
```js=
function sum(arr) {
  let result = 0;
  for (let i = 0; i < arr.length; i++) {
    result += arr[i];
  }
  return result;
}
```
<hr> 

## tailed recursion vs non-tailed recursion

### Tailed Recursion
A recursive function is said to be tailed recursive if the recursive call is the last thing executed by the function. There is no need to keep record of the previous state.

Example:
```js=
function factorial(n, result = 1) {
  if (n === 0) {
    return result;
  }
  return factorial(n - 1, n * result);
}
```
The above function is a tailed recursive function that calculates the factorial of a given number. 

---- 

is the following function is tailed recursive?
```js=
function sum(arr, result = 0) {
  if (arr.length === 0) {
    return result;
  }
  return sum(arr.slice(1), result + arr[0]);
}
```
<!-- yes, it is tailed recursive because the recursive call is the last thing executed by the function. -->
<!-- The above function is a tailed recursive function -->

### Non-Tailed Recursion
A recursive function is said to be non-tailed recursive if the recursive call is not the last thing executed by the function. There is a need to keep record of the previous state.

Example:
```js=
function factorial(n) {
  if (n === 0) {
    return 1;
  }
  return n * factorial(n - 1);
}
```
The above function is a non-tailed recursive function.

#### But why its non-tailed recursive?
because the function needs to keep record of the previous state (n * factorial(n - 1)).

## What is the benefit of tailed recursion?
The benefit of tailed recursion is that it can be easily converted to an iterative loop by a compiler. This is called tail call optimization.

basically, the compiler can convert the tailed recursive function to an iterative loop to save memory.
in that way we can use recursion and benefit from its advantages and at the same time we can save memory.

backing to the factorial example:
```js=
function factorial(n, result = 1) {
  if (n === 0) {
    return result;
  }
  return factorial(n - 1, n * result);
}
```
the compiler can convert the above function to the following:
```js=
function factorial(n) {
  let result = 1;
  for (let i = n; i > 0; i--) {
    result *= i;
  }
  return result;
}
```
So Now the Space Complexity of the factorial function is O(1) instead of O(n).





