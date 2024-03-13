+++
title = "Javascript's `new` keyword"
date = 2019-09-20T12:59:11+01:00
tags = ["JavaScript"]
categories = ["Old blog"]
+++

# Usage
`new` is used to create new instances of objects with the help of constructor functions. While taking a look
at [prototypes](/blog/prototypes), I ran into the `new` keyword, and how it relates to the `function.prototype`
property. I thought that it might be a good exercise to look into how `new` works.

# Under the hood
According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new), there
are three steps taken when using `new`:

1. A new object is created. If the constructor function has its `prototype` property set to some object,
   the newly created object will inherit from that prototype.
2. The constructor function is called with the new object bound to `this`.
3. The result of the `new ...` expression will be what ever is returned by the constructor function. If
   nothing is returned, our newly created object (bound to `this`) will be used instead. It is usually the case
   that nothing is explicitly returned from constructor functions, but we have the option to do so.

# Noteworthy
If the constructor has no parameters, `new Foo` will be equal to `new Foo()`.

# Example

```javascript
const myPrototype = {
    protoProperty = "protolicious!"
}

function MyConstructor() {
    this.message = "hello"
}

MyConstructor.prototype = myPrototype

const myInstance = new MyConstructor
myInstance.message // "hello"
myInstance.protoProperty // "protolicious!"
```
