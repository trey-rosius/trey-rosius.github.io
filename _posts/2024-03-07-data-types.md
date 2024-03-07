---
title: Data Types
date: 2024-03-06 19:45:08 +0000
categories: [Data Types, Variables, Introduction]
tags: [rust, beginners, variables, data-types] # TAG names should always be lowercase
---

## Data types

Rust is a statically typed language. Therefore, it must know the types of each value at compile time.
Every value is of a certain data type, which tells rust exactly how to interact with that value.

Rust datatypes have 2 subsets

### Scalar types.

They represent a single value.
Rust has 4 scalar types

#### Integer Types

A number without a fractional component.
Signed integer types start with `i` and unsigned integer types start with `u`.
If you want to represent a negative number, use a signed integer type.

```rust
let ball_score:i32 = -430;
```

For numbers that'll only ever be, use a unsigned.

```rust
let age:u32 = 35;
```

Signed variants can store numbers from -(2<sup>n - 1</sup>) to 2<sup>n - 1</sup> - 1

Therefor i32 can store numbers from -2<sup>31</sup> to -2<sup>31</sup> -1

Unsigned variants can store numbers from 0 to 2<sup>n</sup> - 1

All these depend on the architecture of the computer your program is running in on.

Integer types default to i32;

| Length  | Signed | Unsigned |
| ------- | ------ | -------- |
| 8-bit   | i8     | u8       |
| 16-bit  | i16    | u16      |
| 32-bit  | i32    | u32      |
| 64-bit  | i64    | u64      |
| 128-bit | i128   | u128     |
| arch    | isize  | usize    |

#### Floating point Types

Also known as numbers with Decimal points. Rust has 2 types of floating point numbers.

f32 and f64 which 32 and 64 bits in size respectively.

All floating point types are signed.

The default type is f64.

```rust
let  x = 2.0; //f64

let y:f32 = 3.0; //f32

```

#### Boolean Types

Represented with 2 values: true and false. They are one byte in size;
They are represented using `bool`.

```rust
let t = true;

let f: bool = false; // with explicit type annotation
```

#### Character Types

Character literals are specified with single quotes as opposed to string literals.

Rust char type is 4 bytes in size and can represent more than just ASCII
`char`

```rust
let c = 'z';
let z: char = 'ℤ'; // with explicit type annotation
let heart_eyed_cat = '😻';
```

### Compound Types

They can group multiple values into one type.

#### tuple type

Tuples help you group a number of values with a variety of types into one compound type.
They have a fixed length. Once declared, they can't grow nor shrink

```rust
let tup:(i32, f64, u8) =(500, 6.4, 1);

```

use pattern matching to destructure a tuple and get individual values.

```rust
let tup:(i32, f64, u8) =(500, 6.4, 1);

let (x, y , z) = tup;

 println!("The value of y is: {y}");

```

You can also access individual tuple elements using their indexes

```rust
let tup:(i32, f64, u8) =(500, 6.4, 1);

let five_hundred = tup.0;

let six_point_four = tup.1;

let one  = tup.2;

```

#### Array Type

Every element of an array must have the same type.
Arrays in rust have a fixed size.

```rust
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
```

You write an array’s type using square brackets with the type of each element, a semicolon, and then the number of elements in the array, like so:

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];

```

You can also initialize an array to contain the same value for each element by specifying the initial value, followed by a semicolon, and then the length of the array in square brackets

```rust
let a = [3; 5]; === let a = [3, 3, 3, 3, 3];

```

Accessing array elements

```rust

 let a = [1, 2, 3, 4, 5];

    let first = a[0];
    let second = a[1];
```
