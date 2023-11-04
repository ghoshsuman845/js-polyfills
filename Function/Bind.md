# bind() method

The `bind()` method in JavaScript creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

Here's how it works:

- It is a method available on all functions.
- It returns a new function with a certain context and potentially pre-set arguments.
- It does not immediately execute the function, but instead returns a new function that can be called at a later time.

Here's a simple example:

```
let car = {
    color: "Red",
    company: "Ferrari"
}


function purchaseCar(price){
    console.log(`I have purchased ${this.color} ${this.company} for Rs. ${price}`)
}

let getCarInfo = purchaseCar.bind(car);
getCarInfo() // Output: I have purchased Red Ferrari for Rs. 70 lakh

```

In this example, `bind()` is called on the `purchaseCar` function with `car` object as the `this` value. It returns a new function `getCarInfo` that, when called, executes `purchaseCar` with `this` set to `car`.

### Bind Vs Call/ Apply

The `bind()`, `call()`, and `apply()` methods in JavaScript are all used to set the this value when calling a function, but they do it in different ways:

- `call() and apply()` invoke the function immediately with a given `this` value and arguments. The difference between `call()` and `apply()` is in how they handle function arguments: `call()` takes arguments individually, while `apply()` takes arguments as an array.

- `bind()`, on the other hand, does not immediately invoke the function. Instead, it returns a new function with the `this` value and arguments set to what you passed in. You can call this new function later. This is useful when you want to have a function with some preset parameters.

Here's an example:

```
let car = {
    color: "Red",
    company: "Ferrari"
}

function purchaseCar(price){
    console.log(`I have purchased ${this.color} ${this.company} for Rs. ${price}`)
}

// Using call()
purchaseCar.call(car, 500000); // Output: I have purchased Red Ferrari for Rs. 500000

// Using apply()
purchaseCar.apply(car, [500000]); // Output: I have purchased Red Ferrari for Rs. 500000

// Using bind()
let purchase = purchaseCar.bind(car, 500000);
purchase(); // Output: I have purchased Red Ferrari for Rs. 500000

```

### Syntax

The syntax for the `bind()` method in JavaScript is as follows:

```
function.bind(thisObj, arg1, arg2, ...)
```

Here's what each parameter means:

- `thisObj`: The value to be passed as the `this` parameter to the target function when the bound function is called.

- `arg1, arg2, ...`: Arguments to prepend to arguments provided to the bound function when invoking the target function.-


### Polyfill

```
Function.prototype.bind = function(context, ...args) {
    context.fn = this;
    return function(){
        return context.fn(...args);
    }
};

```


