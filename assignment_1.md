### 1. Write a program that declares a variable using var, let, and const and prints the value to the console.

```
var a = 5;
console.log(a);
const b = 6;
console.log(b);
let c = 7.89;
console.log(c);
```

### 2. Write a program that reassigns a value to a variable declared with let and prints the new value to the console.

```
let x=555;
x=444;
console.log(x);
```

### 3. Write a program that tries to reassign a value to a variable declared with const and prints the message to the console

```
const x=555;
b=444;
console.log(x);
```

**Output**

```
Uncaught TypeError: Assignment to constant variable.
```

### 4. Write a program to declare a const, let, var variable within an if statement and try to access the variable outside the if block, what is the result?

1.var declaration:

```
if(true){
var x=444;
}
console.log(x);
```

**Output**

```
444
```

2.const declaration:

```
if(true){
const y=555;
}
console.log(y);
```

**Output**

```
Uncaught ReferenceError: y is not defined
```

3.let declaration:

```
if(true){
let z=666;
}
console.log(z);
```

**Output**

```
Uncaught ReferenceError: z is not defined
```

### 5. Write a program that concatenates two or more strings and prints the result to the console.

```
let s1 = "Sibasis";
let s2 = "Palo";
let s3=s1+" "+s2;
console.log(s3);
```

### 6. Write a program that takes a string as input and prints the length of the string to the console.\*\*

```
let s1 = "Sibasis";
console.log(s1.length);
```

### 7. Write a program that converts a string to uppercase and prints the result to the console.

```
let s1 = "Sibasis";
console.log(s1.toUpperCase());
```
