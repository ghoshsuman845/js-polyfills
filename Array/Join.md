# join() method

The `join()` method in JavaScript is used to join all elements of an array into a string. The elements will be separated by a specified separator. The default separator is a comma (,).

Here's how it works:

1. It joins all elements in the array into a string.
2. It does not change the original array, it creates a new string.

Here's a simple example:

```
const arr = ['Hello', 'World'];

const str = arr.join(' ');

console.log(str); // Output: "Hello World"
```

In this example, `join()` is called on the `arr` array with the argument ' '. It joins all elements in the array into a string, with each element separated by a space. The str string is now "Hello World". The arr array is not changed.

### Syntax

The syntax for the `join()` method in JavaScript is quite simple:

```
array.join(separator)
```

Here's what the parameter means:

- `separator` (optional): Specifies a string to separate each pair of adjacent elements of the array. The separator is converted to a string if necessary. If omitted, the array elements are separated with a comma (,).

The `join()` method returns a string resulting from converting all array elements in order of their indices into strings and joining them with the provided separator.

### Polyfill

```
Array.prototype.join = function(separator) {
    // Use comma as separator if it's not specified
    separator = separator || ',';

    let str = '';
    for (let i = 0; i < this.length; i++) {
      str += this[i];
      if (i < this.length - 1) {
        str += separator;
      }
    }

    return str;
};

const arr = ['Hello', 'World'];

const str = arr.join(' ');

console.log(str); // Output: "Hello World"
```


