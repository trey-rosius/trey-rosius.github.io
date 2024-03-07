---
title: Ownership
date: 2024-03-07 00:14:08 +0000
categories: [Ownership, Introduction]
tags:
  [rust, beginners, variables, data-types, ownership, stack, heap, introduction]
---

## Ownership

A set of rules that govern how Rust manages memory.If any of these rules are violated, the program won't compile.

Rust doesn't have a garbage collector like other languages therefore it uses rules.

The number one ownership rule is, all values have a single owner. Only that owner is responsible for deallocating that value.
This is enforced through the borrow checker, which we'll see in the `references and borrowing` lesson.

Other variables can borrow this value, but they can never own the value. Subsequently, they'll lose their reference to this value,
once the owner drops the value.

## Stack and Heap

### Stack

Stack stores values in a LIFO(Last In First Out) manner.

Adding data is called pushing into the stack, while removing data is popping off the stack.

All data stored on the stack must have a fixed size.

If the size of the data at compile time is unknown or dynamic, then it'll be stored on the heap instead.

### Heap

- less organized
- you request a certain amount of space when you put data on the heap.
- memory allocator finds an empty spot that can contain the data, mark it as being used
  and returns a pointer, which is the address of the location.Also known as allocating on the heap
  or just allocating.
- The pointer to the heap is stored on the stack because it's fixed.
- Accessing the data on the heap is simply following the pointer.

Accessing data on the heap is slower than accessing data on the stack.

The allocator has just one spot to get data from the stack. That's at the top of the stack.
But for the heap, the allocator has to find a big enough space to hold the data,
and then perform bookkeeping to prepare for the next allocation.

Problems Ownership addresses.

- keeping track of what parts of code are using what data on the heap.
- Minimizing the amount of duplicate data on the heap
- cleaning up unused data on the heap, so you don't run our of space.

## Ownership Rules

- Every value in Rust has an owner
- There can only be one owner at a time
- Value gets dropped when owner goes out of scope.

The scope of values.

```rust
    {                      // s is not valid here, it’s not yet declared
        let s = "hello";   // s is valid from this point forward

        // do stuff with s
    }                      // this scope is now over, and s is no longer valid

```

## String Type

`let s = String::from("hello");`

Mutate string

```rust
let mut s = String::from("hello");

s.push_str(", world!");

println!("{}",s);
```

In C++, this pattern of deallocating resources at the end of an item’s lifetime is sometimes called Resource Acquisition Is Initialization (RAII).

The below code won't compile, because s1 is moved into s2.Therefor s1 is dropped before the print statement.
This is called shallow copying.
Note well that only stack data is copied and not the heap.

```rust
    let s1 = String::from("hello");
    let s2 = s1;

    println!("{}, world!", s1);

```

You can use the `clone` method to deeply copy data on the heap and not just the stack data.

For example, this code fragment will compile

```rust
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {}, s2 = {}", s1, s2);

```

Bear in mind that `clone` is expensive, because it copies heap data which we don't know its size.

Passing a value to a function would move or copy.
