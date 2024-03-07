---
title: Method Syntax
date: 2024-03-07 00:45:08 +0000
categories: [Getting Started, Introduction]
tags: [rust, beginners, philosophy, impl, introduction] # TAG names should always be lowercase
---

## Methods Syntax

They are defined within the context of a struct/enum/trait object, with the `fn` keyword, can have arguments and return values.

Their first parameter is `self` and represents an instance of the struct the method is being called on.

The example below defines a struct object called `Car`.

To define methods with the context of Car, we'll add them within an `impl`(implementation) block.

We have 4 methods to define

1. Create a new car instance with provided details
2. Print a summary of the car's information
3. Check if the car is a specific color
4. Increase the car's model year by a specified amount (for simulation purposes)

```rust

struct Car {
  make: String,
  model: String,
  year: u16,
  color: String,
  num_doors: u8,
}

impl Car {
  // 1. Create a new car instance with provided details
  fn new(make: String, model: String, year: u16, color: String, num_doors: u8) -> Car {
    Car {
      make,
      model,
      year,
      color,
      num_doors,
    }
  }

  // 2. Print a summary of the car's information
  fn print_info(&self) {
    println!("Make: {}", self.make);
    println!("Model: {}", self.model);
    println!("Year: {}", self.year);
    println!("Color: {}", self.color);
    println!("Number of Doors: {}", self.num_doors);
  }

  // 3. Check if the car is a specific color
  fn is_color(&self, target_color: &str) -> bool {
    self.color.to_lowercase() == target_color.to_lowercase()
  }

  // 4. Increase the car's model year by a specified amount (for simulation purposes)
  fn age(&mut self, years: u16) {
    self.year += years;
  }
}

fn main(){
     let car = Car::new(String::from("Toyota"), String::from("CHR-25"), 2019, String::from("red"), 4);

     let color = "green";
     car.print_info();

     let is_color = car.is_color(&color);

     println!("color is {}",is_color);



}
```
