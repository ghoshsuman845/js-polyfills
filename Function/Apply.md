# apply() method

The `apply()` method in JavaScript is a method that is used to call another function with a given `this` value and arguments provided as an array (or an array-like object). It is used for function borrowing and for invoking a function with a specific `this` context.

Here's how it works:

1. It is a method available on all functions.
2. It calls the function with a given `this` value and arguments provided as an array (or an array-like object).
3. It returns the result of the function call.

Here's a simple example:

```
let car1 = {
    color: "Red",
    company: "Ferrari"
}

let car2 = {
    color: "Blue",
    company: "BMW"
}

function purchaseCar(price){
    console.log(`I have purchased ${this.color} ${this.company} for Rs. ${price}`)
}

purchaseCar.apply(car1, ["70 lakh"]) // Output: I have purchased Red Ferrari for Rs. 70 lakh
purchaseCar.apply(car2, ["90 lakh"]) // Output: I have purchased Blue BMW for Rs. 90 lakh

```

In this example, `apply()` is called on the purchaseCar function with `car1` as the `this` value. It calls purchaseCar with `this` set to car1, so this.color and this.company inside purchaseCar refer to `car1.color` and `car1.company`, respectively. The purchaseCar function is not changed. Similar happens when `apply()` is called on the purchaseCar function with `car2` as the `this` value. This time the `this` refers to `car2`, therefore the same `purchaseCar` function can be borrowed by both the objects `car1` and `car2`. Also the arguments passed to the function `purchaseCar` are provided as array.

### Syntax

The syntax for the `apply()` method in JavaScript is as follows:

```
func.apply(thisObj, argsArray);
```

Here's what each parameter means:

- `thisObj`: The value of `this` provided for the call to function. Note that this may not be the actual value seen by the method: if the method is a function in non-strict mode, `null` and `undefined` will be replaced with the global object, and primitive values will be boxed.

- `argsArray` (optional): An array-like object, specifying the arguments with which function should be called, or null or undefined if no arguments should be provided to the function. Starting with ECMAScript 5 these arguments can be a generic array-like object instead of an array.


### Polyfill

```

Function.prototype.apply = function(context, args) {
    context = context || window;
    args = args || [];

    context.fn = this;

    context.fn(...args);

};

```
