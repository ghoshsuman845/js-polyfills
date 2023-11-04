# map() method

The `map()` method in JavaScript works as follows:

1. It creates a new array with the results of calling a provided function on every element in the calling array.
2. The provided function is called with three arguments: the current element, the index of the current element, and the array map was called upon.
3. The `this` value provided as a second argument to `map()` is used as `this` when executing each callback.
4. It does not mutate the original array.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

const doubledNumbers = numbers.map(function(number) {
    return number * 2;
});

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

In this example, map() is called on the numbers array and returns a new array doubledNumbers where each number is doubled.


### Syntax

The syntax for the map() method in JavaScript is as follows:

```
array.map(callbackFunc(currentValue, index, arr), thisValue)
```

Here's what each parameter means:

- `callbackFunc(currentValue, index, arr)`: A function to be called for each element in the array. This function accepts three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index (optional)`: The index of the current element being processed in the array.
  - `arr (optional)`: The array `map` was called upon.
- `thisValue (optional)`: A value to use as `this` when executing the callback function.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.map = function(callbackFunc){
    const newArr = []
    for(let i=0; i<this.length; i++){
        newArr.push(callbackFunc(this[i]))
    }
    return newArr;
}

console.log(numbers.map(doubledNumbers)) // Output: [2, 4, 6, 8, 10]

```