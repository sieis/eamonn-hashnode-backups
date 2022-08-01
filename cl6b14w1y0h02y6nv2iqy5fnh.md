## How to Check for Null in Javascript

Sometimes you've gotta check to make sure that nothing isn't actually...nothing. 😲❗❓

In JavaScript, null is a primitive type intentionally containing the value of null. Undefined is a primitive type and represents a variable you declare without initiating a value.

So, null is nothing and undefined is just missing something. 🤣

![nothing.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1659374582053/fNcavufhL.gif align="left")

Not super helpful, I know. Let's dive deeper.

## How to Define Null and Undefined Values

An example will help. Below we declare two variables. Let's keep it simple and use null and undefined to compare outcomes since they are sometimes confused because of their similarities.

```javascript
//declaring two variables: one null and one undefined.

let leviticus = null;
// leviticus is null

let dune;
// dune is undefined
```


`leviticus` is intentionally without an object value (null). Whereas `dune` is declared, yet it's unintentionally missing a value (undefined).

## How to Check for Null with typeof()

You can check for null with the `typeof()` operator in JavaScript.

```javascript
// typeof() will return 'object' when called on a null variable

console.log(typeof(leviticus))
// object

console.log(typeof(dune))
// undefined
```

Curiously, if you check with `typeof()`, a null variable will return object. This is because of a [historic bug](https://www.turbinelabs.com/blog/the-odd-history-of-javascripts-null) in JavaScript.

## How to Check for Null with Equality Operators

Another curiosity is that when you loosely check for equality using double equals `==`, `null` and `undefined` will return `true`.

```javascript
console.log(leviticus == dune)
// true

console.log(leviticus === dune)
// false

console.log(leviticus == null)
// true (but not as good a habit to use as strict equality shown in next example)
```

But when you strictly check for equality using triple equals `===`, null and undefined will return `false`.

This is because null and undefined are both [falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy) in JavaScript. Falsy means that a value is considered `false` when encountered in a Boolean (`true` or `false`) context.

JavaScript uses coercion to coerce values from one type to another in order to be able to use them in a Boolean context.

But by strictly checking for equality, you can see that they are in fact not equal.

##How to to Check for Null with Strict Equality

The best way to check for null is to use strict and explicit equality:

```javascript
console.log(leviticus === null)
// true

console.log(dune === null)
// false
```

## How to Check for Null with the `Object.is()` Method

An equally foolproof way to check for null is to use the built-in `Object.is()` method:

```javascript
console.log(Object.is(leviticus, null)
// true
            
console.log(Object.is(dune, null)
// false
```

## Summary

* `null` is a primitive type of a variable which evaluates falsy, has a `typeof()` of object, and is typically intentionally declared as `null`
* `undefined` is a primitive type of a variable which evaluates falsy, has a typeof() of undefined, and represents a variable that is declared but missing an initial value.
* `null == undefined` evaluates as true because they are loosely equal.
* `null === undefined` evaluates as false because they are not, in fact, equal.
* `<null_variable> === null` is the** best way** to strictly check for null.
* `Object.is(<null_variable>,null)` is an **equally reliable way** to check for null.

Take heart! As you've probably gathered, there are a plethora of brain teasers in the JavaScript ecosystem like this. But when you break it down, you can confidently understand them.

![denzel.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1659374974230/hO3LNZeVz.gif align="center")

## Thanks for Reading!

I hope this was a helpful breakdown for you. Keep coding, and keep leaning forward!

Come say hey to me over on Twitter: https://twitter.com/EamonnCottrell

Have a great one 👋.