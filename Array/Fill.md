# fill() method

The `fill()` method in JavaScript changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.

Here's how it works:

1. It changes all elements in the array to a static value.
2. It changes the original array, it does not create a new one.

Here's a simple example:

```
const arr = [1, 2, 3, 4, 5];

arr.fill(0, 2, 4);

console.log(arr); // Output: [1, 2, 0, 0, 5]
```

In this example, `fill()` is called on the `arr` array with the arguments 0, 2, and 4. It changes all elements from index 2 to 4 (exclusive) to 0. The arr array is now `[1, 2, 0, 0, 5]`.

### Syntax

The syntax for the `fill()` method in JavaScript is quite simple:

```
array.fill(value, start, end)
```

Here's what each parameter means:

- `value`: The value to fill the array with.
- `start` (optional): The index to start filling at. Defaults to 0.
- `end` (optional): The index to stop filling at (exclusive). Defaults to array.length.

The `fill()` method modifies the original array and returns it.

### Polyfill

```

Array.prototype.fill = function(value, start, end) {
    // Use the length of the array, if end parameter is not specified
    end = end || this.length;
    // Use 0 as start if start parameter is not specified
    start = start || 0;

    // Make sure start and end are numbers
    start = Number(start);
    end = Number(end);

    for (let i = start; i < end; i++) {
      this[i] = value;
    }

    return this;
};

const arr = [1, 2, 3, 4, 5];

arr.fill(0, 2, 4);

console.log(arr); // Output: [1, 2, 0, 0, 5]
```


