# reduce() method

The `reduce()` method in JavaScript applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

Here's how it works:

1. It applies a function against an accumulator and each element in the array to reduce it to a single value.
2. The provided function is called with four arguments: the accumulator, the current element, the index of the current element, and the array `reduce()` was called upon.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce(function(accumulator, currentValue) {
    return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```

In this example, `reduce()` is called on the `numbers` array and returns a single value `sum` which is the sum of all numbers in the array. The second argument to `reduce()` (0 in this case) is the initial value of the accumulator.

### Syntax

The syntax for the `reduce()` method in JavaScript is as follows:

```
array.reduce(callbackFunc(accumulator, currentValue, index, arr), initialValue)
```

Here's what each parameter means:

- `callbackFunc(accumulator, currentValue, index, arr)`: A function to be called for each element in the array. This function accepts four arguments:
    - `accumulator`: The accumulator accumulates the callback's return values.
    - `currentValue`: The current element being processed in the array.
    - `index` (optional): The index of the current element being processed in the array.
    - `arr` (optional): The array `reduce` was called upon.
- initialValue (optional): A value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used.

The `reduce()` method returns the value that results from the reduction.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.reduce = function(callbackFunc, initialVal){
    let accumulator = (initialVal === undefined) ? undefined : initialVal;
    for (let i = 0; i < this.length; i++) {
      if (accumulator !== undefined)
        accumulator = callbackFunc.call(undefined, accumulator, this[i], i, this);
        // this can be simplified to: accumulator = callbackFunc(accumulator, this[i])
      else
        accumulator = this[i];
    }
    return accumulator;
}

console.log(numbers.reduce(sum)) //  Output: 15

```