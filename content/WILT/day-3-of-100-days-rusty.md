+++
date = '2026-03-19T23:24:38+05:30'
title = 'Day 3 of 100 Days Rusty'
+++

what i learnt in Rust today

### Ownership

It's a set of rules every value has to follow for memory management

1. Each value has an owner.
2. There can only be one owner for a value at a given time.
3. Once the owner gets out of scope, value is dropped.

- `drop`:
  similar to C/C++ `free()` API
- shollow copy and deep copy:
  - rust by default does **not** create deep copy of a variable
  - use `.clone()` method to create deep copy on a variable
- passing a variable as a parameter to a function is similar to declairing a variable,
  - which means ownership of that variable is passed to that function, and it is no longer accessible to main function

  ```rust
    fn main() {
      let s = String::from("Hello");

      some_fu(s); // variable s ownerships is passed to some_fn()

      println!("{s}")  // s is no longer accessible here
    }

    fn some_fn(s: String){
        println!("{s}")
    }  // s is dropped here
  ```
