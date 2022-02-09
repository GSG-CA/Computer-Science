# Algorithm Analysis

In **computer science**, an algorithm is a step-by-step procedure for solving a problem in a finite amount of time.

![](https://i.imgur.com/S21nyLo.png)

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

```javascript=
function add(num1, num2, num3) {
   return num1 + num2 + num3;
}
```

```javascript=
function sayHello() {
    for (let i = 0; i < 100; i++) {
       console.log("Hello");
    }
}
```

```javascript=
function logMultiples(num) {
    for (let i = 0; i < 10; i++) {
        console.log(i * num);
    }
}
```

---

#### O(n)

The following algorithms are **O(n)**, or **linear time**, because the data set is iterated over approximately one time:

```javascript=
function sayHello(numberOfTimes) {
    for (let i = 0; i < numberOfTimes; i++) {
        console.log("Hello");
    }
}
```

```javascript=
function doubleThenTriple(numbers) {
    let doubled = numbers.map(function(num) {
        return num * 2;
    });

    return doubled.map(function(num) {
        return num * 3;
    });
}
```

---

#### O(n<sup>2</sup>)

```javascript=
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

```javascript=
function bubbleSort(arr){

  let len = arr.length;

  for(let i =0; i < len; i++){

    for(let j = 0; j < len; j++){

        if(arr[j] > arr[j + 1]){
          // swap
          let temp = arr[j];
          arr[j] = arr[j+1];
          arr[j+1] = temp;

        }
    }
  }

}
```

In these two examples, within each element of the array, we are iterating over all elements again. Therefore, the runtime is O(n \* n) or O(n2).

It's a helpful rule of thumb that in general, if you see nested loops, the runtime will be O(nlevels of nesting). In other words, a function with a single for loop will be O(n), a function with a loop inside of a loop will be O(n2), a function with a loop inside of a loop inside of a loop will be O(n3), and so on. However, **this rule of thumb doesn't always hold**, as the following examples show:

```javascript=
// o(n^2)
function logMultiples(n) {
    for (var num1 = 1; num1 <= n; num1++) {
        for (var num2 = 1; num2 <= n; num2++) {
            console.log(num1 * num2);
        }
    }
}

// O(n)
function logSomeMultiples(n) {
    for (var num1 = 1; num1 < n=; num1++) {
        for (var num2 = 1; num2 <= Math.min(n, 10); num2++) {
            console.log(num1 * num2);
        }
    }
}
```

![](https://i.imgur.com/wjXHq1j.png)

![](https://i.imgur.com/F0fIuCx.png)
