+++
date = '2026-03-26T23:22:42+05:30'
title = 'Day 5 of 100 Days Rusty'
+++

what i learnt in Rust today

### structs

- structs in rust are similar to go's structs
- idea of structs is to be able to store various datatypes into one variable

### slices

draft = true

- it is basically list indexing in python

```rust

let a = [1, 2, 3, 4, 5]
let all = &a[..] // copy everything
let first = &a[..3] // first 3 elements
let last = &a[3..] // last elements

```
