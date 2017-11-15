# Advanced Objects and Functions

### Primitive Data Types
* Strings
* Numbers
* Booleans
* undefined
* null
* Symbols

All above are not objects, but do have Object wrappers.

When a function is attached to an object, it is called a method. 

There are [[Code]] and [[Call]] properties of every object.

## Functions are Objects 

Function declaration:
```js
function func() {
    //code
}
```

Function expression:
```js
const x = function func() {
    //code
}
```

The declaration will be hoisted and be able to be used before it's officially created, however, in the case of the expression, only the variable will be hoisted, but the assignment of function to that variable will not.

## First Class Functions

```js
const sum = function(x, y) {
    return x + y;
}

const run = function(fn, a, b) {
    console.log(fn(a,b));
}

run(sum, 10, 5); //15

run((a,b) => {
    return x*y;
}, 2, 4); // 8

```

Passing functions around!

## Invoking Functions

Call or execute a function. FOUR ways to do this.

* as a function
* as a method
* as a constructor (new)
* indirectly using call() and apply();


Functions also get `this` and `args`. Depending on how you call the function (from a list above), makes `this` mean something different.

The amount of params passed in doesn't matter. JS will take whatever you give it.

A function called in a global space will call the global object as `this`.

`Arguments` are array like, but they are NOT an array. You cannot use all of the array methods on `arguments`.

You should always define parameters because it makes it easier to tell what that function is supposed to be used for. There are rare cases where you may want to use the arguments object, though.

```js
const sumIt = function () {
    let sum = 0;
    for (let i = 0; i < arguments.length; i++) {

    }
}
```

## Creating JavaScript Objects

Ways to construct: 
* Object literal
* Object constructor

If you call this inside of an object literal construction method. The `this` keyword will refer to the object itself.

The `in` keyword can test to see if a property exists in an object. `hasOwnProperty` will tell you it's on original properties.

