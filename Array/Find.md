# find() method

The `find()` method in JavaScript returns the first element in the array that satisfies the provided testing function. If no values satisfy the testing function, `undefined` is returned.

Here's how it works:

1. It tests each item in the array against a condition defined in a function.
2. The provided function is called with three arguments: the current element, the index of the current element, and the array `find()` was called upon.
3. It returns the first element that satisfies the condition. If no elements satisfy the condition, it returns `undefined`.
4. It does not mutate the original array.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

const found = numbers.find(function(number) {
    return number > 3;
});

console.log(found); // Output: 4
```

In this example, `find()` is called on the `numbers` array and returns the first number that is greater than 3.

### Syntax

The syntax for the `find()` method in JavaScript is as follows:

```
array.find(callbackFunc(currentValue, index, arr), thisValue)
```

Here's what each parameter means:

- `callbackFunc(currentValue, index, arr)`: A function to be called for each element in the array. This function accepts three arguments:
   - `currentValue`: The current element being processed in the array.
   - `index` (optional): The index of the current element being processed in the array.
   - `arr` (optional): The array find was called upon.
- `thisValue` (optional): A value to use as this when executing the callback function.

The `find()` method returns the value of the first element in the array that satisfies the provided testing function. Otherwise `undefined` is returned.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.find = function(callbackFunc){
    if (this == null) {
      throw new TypeError('Array.prototype.find called on null or undefined');
    }
    if (typeof callbackFunc !== 'function') {
      throw new TypeError('callback must be a function');
    }
    for (let i = 0; i < this.length; i++) {
      if (callbackFunc(this[i], i, this)) {
        return this[i];
      }
    }
    return undefined;
}

console.log(numbers.find(found)) //  Output: 4

```