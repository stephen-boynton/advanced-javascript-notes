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
    fun(2); //same as fun1 call
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
    })
