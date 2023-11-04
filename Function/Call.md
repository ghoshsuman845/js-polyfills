# call() method

The `call()` method in JavaScript is a method that is used to call another function, with a given `this` value and arguments provided individually (not as an array). It is used for function borrowing and for invoking a function with a specific `this` context.

Here's how it works:

1. It is a method available on all functions.
2. It calls the function with a given `this` value and arguments provided individually.
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

purchaseCar.apply(car1, "70 lakh") // Output: I have purchased Red Ferrari for Rs. 70 lakh
purchaseCar.apply(car2, "90 lakh") // Output: I have purchased Blue BMW for Rs. 90 lakh

```

In this example, `call()` is called on the purchaseCar function with `car1` as the `this` value. It calls purchaseCar with `this` set to car1, so this.color and this.company inside purchaseCar refer to `car1.color` and `car1.company`, respectively. The purchaseCar function is not changed. Similar happens when `call()` is called on the purchaseCar function with `car2` as the `this` value. This time the `this` refers to `car2`, therefore the same `purchaseCar` function can be borrowed by both the objects `car1` and `car2`. Also the arguments passed to the function `purchaseCar` are not provided as array, this is the only difference between `call()` and `apply()` method.

### Syntax

The syntax for the `call()` method in JavaScript is as follows:

```
function.call(thisObj, arg1, arg2, ...)
```

Here's what each parameter means:

- `thisObj`: The value of `this` provided for the call to function. Note that this may not be the actual value seen by the method: if the method is a function in non-strict mode, null and undefined will be replaced with the global object, and primitive values will be boxed.

- `arg1, arg2, ...`: Arguments for the object method. They are optional and can be passed individually to the function.


### Polyfill

```

Function.prototype.call = function(context, ...args) {

    context.fn = this;

    context.fn(...args);

};

```
