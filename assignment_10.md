### 1. Define ‘Asynchronous programming’.
Asynchronous programming is a programming paradigm that allows tasks to be executed concurrently and independently from the main execution flow of a program. In asynchronous programming, operations do not block the execution of the program, enabling the program to perform other tasks while waiting for a particular operation to complete.

The primary goal of asynchronous programming is to optimize resource utilization and improve the overall efficiency of a program, especially in scenarios where tasks may involve I/O operations or waiting for external events (e.g., network requests, file operations, timers).

In traditional (synchronous) programming, each operation is executed sequentially, one after the other. If an operation takes a long time to complete, it can cause the entire program to halt until the operation finishes. Asynchronous programming addresses this issue by allowing tasks to be scheduled and executed independently, without waiting for the completion of previous tasks.

Asynchronous programming is commonly used in scenarios such as:

1. I/O Operations : Reading from files, making network requests, and accessing databases are typically slow compared to CPU processing. Using asynchronous operations allows the program to continue execution while waiting for these operations to complete.

2. Event Handling: Asynchronous programming is crucial in event-driven environments where the program needs to respond to various events asynchronously, such as user input, timer events, or external signals.

3. Concurrency: Asynchronous programming is often used to manage concurrent execution of multiple tasks, making it possible to run parallel operations and maximize resource usage.

In many programming languages, asynchronous programming is implemented using callbacks, promises, or async/await syntax. These mechanisms help manage the flow of asynchronous operations and handle the results when they are ready.

### 2. What are callbacks? Give an example.

A callback is a function that is passed as an argument to another function and is intended to be executed after the completion of that function. The primary purpose of using callbacks is to enable asynchronous behavior in JavaScript, where tasks can be executed out of the regular execution flow.
The setTimeout() function is commonly used to demonstrate asynchronous behavior since it simulates a delay without blocking the program's execution.
In this example, we'll use both callbacks and async/await to illustrate different ways of handling asynchronous operations:

```
// Asynchronous function with a callback
function delayedCallback(callback) {
  setTimeout(() => {
    console.log('Async operation complete!');
    callback();
  }, 2000); // Simulating a 2-second delay
}

console.log('Start');

delayedCallback(() => {
  console.log('Callback executed!');
});

console.log('End');
```

### 3. What is a promise? What are its different states? Also write the methods which change a promise to their corresponding states.

In JavaScript, a Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a way to handle asynchronous code in a more organized and readable manner compared to traditional callbacks.

Promises have three different states:

Pending: The initial state of a promise. This means the asynchronous operation is still ongoing, and the promise is neither fulfilled nor rejected yet.

Fulfilled: The state of a promise when the asynchronous operation is successfully completed. The promise now has a resulting value, which can be accessed using the then() method.

Rejected: The state of a promise when the asynchronous operation encounters an error or fails. The promise now has a reason for rejection, which can be accessed using the catch() method or the second argument of the then() method.

Methods that change a promise to their corresponding states:

Resolve (Fulfill) a Promise: The resolve function is used to fulfill a promise with a value. Once a promise is resolved, it moves from the pending state to the fulfilled state.

Reject a Promise: The reject function is used to reject a promise with a reason (usually an error). Once a promise is rejected, it moves from the pending state to the rejected state.

Here's an example of a simple promise:

```
// Creating a promise
const myPromise = new Promise((resolve, reject) => {
  // Simulate an asynchronous operation (e.g., fetching data from an API)
  setTimeout(() => {
    const success = true; // Simulating a successful operation, change to false to simulate a rejection
    if (success) {
      resolve('Promise resolved with success!');
    } else {
      reject(new Error('Promise rejected with an error!'));
    }
  }, 2000); // Simulating a 2-second delay
});

// Using the promise with 'then' and 'catch' methods
myPromise
  .then(result => {
    console.log('Fulfilled:', result);
  })
  .catch(error => {
    console.error('Rejected:', error.message);
  });
```

Output (when success is set to true):

```
Fulfilled: Promise resolved with success!
```

Output (when success is set to false):

```
Rejected: Promise rejected with an error!
```

