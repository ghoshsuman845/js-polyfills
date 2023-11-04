# reverse() method

The `reverse()` method in JavaScript is used to reverse the order of the elements in an array. It mutates the original array and returns a reference to the same array (not a new one).

Here's how it works:

1. It reverses the order of the elements in the array.
2. It changes the original array, it does not create a new one.

Here's a simple example:

```
const arr = [1, 2, 3, 4, 5];

arr.reverse();

console.log(arr); // Output: [5, 4, 3, 2, 1]
```

In this example, `reverse()` is called on the `arr` array, and it reverses the order of the elements in the array. The `arr` array is now `[5, 4, 3, 2, 1]`.

### Syntax

The syntax for the `reverse()` method in JavaScript is quite simple:

```
array.reverse()
```

The `reverse()` method does not take any parameters. It reverses the order of the elements in the original array and returns the same array (not a new one).

### Polyfill

```
const arr = [1, 2, 3, 4];

Array.prototype.reverse = function() {
    let mid = Math.floor(this.length / 2);
    for (let i = 0; i < mid; i++) {
      let temp = this[i];
      this[i] = this[this.length - 1 - i];
      this[this.length - 1 - i] = temp;
    }
    return this;
  };

arr.reverse();
console.log(arr); // Output: [5, 4, 3, 2, 1]
```

