# 30 Days of JavaScript
Refresher on JS, I'm using it as a warmup for the day by thinking through logic problems.

## Day 16 -  - Promise Time Limit
### Description:
Given an asynchronous function `fn` and a time `t` in milliseconds, return a new time limited version of the input function. `fn` takes arguments provided to the time limited function.

The time limited function should follow these rules:

If the `fn` completes within the time limit of `t` milliseconds, the time limited function should resolve with the result.
If the execution of the `fn` exceeds the time limit, the time limited function should reject with the string `"Time Limit Exceeded"`.
### Solution:
```javascript
const timeLimit = function(fn, t) {

    return async function(...args) {
        let timeout = new Promise((resolve, reject) => {
            setTimeout(() => {
                reject("Time Limit Exceeded")
            }, t)
        })
        
        return Promise.race([fn(...args), timeout])
    }
};
```

## Day 15 - Interval Cancellation
### Description:
Given a function fn, an array of arguments args, and an interval time t, return a cancel function cancelFn.

After a delay of cancelTimeMs, the returned cancel function cancelFn will be invoked.

> setTimeout(cancelFn, cancelTimeMs)

The function fn should be called with args immediately and then called again every t milliseconds until cancelFn is called at cancelTimeMs ms.
### Solution:
```javascript
const cancellable = function(fn, args, t) {
    let cancelled = false;
    const cancelFn = () => cancelled = true;
    const checkCancelled = () => {
        if (!cancelled) { 
            fn(...args);
            setTimeout(checkCancelled, t);
        }
        return;
    }
    checkCancelled();
    return cancelFn;
};
```
> ^ That was my initial submission using recursion (which was 9ms faster), below is my submission using setInterval
```javascript
const cancellable = function(fn, args, t) {
    fn(...args);
    const interval = setInterval(() => fn(...args), t);
    const cancelFn = () => clearInterval(interval);
    return cancelFn;
};
```

## Day 14 - Timeout Cancellation
### Description:
Given a function fn, an array of arguments args, and a timeout t in milliseconds, return a cancel function cancelFn.

After a delay of cancelTimeMs, the returned cancel function cancelFn will be invoked.

> setTimeout(cancelFn, cancelTimeMs)

Initially, the execution of the function fn should be delayed by t milliseconds.

If, before the delay of t milliseconds, the function cancelFn is invoked, it should cancel the delayed execution of fn. Otherwise, if cancelFn is not invoked within the specified delay t, fn should be executed with the provided args as arguments.
### Solution:
```javascript
const cancellable = function(fn, args, t) {
    let cancelled = false;

    const cancelFn = () => cancelled = true;
    
    const checkCancelled = () => {
        if (!cancelled) { fn(...args) }
    }
    setTimeout(checkCancelled, t);

    return cancelFn;
};
```

## Day 13 - Sleep
### Description:
Given a positive integer millis, write an asynchronous function that sleeps for millis milliseconds. It can resolve any value.
### Solution:
```javascript
async function sleep(millis) {
    const sleepPromise = new Promise((resolve) => {
            setTimeout(() => resolve(), millis)
        })
    await sleepPromise;
}
```

## Day 12 - Add Two Functions
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

## Day 11 - Memoize
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

## Day 10 - Allow One Function Call
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

## Day 9 - Return Length of Arguments Passed
### Solution:
```javascript
const argumentsLength = function(...args) {
    return args.length;
};
```

## Day 8 - Function Composition
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

## Day 7 - Array Reduce Transformation
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

## Day 6 - Filter Elements from Array
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

## Day 5 - Apply Transform Over Each Element in Array
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

## Day 4 - Counter II
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

## Day 3 - To Be Or Not To Be
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

## Day 2 - Counter
### Solution:
```javascript
const createCounter = function(n) {
    let count = n;
    return () => count++;
};
```

## Day 1 - Create Hello World Function
### Solution:
```javascript
const createHelloWorld = function() {
    
    return function(...args) {
        return "Hello World";
    }
};
```