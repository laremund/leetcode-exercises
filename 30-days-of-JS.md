# 30 Days of JavaScript
Refresher on JS, I'm using it as a warmup for the day by thinking through logic problems.

## Day 30
```javascript

```

## Day 29
```javascript

```

## Day 28
```javascript

```

## Day 27
```javascript

```

## Day 26
```javascript

```

## Day 25
```javascript

```

## Day 24
```javascript

```

## Day 23
```javascript

```

## Day 22
```javascript

```

## Day 21
```javascript

```

## Day 20
```javascript

```

## Day 19
```javascript

```

## Day 18
```javascript

```

## Day 17
```javascript

```

## Day 16
```javascript

```

## Day 15
```javascript

```

## Day 14
```javascript

```

## Day 13
```javascript

```

## Day 12
```javascript

```

## Day 11
```javascript

```

## Day 10
```javascript

```

## Day 9
```javascript

```

## Day 8
```javascript

```

## Day 7
```javascript

```

## Day 6
```javascript

```

## Day 5
```javascript

```

## Day 4
```javascript

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