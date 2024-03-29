# Algorithm Analysis

In **computer science**, an algorithm is a step-by-step procedure for solving a problem in a finite amount of time.

A **data structure** is a systematic way of organizing and accessing data

These concepts are central to computing, but to be able to classify some data structures and algorithms as “good,” we must have precise ways of analyzing them.

---

## Algorithm Analysis

**Algorithm analysis** or **Complexity Analysis** is a process of determining the amount of time, resource, etc. required when executing an algorithm.

The efficiency of any algorithmic solution to a problem is a measure of the:

- Time efficiency: the time it takes to execute.
- Space efficiency: the space (primary or secondary memory) it uses.

##### Complexity Analysis – Why we need it?

There are often many different algorithms which can be used to solve the same problem.

Thus, it makes sense to develop techniques that allow us to Compare different algorithms with respect to their “efficiency” and to Choose the most efficient algorithm for the problem

---

### Experimental Approach

- Write a program that implements the algorithm.
- Run the program with data sets of varying size.
- Determine the actual running time.

##### Experimental Approach - Problems

- It is necessary to implement and test the algorithm in order to determine its running time.
- Experiments can be done only on a limited set of inputs, and may not be indicative of the running time for other inputs.
- The same hardware and software should be used in order to compare two algorithms. – condition very hard to achieve!

---

### Asymptotic Approach (Big O Notation)

- This "approximate" measure of efficiency is called asymptotic complexity.
- Thus the asymptotic complexity measure does not give the exact number of operations of an algorithm, but it shows how that number grows with the size of the input.
- This gives us a measure that will work for different operating systems, compilers and CPUs.

The most commonly used notation for specifying asymptotic complexity is the **Big O notation**.

**Big O notation** is a concept borrowed from mathematics that gives you an approximate upper bound (worst-case) on the runtime of your algorithm based on the size of the data set that the algorithm will use.

Example: O(n), O(n<sup>2</sup>), O(log n), O(2<sup>n</sup>) where <u>**n** is the (input size)</u>

---

To get started with Big O notation, it is useful to understand what is important and what is not. There are a couple of rules with the notation to remember:

1. Constants are ignored
2. Smaller components are ignored

Keeping those rules in mind, the following are equivalent:

**O(500 \* n) --> O(n)**

**O(99999999999) --> O(1)**

**O(10\*n<sup>2</sup> + 5n + 20) --> O(n<sup>2</sup>)**

**O(n \* n) --> O(n<sup>2</sup>)**

**O(n*log(n) + 30000 * n) --> O(n \* log(n))**

##### Notice that in all examples, constant values are replaced with 1, and all smaller components that are added are ignored.

---

### Examples Big O Runtimes

#### O(1)

The following functions are **O(1)** or **constant time** because the algorithm is not dependent on a variable size data set. In other words, regardless of the input size, the runtime of the algorithm will not grow beyond some constant size. (In many cases, it will be roughly the same regardless of the input).

```javascript
function add(num1, num2, num3) {
  return num1 + num2 + num3;
}
```

```javascript
function sayHello() {
  for (let i = 0; i < 100; i++) {
    console.log("Hello");
  }
}
```

```javascript
function logMultiples(num) {
  for (let i = 0; i < 10; i++) {
    console.log(i * num);
  }
}
```

---

#### O(n)

The following algorithms are **O(n)**, or **linear time**, because the data set is iterated over approximately one time:

```javascript
function sayHello(numberOfTimes) {
  for (let i = 0; i < numberOfTimes; i++) {
    console.log("Hello");
  }
}
```

```javascript
function doubleThenTriple(numbers) {
  let doubled = numbers.map(function (num) {
    return num * 2;
  });

  return doubled.map(function (num) {
    return num * 3;
  });
}
```

---

#### O(n<sup>2</sup>)

```javascript
function allPairs(arr) {
  let pairs = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      pairs.push([arr[i], arr[j]]);
    }
  }

  return pairs;
}
```

```javascript
function bubbleSort(arr) {
  let len = arr.length;

  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len; j++) {
      if (arr[j] > arr[j + 1]) {
        // swap
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
}
```

In these two examples, within each element of the array, we are iterating over all elements again. Therefore, the runtime is O(n \* n) or O(n2).

It's a helpful rule of thumb that in general, if you see nested loops, the runtime will be O(nlevels of nesting). In other words, a function with a single for loop will be O(n), a function with a loop inside of a loop will be O(n2), a function with a loop inside of a loop inside of a loop will be O(n3), and so on. However, **this rule of thumb doesn't always hold**, as the following examples show:

```javascript
// o(n^2)
function logMultiples(n) {
    for (let num1 = 1; num1 <= n; num1++) {
        for (let num2 = 1; num2 <= n; num2++) {
            console.log(num1 * num2);
        }
    }
}

// O(n)
function logSomeMultiples(n) {
    for (let num1 = 1; num1 < n=; num1++) {
        for (let num2 = 1; num2 <= Math.min(n, 10); num2++) {
            console.log(num1 * num2);
        }
    }
}
```

---

## Across Time and Space

So far we've only been talking about the runtime of different algorithms using Big O Notation. This is often referred to as analyzing the **time complexity** of the algorithm.

But Big O isn't just used to talk about the time it takes our programs to run; it's also used to talk about how much space (i.e. memory) our program requires. This is often referred to as analyzing the **space complexity** of the algorithm.

Very often we're concerned primarily with **auxiliary space complexity**, that is, how much additional memory does the algorithm require beyond what needs to be allocated for the inputs themselves?

Let's look at a couple of examples:

```js
function total(array) {
  var total = 0;
  for (var i = 0; i < array.length; i++) {
    total += array[i];
  }
  return total;
}
```

In this example, `total` takes one input, which is an array. Let's let `n` denote the length of the array. Note that the time complexity of `total` is O(n), since we're looping through the array once and adding to the total. However, the space complexity is just O(1), since we only require one additional unit of space, for the number stored in `total`.

Here's another example:

```js
function double(array) {
  var newArray = [];
  for (var i = 0; i < array.length; i++) {
    newArray.push(2 * array[i]);
  }
  return newArray;
}
```

Here, our function `double` takes each element of the input array, doubles it, and returns a new array of doubled values. In this case, both the time and space complexities are O(n). Space complexity is larger in this case because we need n additional units of space: one for each element in the original array.

---

![](https://i.imgur.com/wjXHq1j.png)

![](https://i.imgur.com/F0fIuCx.png)

---

## Big O [Exercises](./BigOExercises.md)
