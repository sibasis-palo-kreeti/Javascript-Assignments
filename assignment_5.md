### 1. What is an IIFE (Immediately Invoked Function Expression) and why would you use it in JavaScript? Give an example of IIFE.

An IIFE, which stands for Immediately Invoked Function Expression, is a JavaScript design pattern that involves creating and executing a function immediately after its declaration. It is typically used to create a new scope, encapsulate variables, and avoid polluting the global namespace.

An IIFE is formed by wrapping a function expression inside parentheses and immediately invoking it using additional parentheses. This way, the function is declared and executed in a single step without needing to assign it to a variable or explicitly call it later.

Here's an example of an IIFE:

```
(function() {
  const message = "Hello, World!";
  console.log(message);
})();

```

### 2. What is the purpose of using the bind() method in JavaScript and how is it different from call() and apply()?

The bind(), call(), and apply() methods in JavaScript are used to manipulate the this context and invoke functions with a specified context. Although they serve a similar purpose, they differ in how they handle the function invocation and passing arguments. Here's an overview of each method:

**bind():** The bind() method creates a new function with a specified this context and optional arguments. It does not immediately invoke the function but returns a new function that can be called later. The bind() method is useful when you want to set the this value for a function permanently.
Example:

```
const obj = {
  name: 'Sarthak',
  greet: function() {
    console.log('Hello, ' + this.name);
  }
};

const boundGreet = obj.greet.bind(obj);
boundGreet(); // Output: "Hello, Sarthak"

```

**call():** The call() method invokes a function with a specified this context and individual arguments passed directly. It immediately executes the function with the provided arguments.
Example:

```
const obj = {
  name: 'Sarthak',
  greet: function(greeting) {
    console.log(greeting + ', ' + this.name);
  }
};

obj.greet.call(obj, 'hey!'); // Output: "Hey!, Sarthak"
```

In this example, call() is used to invoke the greet function with the this context set to the obj object and the argument 'Hello'. The function is executed immediately with the provided context and arguments.

**apply():** The apply() method is similar to call() but accepts an array-like object or an actual array as the second argument. It immediately executes the function with the specified this context and an array of arguments.
Example:

```
const obj = {
  name: 'Sarthak',
  greet: function(greeting) {
    console.log(greeting + ', ' + this.name);
  }
};
obj.greet.apply(obj, ['Hi! ']); // Output: "Hi! , Sarthak"
```

In this example, apply() is used to invoke the greet function with the this context set to the obj object and an array ['Hello'] as the argument. The function is executed immediately with the provided context and arguments.

Its imortant to note that , multiple arguments cannot be passed in the apply method ,as it will take only first argument in the function call , instead we can use the `...` operator.

```
const obj={
    name:'sarthak',
    greet: function(x,y){
        console.log(x+y+this.name)
    }
};
const arr=['hi! ','what is up '];
obj.greet.apply(obj,arr); // output: hi! what is up sarthak

```

### 3. What is a Higher-Order Function (HOF) in JavaScript and how is it different from regular functions? Explain with an example.

In JavaScript, a Higher-Order Function (HOF) is a function that takes one or more functions as arguments and/or returns a function as its result. In other words, it treats functions as values, allowing you to manipulate and operate on them.

The key difference between regular functions and Higher-Order Functions is that regular functions typically operate on data, performing specific operations or calculations, whereas Higher-Order Functions operate on functions themselves, enabling composition, abstraction, and the creation of more reusable and flexible code.

Here's an example to illustrate the concept of a Higher-Order Function:

```
function multiplyBy(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
const triple = multiplyBy(3);

console.log(double(5));  // Output: 10
console.log(triple(5));  // Output: 15
```

#### Output:

```
10
15
```

### 4. Write a function called multiplyBy that takes a number as input and returns a new function that multiplies any number passed into it by the original number.

```
function multiplyBy(n){
  return (m)=>{
    return n*m;
  }
}
```

### 5. Write a function named sortArray that takes in two parameters:

#### 1. An array of numbers

#### 2. A boolean value ascending that indicates whether the array should be sorted in ascending or descending order.

**● The sortArray function should return the sorted array. Use an anonymous function to do the actual sorting, rather than using the built-in sort method.**

```
 let sorted_arr=function(arr,asc){
     if(asc==true){
         for(var i=0;i<arr.length-1;i++){
             for(var j=0;j<arr.length-1-i;j++){
                 if(arr[j]>arr[j+1]){
                     var temp=arr[j];
                     arr[j]=arr[j+1];
                     arr[j+1]=temp;
                 }
             }
         }
         return arr;
     }
         for(var i=0;i<arr.length-1;i++){
             for(var j=0;j<arr.length-1-i;j++){
                 if(arr[j]<arr[j+1]){
                     var temp=arr[j];
                     arr[j]=arr[j+1];
                     arr[j+1]=temp;
                 }
             }
         }
     return arr;
 }
 arr=[1,3,5,6,2];
 sorted_arr(arr,true);
 console.log(arr);
 sorted_arr(arr,false);
 console.log(arr);
```
