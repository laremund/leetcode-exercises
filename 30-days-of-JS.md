# 30 Days of JavaScript
Refresher on JS, I'm using it as a warmup for the day by thinking through logic problems.

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