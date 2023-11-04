# flatMap() method

The `flatMap()` method in JavaScript is a combination of `map()` and `flat()`. It first maps each element using a mapping function, then flattens the result into a new array. It's essentially identical to a `map()` followed by a `flat()` of depth 1, but `flatMap()` is often quite useful, as merging both into one method is slightly more efficient.

Here's how it works:

1. It applies a function to each item in the array to create a new array (like map()).
2. It then flattens the result into a new array (like flat()).
3. It returns a new array and does not change the original array.

Here's a simple example:

```
const arr = [1, 2, 3, 4];

const result = arr.flatMap(x => [x * 2]);

console.log(result); // Output: [2, 4, 6, 8]
```

In this example, `flatMap()` is called on the `arr` array and returns a new array `result` where each element is the result of the function `x => [x * 2]` applied to each element in the original array.

### Syntax

The syntax for the `flatMap()` method in JavaScript is as follows:

```
array.flatMap(callbackFunc(currentValue, index, arr), thisArg)
```

Here's what the parameter means:

- `callbackFunc(currentValue, index, arr)`: A function to be called for each element in the array. This function accepts three arguments:
    - `currentValue`: The current element being processed in the array.
    - `index` (optional): The index of the current element being processed in the array.
    - `arr` (optional): The array flatMap was called upon.
- `thisArg` (optional): A value to use as this when executing the callback function.

The `flatMap()` method returns a new array with the results of the callback function and all sub-array elements concatenated into it.

### Polyfill

```
const arr = [1, 2, 3, 4];

Array.prototype.flatMap = function(callback){
    let newArray = [];
    for (let i = 0; i < this.length; i++) {
      let result = callback(this[i], i, this);
      if (Array.isArray(result)) {
        newArray.push(...result);
      } else {
        newArray.push(result);
      }
    }
    return newArray;
}


const result = arr.flatMap(x => [x * 2]);
console.log(result); // Output: [2, 4, 6, 8]
```

