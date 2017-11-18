# Constructors

* Constructors are just a function that is invoked using new. 
* A constructor returns an object.
*  Constructors are used to create multiple similar objects.
*  The returned objects share the same prototype which comes from the constructor.

## Invoking Functions as Constructors: The Magic of New

Use uppercase, so people know if it's a constructor.

```js
const Greeting = function() {

}

const greet1 = new Greeting();
const greet2 = new Greeting();
```

`greet1` and `greet2` are not `===`. But they are both `instanceof` Greeting.

`greet1` is an object, it's prototype is Object.

The `__proto__` of Greeting is a function prototype, but the `prototype` is Object. _confusing_

## The value of This with a Constructor

```js

function Greeting() {
    console.log(this)
}

Greeting(); //Window object

new Greeting(); // Greeting is the value of this in a constructor function.
```

`new` creates a new object that is bound to Greeting. That's what gives constructor functions value. We use that power with `this`.

```js
function Users(fname, lname) {
    this.firstName = fname;
    this.lastName = lname;
    this.fullName = function () {
        return `${this.firstName} ${this.lastName}`;
    }
}

const user1 = new Users("James", "Johnson");

const user2 = new Uswers = new Users("Mary", "Smith");

```

Danger of constructor functions without the `new` keyword. This is why you always use an uppercase letter. The value of `this` will be the GLOBAL OBJECT. If you don't use `new`, it's going to define variables in the GLOBAL SPACE. Which is a big ol' no-no.
