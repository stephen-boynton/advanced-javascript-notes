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

