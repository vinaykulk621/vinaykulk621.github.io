+++
date = '2026-03-20T22:48:31+05:30'
title = 'Day 4 of 100 Days Rusty'
+++

what i learnt in Rust today

### Reference and borrowing

reference is basically pointer to a variable, below example shows the usage

```rust
fn main() {
    let mut s = String::from("Hello");
    push_world(&mut s);
    println!("{s}")
}

fn push_world(s: &mut String) {
    s.push_str("world")
}
```

---

Rules of referencing a borrow

- at any given time, you can exactly **one** **mutable** reference and any number of **immutable** reference
- reference are always valid in rust

### In rust you can not create a dangling reference (i.e; null pointer):

```rust
fn main() {
    let str = dangle(); // This will not compile,
}

fn dangle() -> &String {
    let s = String::from("dangle");     // create a string
    return &s;  //returning reference to it
} // here s is dropped as it goes out of scope, therefore creating a dangling reference
// but rust will not compile this, therefore the property, **references are always valid**
```
