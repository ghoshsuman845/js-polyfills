# flat() method

The `flat()` method in JavaScript creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.

Here's how it works:

1. It concatenates all sub-array elements recursively up to the specified depth.
2. It returns a new array and does not change the original array.

Here's a simple example:

```
const arr = [1, 2, [3, 4, [5, 6]]];

const flattened = arr.flat(2);

console.log(flattened); // Output: [1, 2, 3, 4, 5, 6]
```

In this example, `flat()` is called on the `arr` array with a depth of 2, and it returns a new array `flattened` where all sub-array elements are concatenated up to a depth of 2.

### Syntax

The syntax for the `flat()` method in JavaScript is as follows:

```
array.flat(depth)
```

Here's what the parameter means:

- `depth` (optional): The depth level specifying how deep a nested array structure should be flattened. Defaults to 1.

The `flat()` method returns a new array with all sub-array elements concatenated into it recursively up to the specified depth.

### Polyfill

```
const arr = [1, 2, [3, 4, [5, 6]]];

Array.prototype.flat = function(depth){
    let flattenDepth = (depth === undefined) ? 1 : Math.floor(depth);
    if (flattenDepth < 1) {
      return this.slice();
    }
    return this.reduce(function(acc, val) {
      return acc.concat(Array.isArray(val) ? val.flat(flattenDepth - 1) : val);
    }, []);
}

const flattened = arr.flat(2);
console.log(flattened); // Output: [1, 2, 3, 4, 5, 6]

```

This polyfill checks if the `flat` function exists on the `Array.prototype`. If it doesn't, it adds the `flat` function. The `flat` function takes a `depth` parameter. It then applies the `reduce` function to each element in the original array. If an element is an array and the `flattenDepth` is greater than 0, it recursively calls `flat` on that element with `flattenDepth - 1`. Otherwise, it just concatenates the element to the accumulator.