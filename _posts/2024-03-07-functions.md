---
title: Functions
date: 2024-03-06 20:45:08 +0000
categories: [Functions, Introduction]
tags: [rust, beginners, variables, data-types]
---

# Functions

Use the `fn` keyword to declare new functions followed by function name which has to be of `snake_case` conventional standard and a set of parentheses.

The below function represents the main entry point of a rust program.

```rust
fn main(){

}
```

Create a new function call (add_numbers) and call it from the main function.

```rust

fn main(){
  println!("hello world");

    add_numbers();

}
fn add_numbers(){
   println!(" add more numbers");
}
```

You can return early from a function by using the `return` keyword and specifying the value.

Most functions return the last value implicitly.

```rust
fn five() ->i32{
5
}

fn main(){
let x = five();

println!("The value of x is: {x}");

}
```

`->i32` this is the functions return type.
