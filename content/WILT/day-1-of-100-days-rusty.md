+++
date = '2026-03-17T21:52:22+05:30'
title = 'Day 1 of 100 Days Rusty'
+++

I am going to learn rust by continuosly coding in rust in next 100 days.

Today is **Day-1**

---

what i learnt in Rust today

### mutable/immutable variables

Every variable in immutable by default unless specified mutable by `mut` keyword

```rust
let x = 7 // immutable
let mut y = 8 //mutable
```

### `cargo` commands:

- `cargo new hello`: create a new rust project with name hello
- `cargo check`: check if the command compiles, but not build an executable
- `cargo build`: build an executable
- `cargo run`: build an executable and run it
- `cargo add <package>` adds a package (crate)

### Infinite loop:

```rust
loop {
    println!("Eveything inside executes forever")
}
```

### Type casting/shadowing

Create a mutable variable and then, declare another variable with the same name of the type you want to parse into, then parse it

```rust
let mut num = String::new()
let num : u32 = match num.trim().parse() {
      Ok(num) => num,
      Err(_) => {
          println!("Not a number");
          break;
      }
}
```

### signed(i32) and unsigned(u32) integers

Note: Rust performs modulo arithmetic/wraps around the values in case of buffer overflow in release mode, in debug mode: it panics

| signed(i32)                                          | unsinged(u32)                           |
| ---------------------------------------------------- | --------------------------------------- |
| -2,147,483,648 to +2,147,483,648                     | 0 to +4,294,967,295                     |
| use when you need both negative and positive numbers | use when you need only positive numbers |

---

I wrote a simple number guessing game, following [doc.rust-lang.org/stable/book](https://doc.rust-lang.org/stable/book/print.html)

```rust
use rand::RngExt;
use std::{cmp::Ordering, io};

fn main() {
    println!("Guess the number");

    let secret_number = rand::rng().random_range(1..=100);

    loop {
        let mut guess = String::new();
        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line!");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please enter a number");
                continue;
            }
        };

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Higher"),
            Ordering::Greater => println!("Lower"),
            Ordering::Equal => {
                println!("Bingoo!!!");
                break;
            }
        }
    }
}
```
