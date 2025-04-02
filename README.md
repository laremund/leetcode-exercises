# 30 Days of JavaScript
Refresher on JS, I'm using it as a warmup for the day by thinking through logic problems.

## Day 12 - 04/02 - Add Two Functions
### Description:
Given two promises promise1 and promise2, return a new promise. promise1 and promise2 will both resolve with a number. The returned promise should resolve with the sum of the two numbers.
### Solution:
```javascript
const addTwoPromises = async function(promise1, promise2) {
    return (await promise1) + (await promise2);
};
```
> *Got a **lot** easier once I remembered that an async function returns a promise by default, and
how await would give me the result of a fulfilled promise.*

## Day 11 - 03/28 - Memoize
### Solution:
```javascript
function memoize(fn) {
    const cache = {};
    return function(...args) {
        const argKey = String(args);
        if (argKey in cache) {
            return cache[argKey];
        }
        const result = fn(...args);
        cache[argKey] = result;
        return result;
    }
}
```
> *This one was a not-so-gentle reminder of how spread syntax works, apparently I've forgotten, so I failed a random test case a bunch of times until I figured out that was the issue.*

## Day 10 - 03/37 - Allow One Function Call
### Solution:
```javascript
const once = function(fn) {
    let callCount = 0;

    return function(...args){
        callCount++;
        if (callCount == 1) {
            return fn(...args);
        }
    }
};
```

## Day 9 - 03/26 - Return Length of Arguments Passed
### Solution:
```javascript
const argumentsLength = function(...args) {
    return args.length;
};
```

## Day 8 - 03/25 - Function Composition
### Solution:
```javascript
const compose = function(functions) {

    return function(x) {
        for (let i = functions.length - 1; i >= 0; i--) {
            x = functions[i](x);
        }
        return x;
    }
};
```

## Day 7 - 03/24 - Array Reduce Transformation
### Solution:
```javascript
const reduce = function(nums, fn, init) {
    let val = init;
    for (let num of nums) {
        val = fn(val, num);
    }
    return val;
};
```

## Day 6 - 03/23 - Filter Elements from Array
### Solution:
```javascript
const filter = function(arr, fn) {
    const filteredArr = [];
    for (let i = 0; i < arr.length; i++) {
        if (fn(arr[i], i)) filteredArr.push(arr[i]);
    }
    return filteredArr;
};
```

## Day 5 - 03/22 - Apply Transform Over Each Element in Array
### Solution:
```javascript
const map = function(arr, fn) {
    let newArr = [];
    for (let i = 0; i < arr.length; i++) {
        newArr.push(fn(arr[i], i));
    }
    return newArr;
};
```

## Day 4 - 3/21 - Counter II
### Solution:
```javascript
const createCounter = function(init) {
    let original = init;
    return {
        increment: () => ++init,
        decrement: () => --init,
        reset: () => init = original
    };
};
```

## Day 3 - 3/20 - To Be Or Not To Be
### Solution:
```javascript
const expect = function(val) {
  return {
    toBe: function(val2) {
      if (val === val2) return true;
      throw "Not Equal";
    },
    notToBe: function(val2) {
      if (val !== val2) return true;
      throw "Equal";
    }
  };
};
```

## Day 2 - 3/19 - Counter
### Solution:
```javascript
const createCounter = function(n) {
    let count = n;
    return () => count++;
};
```

## Day 1 - 3/18 - Create Hello World Function
### Solution:
```javascript
const createHelloWorld = function() {
    
    return function(...args) {
        return "Hello World";
    }
};
```