# split() method

The `split()` method in JavaScript is used to split a string into an array of substrings, and returns the new array.

Here's how it works:

1. It splits the string into an array of substrings based on a specified separator.
2. It does not change the original string, it creates a new array.

Here's a simple example:

```
const str = 'Hello World';

const arr = str.split(' ');

console.log(arr); // Output: ["Hello", "World"]
```

In this example, `split()` is called on the `str` string with the argument ' '. It splits the string into an array of substrings, with each substring separated by a space. The `arr` array is now `["Hello", "World"]`. The str string is not changed.

### Syntax

The syntax for the `split()` method in JavaScript is as follows:

```
string.split(separator, limit)
```

Here's what the parameter means:

- `separator` (optional): Specifies the character, or the regular expression, to use for splitting the string. If omitted, the entire string will be returned as a single array element.
- `limit` (optional): An integer that specifies the number of splits. Items after the split limit will not be included in the array.

The `split()` method returns a new array. The original string is not changed.

### Polyfill

```
String.prototype.split = function(separator) {
    let output = [];
    let start = 0;
    let end;

    separator = separator || '';

    if (separator === '') {
      for (let i = 0; i < this.length; i++) {
        output.push(this.charAt(i));
      }
    } else {
      while ((end = this.indexOf(separator, start)) !== -1) {
        output.push(this.substring(start, end));
        start = end + separator.length;
      }
      output.push(this.substring(start));
    }

    return output;
};

const str = 'Hello World';

const arr = str.split(' ');

console.log(arr); // Output: ["Hello", "World"]
```


