# 30 Days of JavaScript
Refresher on JS, I'm using it as a warmup for the day by thinking through logic problems.

## Day 8 - 03/25 - Function Composition
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
```javascript
const createCounter = function(n) {
    let count = n;
    return () => count++;
};
```

## Day 1 - 3/18 - Create Hello World Function
```javascript
const createHelloWorld = function() {
    
    return function(...args) {
        return "Hello World";
    }
};
```