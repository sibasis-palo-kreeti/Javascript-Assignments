### 1 Create a Class AlertBox.

#### ii Create a new instance of AlertBox and show a message.

```
class AlertBox{
    constructor(applicationName){
        this.applicationName=applicationName;
    }
    showAlertBox(message){
          console.log(this.applicationName+' '+message);
    }
}
const a=new AlertBox("Alertbox");
a.showAlertBox("is now well and alive!");
```

### 2 Create a new class SuccessMessage which extends AlertBox. Override the showAlertBox method.

```
class SuccessMessage extends AlertBox{
    showAlertBox(message){
          console.log(this.applicationName+' success '+message);
    }
}
const b=new SuccessMessage("SuccessBox");
b.showAlertBox('successfull!!');
```

### 3 What is inheritance and prototypes? Can you achieve inheritance using prototypes If yes, how? ( Give examples )

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows objects or classes to inherit properties and behaviors from other objects or classes. It enables code reuse, promotes modularity, and helps create hierarchical relationships between objects.

Prototypes, in the context of JavaScript, are mechanisms that allow objects to inherit properties and methods from other objects. Every JavaScript object has an internal link to another object called its prototype. When you access a property or method on an object, and it doesn't exist on that object itself, JavaScript will look for it in the prototype chain.

```
// Prototype-based inheritance (Traditional JavaScript)
function Animal(name) {
  this.name = name;
}

Animal.prototype.sayHello = function() {
  console.log(`Hello, I'm ${this.name}`);
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.bark = function() {
  console.log('Woof! Woof!');
};

const animal = new Animal('Generic Animal');
const dog = new Dog('Buddy', 'Golden Retriever');

animal.sayHello(); // Output: Hello, I'm Generic Animal
dog.sayHello();    // Output: Hello, I'm Buddy
dog.bark();        // Output: Woof! Woof!
```

In this example, we use constructor functions to define the Animal and Dog classes. The Dog prototype is linked to the Animal prototype using Object.create(Animal.prototype), and we manually set the constructor property to Dog. The methods are defined on the prototypes using Animal.prototype.methodName = function().

Both examples achieve inheritance, but the difference lies in the syntax and approach. The class-based inheritance (ES6) provides a more structured and intuitive way to define classes and their relationships, while the prototype-based approach (Traditional JavaScript) offers a more direct manipulation of object prototypes. It's essential to understand both approaches, as they are both used in different codebases and libraries.
