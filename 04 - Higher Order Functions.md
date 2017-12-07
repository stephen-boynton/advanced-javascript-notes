# Higher Order Functions

Higher Order functions that operate on other functions, by either taking them as
arguments or returning them. The fact that JavaScript supports first-class
functions, makes it possible to create Higher Order functions.

When using `this`, you can use the scope in a callback. You can either use a
variable to store the current value of this or you can use `bind`.

```js
var fullName = function() {
  setTimeout(
    function() {
      console.log(this.firstName + " " + this.lastName);
    }.bind(this),
    2000
  );
};
```

## Arrow Functions

Also can help us solve the problem of `this`.
