# includes() method

The `includes()` method in JavaScript determines whether an array includes a certain value among its entries, returning `true` or `false` as appropriate.

Here's how it works:

1. It checks if the array contains a specific item.
2. It returns `true` if the array contains the item, and `false` otherwise.
3. It uses strict equality (===) for comparison.

Here's a simple example:

```
const arr = [1, 2, 3, 4, 5];

const includesTwo = arr.includes(2);

console.log(includesTwo); // Output: true
```

In this example, `includes()` is called on the `arr` array with the argument 2, and it returns true because 2 is in the array.

### Syntax

The syntax for the `includes()` method in JavaScript is as follows:

```
array.includes(valueToFind, fromIndex)
```

Here's what each parameter means:

- `valueToFind`: The value to search for in the array.
- `fromIndex` (optional): The position in the array at which to begin searching for `valueToFind`. A negative value searches from the index of `array.length + fromIndex` by default 0.

The `includes`() method returns `true` if the array contains the value, and `false` otherwise.

### Polyfill

```
const arr = [1, 2, 3, 4];

Array.prototype.includes = function(searchElement, fromIndex) {
    let length = this.length >>> 0; // Ensure it's a number and non-negative
    fromIndex = fromIndex | 0; // Ensure it's a number

    for (let i = fromIndex < 0 ? Math.max(length + fromIndex, 0) : fromIndex; i < length; i++) {
      if (this[i] === searchElement) {
        return true;
      }
    }
    return false;
}

const includesTwo = arr.includes(2);
console.log(includesTwo); // Output: true
```

