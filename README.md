# Class Extensions and Inheritance: `super`

## Learning Goals

- Use the `super` method

## Introduction

In addition to extending classes, we can build methods that perform
actions on instance data that is specific to the child class. 

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} makes a loud sound!`
  }
}

// Inherits from Pet
class Dog extends Pet { ... }

let dog = new Dog("Shadow");

dog.speak(); // Shadow makes a loud sound!
```

We already have a method for `speak` on our `Pet` class, so how can this
be leveraged to create independent methods that the parent class does
not share? This is where the `super` method comes in. In this lesson,
we'll illustrate how `super` works.

## Use the `super` Method

In the code below, we have 2 JavaScript classes: `Pet` and `Dog`. The `Dog`
class is a _subclass_ or _child_ class of `Pet` and it uses the `extends`
keyword to inherit methods from the parent class.

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} makes a loud sound!`
  }
}

// Inherits from Pet
class Dog extends Pet {
  constructor(name, breed) {
    super(name)
    this.breed = breed;
  }
  bark() {
    return `${super.speak()} ${this.name} the ${this.breed} says woof!`;
  }
}

let dog = new Dog("Spot", "foxhound");

dog.speak(); // Spot makes a loud sound!
dog.bark(); // Spot makes a loud sound! Spot the foxhound says woof!
```
With `super`, we can inherit functionality from the parent class in two different ways:
In `Dog`s `constructor`, `super` is used as a `method`. Whereas, `Dog`'s `bark()`
method used `super` as an `object`. When the `super` keyword is used as a method, it
calls the parent class `Pet` with the parameters passed to `Dog`. This is to ensure
that `Dog` is an instance of `Pet`. When `super` is used as an `object` that refers to
a `Pet` instance, it can call methods of the parent class `Pet` explicitly.

**NOTE:** Instead of overwriting `speak()` from the parent class of `Pet`, we used
`speak()` in order to build new functionality into the child class. We want `dog.speak()`
or any other instance of the `Dog` class to still have the same return value as its parent.

## Conclusion

In this lesson, we dive deeper into class extensions and inheritance in JavaScript. In
combination with `extends`, `super` allows us to create custom `constructor` functions
and pass down properties and method values.

## Resources

* [Inheritance in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)
* [“Super” and “Extends” In JavaScript ES6 - Understanding The Tough Parts](https://medium.com/beginners-guide-to-mobile-web-development/super-and-extends-in-javascript-es6-understanding-the-tough-parts-6120372d3420)
* [Class inheritance, super](https://javascript.info/class-inheritance)