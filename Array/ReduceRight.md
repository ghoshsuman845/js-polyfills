# reduceRight() method

The `reduceRight()` method in JavaScript applies a function against an accumulator and each element in the array (from right to left) to reduce it to a single value.

Here's how it works:

1. It applies a function against an accumulator and each element in the array (from right to left) to reduce it to a single value.
2. The provided function is called with four arguments: the accumulator, the current element, the index of the current element, and the array `reduceRight()` was called upon.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduceRight(function(accumulator, currentValue) {
    return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```

In this example, `reduceRight()` is called on the `numbers` array and returns a single value `sum` which is the sum of all numbers in the array. The second argument to `reduceRight()` (0 in this case) is the initial value of the accumulator. The difference between `reduce()` and `reduceRight()` is the direction in which the array is traversed.

### Syntax

The syntax for the `reduceRight()` method in JavaScript is as follows:

```
array.reduceRight(callbackFunc(accumulator, currentValue, index, arr), initialValue)
```

Here's what each parameter means:

- `callbackFunc(accumulator, currentValue, index, arr)`: A function to be called for each element in the array (from right to left). This function accepts four arguments:
   - `accumulator`: The accumulator accumulates the callback's return values.
   - `currentValue`: The current element being processed in the array.
   - `index` (optional): The index of the current element being processed in the array.
   - `arr` (optional): The array `reduceRight` was called upon.
- initialValue (optional): A value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used.

The `reduceRight()` method returns the value that results from the reduction.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.reduceRight = function(callbackFunc, initialVal){
    let accumulator = (initialVal === undefined) ? undefined : initialVal;
    for (let i = this.length - 1; i >= 0; i--) {
      if (accumulator !== undefined)
        accumulator = callbackFunc.call(undefined, accumulator, this[i], i, this);
        // this can be simplified to: accumulator = callbackFunc(accumulator, this[i])
      else
        accumulator = this[i];
    }
    return accumulator;
}

console.log(numbers.reduceRight(sum)) //  Output: 15

```