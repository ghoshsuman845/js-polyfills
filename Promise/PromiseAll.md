# Promise.all()

`Promise.all()` is a method in JavaScript that is used to handle multiple promises simultaneously. It takes an iterable of promises as an input, and returns a single Promise that resolves when all of the input promises have resolved, or rejects with the reason of the first promise that rejected.

Here's how it works:

1. It takes an iterable of Promises.
2. It returns a new Promise.
3. The new Promise resolves with an array of resolved values from all the input promises, in the same order as the input promises.
4. If any of the input promises reject, the returned promise rejects with the reason of the first promise that rejected.

Here's a simple example:

```
let promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 2000, 'one');
});

let promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 1000, 'two');
});

Promise.all([promise1, promise2])
  .then(values => {
    console.log(values); // ['one', 'two']
  })
  .catch(error => {
    console.error(error);
  });

```

In this example, `promise1` resolves after 2 seconds with the value 'one', and `promise2` resolves after 1 second with the value 'two'. `Promise.all()` is used to wait for both promises to resolve, and then logs the array of resolved values. If any promise had been rejected, the `catch` block would log the error.

### Syntax

The syntax for `Promise.all()` is as follows:

```
Promise.all(iterable);
```

Here, `iterable` is an iterable object such as an Array, where each item is a Promise.
`Promise.all()` returns a new Promise that fulfills when all of the promises in the iterable argument have fulfilled, or rejects as soon as one of the promises in the iterable argument rejects.

Here's an example:

```
let promise1 = Promise.resolve('Hello');
let promise2 = Promise.resolve('World');

Promise.all([promise1, promise2])
  .then(values => console.log(values))  // Logs: ['Hello', 'World']
  .catch(error => console.log(error));
```


### Polyfill

The provided polyfill is not for `Promise.all()`, but rather for `Function.prototype.apply()`. However, I can explain how a polyfill for Promise.all() would work in simple steps:

1. Define Promise.all() as a function that takes an array of promises.
2. Inside this function, create a new Promise. This Promise is what you'll return from Promise.all().
3. Inside the new Promise, keep track of how many promises have resolved with a counter, and store the resolved values in an array.
4. For each promise in the input array, convert it to a Promise if it's not already (this is what Promise.resolve() does). Then, attach a then() handler to it.
5. In the then() handler, store the resolved value in the array, and increment the counter. If the counter equals the number of promises, resolve the new Promise with the array of resolved values.
6. Also attach a catch() handler to each promise. If any promise rejects, reject the new Promise with the reason of the first promise that rejected.

Here's the code for a simple Promise.all() polyfill:

```
function PromiseAll(promiseArr) {
  const results = [];
  let resolvedPromCounter = 0;

  return new Promise((resolve, reject) => {
    promiseArr.forEach((promise, index) => {
      promise.then((val) => {
        results[index] = val;
        resolvedPromCounter += 1;
        
        if (resolvedPromCounter === promiseArr.length) {
          resolve(results)
        }
      })
        .catch(error => {
          reject(error)
        })
    })
  });
}
```



