+++
title = "debugger;"
date = 2019-09-25T07:52:21+01:00
tags = ["JavaScript"]
categories = ["Old blog"]
+++

A really simple one, this is, but oh how it blew my mind! In your JavaScript code, insert `debugger;`
where you might want a breakpoint. Refresh your browser with dev tools open, and voila! The debugger pauses
execution at the debugger statement.

Using the debugger statement is less typing than console logging, and you get all the variables that are in scope.
You also get the ability to step and can see how stuff changes. When console logging it might be hard to know
when stuff happens, and that might lead to a wrong idea of what's actually happening.

I'm a keyboard person. If I can avoid mousing around, I'll avoid it. Using the debugger statement, I can edit
my code, alt+tab to the browser, refresh and see what's up, and alt+tab back to the editor. I don't need the
mouse unless I want to start stepping through the code, and that probably means taking a break from editing anyways.