In this example, myPromise represents an asynchronous operation that resolves with a success message when success is set to true, and rejects with an error message when success is set to false. We use the then() method to handle the fulfilled state and the catch() method to handle the rejected state of the promise.

Promises provide a powerful and readable way to handle asynchronous operations and handle success and error scenarios in a more structured manner. Additionally, they make it easier to chain multiple asynchronous operations together and manage their results.

### 4. Write a JS promise which resolves after 5s, with a value of “Hello Javascript”. Also, write code to print the length of this string after resolving.

```
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true; // Simulating a successful operation, change to false to simulate a rejection
    if (success) {
      resolve('Hello Javascript');
    } else {
      reject(new Error('Promise rejected with an error!'));
    }
  }, 5000); // Simulating a 5-second delay
});


myPromise
  .then(result => {
    console.log(result +', length of string= '+result.length);
  })
  .catch(error => {
    console.error('Rejected:', error.message);
  });
```

### 5. What is ‘callback hell’ problem? How does the use of promises help in reducing this?

'Callback hell,' also known as the 'pyramid of doom,' is a term used to describe a situation in asynchronous programming where multiple nested callbacks create a deeply indented and hard-to-read code structure. This occurs when dealing with multiple asynchronous operations that depend on each other's results, and the code ends up being heavily nested due to the use of callbacks.

Here's an example of callback hell:

```
asyncFunction1(() => {
  asyncFunction2(() => {
    asyncFunction3(() => {
      asyncFunction4(() => {
        // and so on...
      });
    });
  });
});
```

In this example, we have four asynchronous functions (asyncFunction1, asyncFunction2, asyncFunction3, and asyncFunction4). Each of these functions takes a callback as an argument to be executed once the asynchronous operation is completed. When you have many such nested callbacks, the code becomes hard to read and maintain, leading to what is called "callback hell."

Promises provide a more structured and flat approach to handling asynchronous operations. They allow you to chain multiple asynchronous operations in a way that is easier to read and understand. By using promises, you can convert the deeply nested callbacks into a sequence of .then() and .catch() calls, significantly reducing the callback hell problem.

Here's the same example refactored using promises:

```
asyncFunction1()
  .then(() => asyncFunction2())
  .then(() => asyncFunction3())
  .then(() => asyncFunction4())
  .then(() => {
    // Code after all asynchronous operations are completed
  })
  .catch(error => {
    // Handle any errors from the asynchronous operations
  });
```

By adopting promises, we can significantly reduce the nesting and improve the readability of your asynchronous code, making it more maintainable and easier to reason about. Additionally, with the introduction of async/await in modern JavaScript, you can further simplify the handling of promises, making asynchronous code even more concise and clear.

### 6. What is the difference between Promise.all() and Promise.allSettled()? Give an example.

Both Promise.all() and Promise.allSettled() are methods used to handle multiple promises in parallel.

1. Promise.all():
   Promise.all() takes an iterable (usually an array) of promises as input and returns a new promise.
   This method resolves when all the promises in the input array have resolved successfully (fulfilled) and rejects if any of the promises are rejected.
   If all promises fulfill successfully, Promise.all() returns an array with the fulfillment values of the original promises, in the same order as provided.
   If any promise is rejected, Promise.all() immediately rejects with the reason of the first promise that was rejected.
   Example using Promise.all():

```
const promise1 = Promise.resolve('Resolved Promise 1');
const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => reject('Rejected Promise 2'), 1000);
});
const promise3 = Promise.resolve('Resolved Promise 3');

Promise.all([promise1, promise2, promise3])
  .then(results => {
    console.log('All promises fulfilled:', results);
  })
  .catch(error => {
    console.error('At least one promise rejected:', error);
  });
```

Output (after 1 second when promise2 rejects):

```
At least one promise rejected: Rejected Promise 2
```

2. Promise.allSettled():
   Promise.allSettled() also takes an iterable (usually an array) of promises as input and returns a new promise.
   This method resolves when all the promises in the input array have either fulfilled or rejected (settled). It does not reject even if some promises are rejected.
   The returned promise is an array of objects, each representing the outcome of each promise. The objects contain either a status property with values 'fulfilled' or 'rejected' and a value property with the fulfilled value or a reason property with the rejection reason.
   Example using Promise.allSettled():

