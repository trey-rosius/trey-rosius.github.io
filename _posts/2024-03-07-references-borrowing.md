---
title: References And Borrowing
date: 2024-03-07 00:30:08 +0000
categories: [Getting Started, Introduction]
tags: [rust, beginners, philosophy, introduction, borrowing, references] # TAG names should always be lowercase
---

## References and Borrowing

A reference is an address we can follow to access data owned by some other value.

Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type for the
life of that reference.

```rust

fn main(){
 let s1 = String::from("hello");

 let len = calculate_length(&s1);

 println!("The length of '{}' is {}.", s1, len);



}

fn calculate_length(s: &String) -> usize{


s.len()
}
```

The act of creating a reference is called borrowing.

Mutable references have one big restriction: if you have a mutable reference to a value, you can have no other references to that value.

This would fail.

```rust
    let mut s = String::from("hello");

    let r1 = &mut s;
    let r2 = &mut s;

    println!("{}, {}", r1, r2);

```

## The Rules of References

Let’s recap what we’ve discussed in references:

At any given time, you can have either one mutable reference or any number of immutable references.
References must always be valid.
