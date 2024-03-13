+++
title = "Javascript Promises"
date = 2019-08-30T14:00:34+01:00
tags = ["JavaScript"]
categories = ["Old blog"]
+++

# In short
Promises makes chaining asynchronous tasks a little prettier than its deeply nested callback counterpart. For example:
```javascript
myPromise
    .then(doTheFirstThing)
    .then(doTheSecondThing)
    .catch(failHandler)
```
This chainability is argued to be more easily reasoned about. Promises also come with some guarantees:
1. Callbacks won't be called before completion of the current run of the event loop, which avoids race conditions.
2. Callbacks added with `then()` even *after* the success/failure of async operation will be called.
3. Multiple callbacks can be added with `then()`. They will be executed in order.
4. Callbacks are called one time at most.

## Elaboration

`catch(failureCallback)` is short for `then(null, failureCallback)`.

Regarding guarantee #1, some clarification might be needed. The JavaScript event loop does not preemt "the
current run" (i.e. the currently running function). This makes reasoning about our code easier, but it also means
that for example mouse events can be delayed by a long-running function.
When using callbacks, it's harder to know what is actually running, because we have functions calling functions.

Learned from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

