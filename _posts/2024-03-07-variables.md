---
title: Variables
date: 2024-03-06 19:38:08 +0000
categories: [Variables, Introduction]
tags: [rust, beginners, variables, introduction] # TAG names should always be lowercase
---

## Variables

By default, variables are immutable.
Rust encourages you to favour immutability inorder to take advantage of it's safety and easy concurrency features, but sometimes you might want to opt out.

The following code fragment won't run

```rust
fn main() {
    let x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

> x is immutable and can't be reassigned.
> {: .prompt-danger }

All these errors are gotten at compile time.

Adding `mut` keyword infront of x makes it mutable.

Now, we can reassign x to 6 without any issues.

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

## Constants

These are values that are bound to a name and not allowed to change.

`mut` can't be used on a constant. Meaning they are always immutable.

Declare constants using the `const` keyword.

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

Rust’s naming convention for constants is to use all uppercase with underscores between words

## Shadowing

Declaring a new variable with the same name as the previous variable is called shadowing.

```rust
fn main() {
   let x = 5;

   let x = x + 1;

   {
       let x = x * 2;
       println!("The value of x in the inner scope is: {x}");
   }

   println!("The value of x is: {x}");
}
```

Can't assign to the variable without using a let. That's the difference between shadowing and `mut`
