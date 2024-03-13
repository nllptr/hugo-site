+++
title = "Javascript Prototypes"
date = 2019-09-19T05:29:15+01:00
tags = ["JavaScript"]
categories = ["Old blog"]
+++

# Objects and the prototype chain
In JavaScript there is only one construct - objects. Objects have a property that links that object to its prototype.
That prototype in turn has a link to its prototype, and so this chain goes on until someone has a prototype of `null`
This is what we know as the "prototype chain". The most common "top level object" is `Object`, which has a
`null` prototype. Not sure, but the wording at
[Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
leads me to believe that there are other top level objects.

# JavaScript inheritance
When we access a property on an object, JavaScript first looks at that object's "own properties". If the property is
not found, the next step is to take a look at that object's prototype to see if it's present there. If not,
then we move up the prototype chain either until the property is found or until we reach the end of the chain.

# Accessing
Since ECMAScript 2015, we access the prototype by using `Object.getPrototypeOf(myObject)` or
`Object.setPrototypeOf(myObject)` respectively. We could also use `myObject.__proto__`, which is implemented by many
browsers (but NOT standard).

# Pitfall
Do not confuse `__proto__` and `Object.getPrototypeOf()` with the property `func.prototype`. Note that this is a
property that exists on **functions**. When using that function as a constructor, JavaScript looks to the `prototype`
property to see what should be the pototype of the created object.

```javascript
const myProto = {
    protoProp: "hello"
}

function MyConstructor(thing) {
    this.thing = thing
}

MyConstructor.prototype = myProto
MyInstance = new MyConstructor("thing")

// MyInstance would look like this:
MyConstructor {
    thing: "thing"
    __proto__ : {
        protoProp: "hello",
    }
}
```

