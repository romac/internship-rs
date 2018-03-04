Internship
===========

[![Docs.rs](https://docs.rs/internship/badge.svg)](https://docs.rs/internship)
[![Build Status](https://travis-ci.org/HyeonuPark/internship-rs.svg?branch=master)](https://travis-ci.org/HyeonuPark/internship-rs)
[![codecov](https://codecov.io/gh/HyeonuPark/internship-rs/branch/master/graph/badge.svg)](https://codecov.io/gh/HyeonuPark/internship-rs)

Interned string and more for rust.

# What is interning?

Interning is a method to store exactly one copy of immutable data.

Imagine your program holds lots of string values, mostly same value in it,
and does not mutate them at all. If you use `String` to store them,
lots of memories are wasted just for storing identical texts.

Interning efficiently eliminate this problem by managing global pool of cache,
in the case above the type of the pool can be `HashSet<Rc<str>>`.
When you need a new owned string, first you should lookup global pool for it.
If desired string is found then use it.
If not, just create a new one and put them also to the pool.

# What does this library provide?

The core of the API is `Intern<T>`. You can think of it as `Rc<T>`,
but guaranteed uniqueness over its value within thread.

# License

This repository is dual-licensed under the [MIT license][license-mit]
and [Apache license 2.0][license-apl] at your option.
By contributing to Internship you agree that your contributions will be licensed
under these two licenses.

<!-- links -->

[license-mit]: ./LICENSE-MIT
[license-apl]: ./LICENSE-APACHE
