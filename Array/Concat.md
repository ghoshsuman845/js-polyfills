# concat() method

The `concat()` method in JavaScript is used to merge two or more arrays into a new array. This method does not change the existing arrays but instead returns a new array.

Here's how it works:

1. It merges two or more arrays into a new array.
2. It does not change the original arrays, it creates a new one.

Here's a simple example:

```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const newArr = arr1.concat(arr2);

console.log(newArr); // Output: [1, 2, 3, 4, 5, 6]
```

In this example, `concat()` is called on the `arr1` array with the `arr2` array as an argument, and it returns a new array `newArr` that is the result of merging `arr1` and `arr2`. The `arr1` and `arr2` arrays are not changed.

### Syntax

The syntax for the `concat()` method in JavaScript is quite simple:

```
array.concat(value1, value2, ..., valueN)
```

Here's what each parameter means:

- `value1, value2, ..., valueN` (optional): Arrays and/or values to concatenate into a new array. If all valueN parameters are omitted, `concat` returns a shallow copy of the existing array on which it is called.

The `concat()` method returns a new array that is the result of merging the original array with the arrays and/or values provided as arguments.

### Polyfill

```

Array.prototype.concat = function() {
  let newArray = [...this];
  for (let i = 0; i < arguments.length; i++) {
    let arg = arguments[i];
    if (Array.isArray(arg)) {
      newArray.push(...arg);
    } else {
      newArray.push(arg);
    }
  }
  return newArray;
};

const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const newArr = arr1.concat(arr2);
console.log(newArr); // Output: [1, 2, 3, 4, 5, 6]
```

In this version, the spread operator (...) is used to copy the original array and to push all elements of arg to newArray if arg is an array. This eliminates the need for the inner loop.

