# this

`this` is determined at runtime. Depending on the code, it may be something different.

`this` is:
* Established at runtime, when a function is invoked
* determined by the type of invocation
* a reference to an object

`this` is not:
* The function. Though it is established when the function is invoked, it is not the function.

The binding of a value to `this` can be implicit (set by JavaScript) or explicit (set by you).

## this in Normal Function Invocation

How the function is invoked, not where the function is defined.

`this` IS NOT THE FUNCTION. 

```js
let name = "global"
const fun1 = function () {
    let name = "fun1";
    console.log("From fun1 ---");
    console.log(this); // Window
    console.log(this.name); //"global" or "Window.name"
    fun2(); //same as fun1 call
}

const fun2 = function() {
    let name = "fun2";
    console.log("From fun2 ---");
    console.log(this); // Window
    console.log(this.name); //"global" or "Window.name"
}
```

Even though fun2 is called within fun1, the scope is the same as fun1.

```js
let name = "global"
const fun1 = function () {
    let name = "fun1";
    console.log("From fun1 ---");
    console.log(this); // Window
    console.log(this.name); //"global" or "Window.name"
    return function fun2 () {
        let name = "fun2";
        console.log("From fun2 ---");
        console.log(this); // Window
        console.log(this.name); //"global" or "Window.name"
    }
}
```

Even the above example is the same. Doesn't matter where the function is declared. Depends on HOW it is invoked.

```js

const runIt = function(fn) {
    let name = "runIT";
    console.log("From runIt ---");
    console.log(this); // Window
    console.log(this.name); //"global" or "Window.name"
    fn()
}

runIt(function fun2 () {
    let name = "fun2";
    console.log("From fun2 ---");
    console.log(this); // Window
    console.log(this.name); //"global" or "Window.name"
});

```

Still the same!!!!

## Normal Function Invocation Using Strict Mode

If you are in strict mode, `this` will not be bound to the global object by default.

Using the examples above, `this` will be undefined.

## this with Method Invocation

```js
var name = "global";

const obj1 = {
    name: "obj1"
    fun1: function () {
        let name = "fun1";
        console.log("From fun1 ---");
        console.log(this); // obj
        console.log(this.name); //"obj1"
    }
};

obj1.fun1();
```

`this` is the Object! This is not because the method was defined inside the object. This is because the object was USED to invoke it.

```js
var name = "global";

const obj1 = {
    name: "obj1",
    fun1: function () {
        let name = "fun1";
        console.log("From fun1 ---");
        console.log(this); // obj
        console.log(this.name); //"obj1"
    }
};

// obj1.fun1();

const obj2 = {
    name: "obj2",
    fun2: obj1.fun1
}

obj2.fun2(); // OBJECT 2 is now this!
```

See again how the method is being called and not where the method is defined. The method is defined in obj1 but invoked by obj2, thus obj2 is now `this`.

Finally a simple explanation.

```js
const name = "global";

const fun3 = function() {
    console.log("from fun3");
    console.log(this);
    console.log(this.name);
}

this.fun3() // this is Window and Window.name

const obj4 = {
    name: "obj4",
    obj5: {
        name: "obj5",
        fun5: function () {
            let name = "fun5";
            console.log("From fun5 ---");
            console.log(this);
            console.log(this.name);
        }
    }
};

obj4.obj5.fun5();
```

^^ obj5 is `this`. Pretty great.

## Attaching a Method to a Function

```js
const fun6 = function () {
    console.log(this);
}

fun6.name = "fun6";
fun6.fun7 = function() {
    let name = "fun7";
    console.log("From fun7 ---");
    console.log(this);// fun 6
    console.log(this.name); // fun6
}

fun6.fun7();
```

Functions are objects, so fun6 gets a method like an object and is thus is the object for `this`

All of this stuff is IMPLICIT BINDING.

## The Prototype

Every object has a set of its own properties that are defined on the object, but some are already defined in the object's prototype.

Almost every object is linked to another object. That linked object is called the prototype.

Objects inherit properties and methods from its prototype ancestry.

A prototype is automatically assigned to any object.

*Reminder: everything in JS is an object, except for primitives*

You can define an object's prototype.

## The Function Prototype

Functions are objects, therefore, they have a prototype!

These methods are on functions:
* apply
* bind
* call

You can use these functions to change the value you `this`.

## Call and Apply Methods