```
const promise1 = Promise.resolve('Resolved Promise 1');
const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => reject('Rejected Promise 2'), 1000);
});
const promise3 = Promise.resolve('Resolved Promise 3');

Promise.allSettled([promise1, promise2, promise3])
  .then(results => {
    console.log('All promises settled:', results);
  });
```

Output (after 1 second when promise2 rejects):

```
All promises settled: [
  { status: 'fulfilled', value: 'Resolved Promise 1' },
  { status: 'rejected', reason: 'Rejected Promise 2' },
  { status: 'fulfilled', value: 'Resolved Promise 3' }
]
```

### 7. Write a JS function that throws a SyntaxError if the value age (passed as parameter of the function) is greater than 80. The error message will be “You are too old."

```
function fn(age){
    try{
    if(age>80){
        throw new Error('You are too old');
    }
    return ;
    }catch (error){
        console.log(error.message);
    }
}

```

### 8. For this code, answer the following:

```
const p1 = Promise.any([
new Promise((resolve, reject) => setTimeout(() => reject('Part 1 is rejected.'), 2000)),
new Promise((resolve, reject) => setTimeout(() => resolve('Part 2 is resolved.' ), 5000)),]);
p1.then((res) => console.log(res)).catch((res) => console.log(res))
```

#### a. Write the output of this code. Briefly explain the reasoning.

Output:

```
Part 2 is resolved.
```

Explanation:
The Promise.any() method checks for if any of the promises that are passed into it's argument are resolved or not . In the above example , the promise 2 is resolved after 5 seconds , promise 1 is rejected after 2 seconds , so the only output will be the output of promise one which is printed after 5 seconds.

#### b. What will be the output of this code if Promise.any() is replaced by Promise.race()? Is the output for this case generated faster or slower? Give reasons.

Output:

```
Part 1 is rejected.
```

Explanation:
The output is such because the Promise.race() method checks for the fastest promise in its argument to get executed , in the above case the fastest promise was promise 1 with a timeout of 2 secs , thats why the output is 'Part 1 is rejected.' which is printed after 2 secs.

### 9. Given is a code snippet

```
const p = new Promise((resolve, reject) => {
resolve(“Part a”);
resolve(“Part b”);
})
p.then((res)=>console.log(res));
```

#### a. What will be the output of the above? Justify your answer.

```
const p = new Promise((resolve, reject) => {resolve("Part a"); resolve(“Part b”);})
SyntaxError: Invalid or unexpected token
    at internalCompileFunction (node:internal/vm:73:18)
    at wrapSafe (node:internal/modules/cjs/loader:1178:20)
    at Module._compile (node:internal/modules/cjs/loader:1220:27)
    at Module._extensions..js (node:internal/modules/cjs/loader:1310:10)
    at Module.load (node:internal/modules/cjs/loader:1119:32)
    at Module._load (node:internal/modules/cjs/loader:960:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:23:47
```

Explaination :
The error we encountered is due to a syntax issue in our code. The problem lies in the way we are using resolve in the Promise constructor. A Promise can only be resolved once, but in our code, we are calling resolve twice, which is not allowed.

#### b. What code should we write to get both the resolved results

If we need to resolve the Promise with multiple values, we can return an array of values or an object containing the desired parts:

```
const p = new Promise((resolve, reject) => {
  const result = {
    partA: "Part a",
    partB: "Part b",
  };
  resolve(result);
});
```

output:

```
{ partA: 'Part a', partB: 'Part b' }
```

This way, you can resolve the Promise with a single value (in this case, an object), containing both "Part a" and "Part b". When the Promise is resolved, you can access the parts accordingly.

### 10. Using async / await syntax, and fetch(), make an API request to https://official-joke-api.appspot.com/random_joke and console the results. Also handle errors if any.

```
async function fetchJoke() {
  try {
    const response = await fetch("https://official-joke-api.appspot.com/random_joke");
    if (!response.ok) {
      throw new Error("Request failed with status " + response.status);
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("An error occurred:", error.message);
  }
}

fetchJoke();
```
