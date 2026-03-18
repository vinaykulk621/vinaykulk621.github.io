+++
date = '2026-03-18T22:41:39+05:30'
title = 'Day 2 of 100 Days Rusty'
+++

what i learnt in Rust today

Today i mainly learnt following things:

- basic data types
- fn
- loops

### Data Types

![Data Types](/images/data-types.png "Data Types in `rust`")

- `char` is similar to `rune` from GO programing language
  - it's of size 8 bits
  - should be enclosed in 'single quotes'
  ```rust
  let c: char = 'Z'; // can take any single charecter/emoji etc..
  ```
- `arrays` are similar to C programming language(fixed size, same type, accessing elements)
- array comperhension??
  ```rust
  let num = [1; 4]; // num = [1, 1, 1, 1]
  ```
  In the above code, you are basically telling repeat number **1**, 4 times
- `tuples` are similar to tuples in python

  ```rust
  let tup: (i32, u32, f32) = (-32, 32, 32.0);
  println!("signed: {}, unsigned: {}, float: {}", tup.0, tup.1, tup.2);
  ```

### loops

loops are pretty interesting in rust

- normal loop

  ```rust
  loop {
      println!("looooop!!");
  }
  ```

- named loop

  ```rust
  'named_loop: loop {
      println!("named loop!!");
      let mut x = 0;

      loop {
          println!("unnamed inner loop, x:{x}");
          x+=1
          if x==2 {
              println!("breaking from inner loop, x:{x}");
              break;
          }

          if x==4 {
              println!("breaking from outer named loop, x:{x}");
              break 'named_loop
          }
      }
  }

  // prints the following
  // named loop!!
  // unnamed inner loop, x:0
  // unnamed inner loop, x:1
  // breaking from inner loop, x:2
  // unnamed inner loop, x:3
  // breaking from outer named loop, x:4
  ```

- for loop
  ```rust
  let num = [1, 2, 3]
  for n in num {
      println!(n)
  }
  ```

---

MISC:

- Rust uses snake_case
- Unlike JS/Python rust does not have truthy/falsy values
