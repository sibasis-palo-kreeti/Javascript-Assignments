### 1. If we execute this Javascript, what will the browser's console show?

```
var text = 'outside';
function logIt(){
    console.log(text);
    var text = 'inside';
};
logIt();
```

```
undefined
```

#### In JavaScript, variables are "hoisted" to the top of the function. When we declare text as a local variable inside logIt, it shadows the variable in the outer scope. And when a variable is declared, it is initialized to undefined. That's why undefined gets printed.

### 2. Write a regular expression to reverse the first and last name

```
var name = "Sibasis Palo";
var reverseName = name.replace(/^(\w+)\s+(\w+)$/, "$2 $1");

console.log(reverseName);
```

**Output**

```
Palo Sibasis
```

### 3. Write a Regular expression to validate email address

```
function check_match(s){
 const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    let a=regex.test(s);
    if(a==true){
    console.log("Email verified");
    return ;
    }
    console.log("Not an email");
    return ;
}
```

### 4. Find the Output

```
var x = 100;
console.log(x);
function test(){
var x = 250;
console.log(x);
if (x > 100) {
let x = 350;
console.log(x);
}
console.log(x);
}
test();
console.log(x);
```

```
100
250
350
250
100
```

### 5. What is the difference of output between these two expressions? Give your reasons for it:

#### a. 12 == “12”

#### b. 12 === “12”

#### c. Number(12) === 12

a.

```
true
```

"==" is a loose equality comparision operator which means ,it changes the data type of the two operands into a same type and then performs compariosn.

b.

```
false
```

"===" is a strict equality comparision operator so it comapres the two operands in the same data type only, hence the output is false.

c.

```
true
```

Number is an inbuilt class in javascript and Number(12) is an object of that class , on the other hand 12 is a numeric literal in JavaScript. It represents a numeric value but belongs to the same class.

### 6. What is NaN?

The NaN global property is a value representing Not-A-Number.

There are five different types of operations that return NaN:

    * Failed number conversion (e.g. explicit ones like parseInt("blabla"), Number(undefined), or implicit ones like Math.abs(undefined))
    * Math operation where the result is not a real number (e.g. Math.sqrt(-1))
    * Indeterminate form (e.g. 0 * Infinity, 1 ** Infinity, Infinity / Infinity, Infinity - Infinity)
    * A method or expression whose operand is or gets coerced to NaN (e.g. 7 ** NaN, 7 * "blabla") — this means NaN is contagious
    * Other cases where an invalid value is to be represented as a number (e.g. an invalid Date new Date("blabla").getTime(), "".charCodeAt(1))
