+++
title = "First impression of Rust"
date = 2019-09-11T05:34:21+01:00
categories = ["Old blog"]
+++

I just started looking at Rust. I've been putting it off for a while since I've been focusing on Go,
and haven't really had the bandwidth to learn another language. But yesterday I was inspired by a colleague
of mine. And so I present my initial thoughts.

# Getting started
When I first started with Go, it could be a bit of a hassle to get things set up, with GOPATH and such.
With Rust I felt it was way easier. Though, I will have to take into account that I'm comparing apples to
oranges. Setting up Go these days is a bit easier, and I have no idea wether Rust has been difficult to set up
in the past. But looking at it here and now, it was only a matter of installing `rustup`, and things just work.

# Learning Rust
One thing that got me excited about Go was the (in my opinion) good and easy-to-read documentation of the
standard library. It seems that Rust has taken it a few steps further. Similar to Go, Rust comes with utilities
to browse documentation locally in your web browser. This is a huge deal for me, since most of my learning time is
on the commuter train with an unstable Internet connection.

I haven't really looked into it yet, but it seems that Rust has some really neat ways of documenting ones code,
and generating web docuementation from it. Another super sweet feature is that the documentation comes with an e-book,
usually just called "the book".

# Package management
One place where Rust seems to out-shine Go is in the space of package management. I've been happy so far
with Go's way of doing things, since I've usually only done small projects without complex dependencies. The
`go get` command was simple and worked. Vendoring worked. But at this point the Go team has started working on ways
to better manage dependencies (such as modules). Rust seems to give you a lot of this out of the box. The tool
`cargo` is used to manage your dependencies, and seems to do a good job. Please note that these are just my
initial thoughts. I'm sure that I with time will find things that I wish were different. It's not a perfect world.

# Standard libarary
The great standard library of Go is something I love. Same with Python. I don't know yet, but my initial
impressions (which are just that - impressions) are that Rust does not have the same rich standard library.
For example - a tutorial in "the book" shows you how to write a number guessing game. This requires generating
a random number, functionality that I've come to take for granted that it should exist in the standard library.
This is not the case in Rust. However, there is a library (written by the Rust team I believe) that is easily
installed with `cargo`.

# Enumerated types
I've come to get accustomed to Go's multiple return values. Especially when it comes to error handling. It's
very common practice that the last return value of a function is an error value which you check right after the
function returns to make sure everything went ok.
Rust instead uses enumerated types. One such type is the `Result` type, which is an enumerated type. After calling
a function that returns an enumerated type you check the return value. The nice thing about checking (or "matching")
enumerated types is that the compiler forces you to check every case. That way, you can know at compile time that
you didn't leave any cases out.

# Conclusion
Rust seems to have a lot going for it. I'm curious, but probably not curious enough to keep digging. Especially
since I'm mostly in the web API space, which is where Go really shines. I'll probably revisit Rust at
some point, but right now, I have other things that require my attention.
