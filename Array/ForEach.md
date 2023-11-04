# forEach() method

The `forEach()` method in JavaScript is used to execute a provided function once for each array element. It does not return a new array like the `map()` method.

Here's how it works:

1. It is a method available on all arrays.
2. It executes a provided function once for each array element.
3. The provided function is called with three arguments: the current element, the index of the current element, and the array `forEach()` was called upon.
4. It does not mutate the original array.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number, index) {
    console.log(`Element ${number} is at index ${index}`);
});

// Output:
// Element 1 is at index 0
// Element 2 is at index 1
// Element 3 is at index 2
// Element 4 is at index 3
// Element 5 is at index 4
```

In this example, `forEach()` is called on the numbers array and logs each number along with its index.

### Syntax

The syntax for the `forEach()` method in JavaScript is as follows:

```
array.forEach(callbackFunc(currentValue, index, arr), thisValue)
```

Here's what each parameter means:

- `callbackFunc(currentValue, index, arr)`: A function to be called for each element in the array. This function accepts three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index (optional)`: The index of the current element being processed in the array.
  - `arr (optional)`: The array `forEach` was called upon.
- `thisValue (optional)`: A value to use as `this` when executing the callback function.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.forEach = function(callbackFunc){
    for(let i=0; i<this.length; i++){
        callbackFunc(this[i])
    }
}

const printNums = function(number, index) {
    console.log(`Element ${number} is at index ${index}`);
}

numbers.forEach(printNums) 

// Output:
// Element 1 is at index 0
// Element 2 is at index 1
// Element 3 is at index 2
// Element 4 is at index 3
// Element 5 is at index 4

```