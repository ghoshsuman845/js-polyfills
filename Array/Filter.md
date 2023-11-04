# filter() method

The `filter()` method in JavaScript creates a new array with all elements that pass a test implemented by the provided function.

Here's how it works:

1. It creates a new array with all elements that pass a test (provided as a function).
2. The provided function is called with three arguments: the current element, the index of the current element, and the array `filter()` was called upon.
3. It does not mutate the original array.

Here's a simple example:

```
const numbers = [1, 2, 3, 4, 5];

const evenNumbers = numbers.filter(function(number) {
    return number % 2 === 0;
});

console.log(evenNumbers); // Output: [2, 4]
```

In this example, `filter()` is called on the `numbers` array and returns a new array `evenNumbers` where each number is even.

### Syntax

The syntax for the `filter()` method in JavaScript is as follows:

```
array.filter(callbackFunc(currentValue, index, arr), thisValue)
```

Here's what each parameter means:

- `callbackFunc(currentValue, index, arr)`: A function to be called for each element in the array. This function accepts three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index (optional)`: The index of the current element being processed in the array.
  - `arr (optional)`: The array `filter` was called upon.
- `thisValue (optional)`: A value to use as `this` when executing the callback function.

The `filter()` method returns a new array with all elements that pass the test implemented by the provided function.

### Polyfill

```
const numbers = [1, 2, 3, 4, 5];

Array.prototype.filter = function(callbackFunc){
    const newArr = []
    for(let i=0; i<this.length; i++){
       if(callbackFunc(this[i])){
          newArr.push(callbackFunc(this[i]))
       }
    }
    return newArr;
}

console.log(numbers.map(evenNumbers)) // Output: [2, 4]

```