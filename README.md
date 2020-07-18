# learn-rustlang
Notes and code that help me learn rust lang

```bash
# Create new project.
cargo new <project-name>

# Build binary and write it to <project-root>/target/debug/<project-name>
cargo build
# Compile with optimizations and write to <project-root>/target/release/<project-name>
# Rust will not include checks for integer overflow that cause panics - program exits with error.
# Instead, it will perform two's complement wrapping.
cargo build --release

# Shortcut for building binary and running it.
cargo run

# Check to see if code compiles, but no executable is outputted. Useful for quickly checking code.
cargo check

# Locally build and open documentation in browser for all project dependencies.
cargo doc --open
```

`String` is growable, UTF-8

*associated function* is analogous to *static member functions* in c++.

## Variables

variables are declared with `let`, while constants are declared with `const`.

*Constants* are similar to immutable variables, but different in that there is no way to make constants mutable.

Constants require type annotation.

Example:

```rust

const MAX_POINTS: u32 = 100_000;
```

### Tuples

- Different types in one tuple.
- Access positional elements with `.` operator followed by 0-based index.

```rust

fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
	
	// Destructuring/unpacking a tuple.
	let (x, y, z) = tup;
	
	let a = tup.0; // 500
	let b = tup.1; // 6.4
	let c = tup.2; // 1
}

```

### Array

- Elements must all be same type.
- Fixed length, unlike vector, which can grow.
- Useful when you want to store data in the stack than the heap.

```rust

fn main() {
    let a = [1, 2, 3, 4, 5];
	
	// Annotating array type by `[type; size]`
	let b: [i32; 5] = [1, 2, 3, 4, 5];
	
	// Shorthand for initializing array with same value elements.
	let c = [3; 5];
	// equialent to:
	let c = [3, 3, 3, 3, 3];
	
	// Accesing elements.
	let first = a[0]; // 1
    let second = a[1]; // 2
	
	// Accessing out-of-bounds index will cause runtime error, not compile-time.
}

```

## Functions

- Use snake case naming: All letters are lowercase with underscores.
- Functions can call other functions even if they're defined below it.
- Must always define parameter types.
- Function bodies contain *statements* (no return value) and *expressions* (returns a value).
  - *Expressions* do not have semicolons at the end - adding semicolon makes it a *statement*.
- Return values do not need to be named, but type must be declared using `->`.
- Return early from a function using the `return` keyword. Otherwise, function returns last *expression*.

```rust

fn main() {

	// Call functions defined below with *argument* 5.
    another_function(5);
}

// Function takes *parameter* x of type i32.
fn another_function(x: i32) {
    println!("The value of x is: {}", x);
}

// Returns 5. No semicolon after 5.
fn five() -> i32 {
    5
}
```

## Control Flow

### Conditionals

- Conditional expressions must evaluate to bool, not 0 or nonzero like C++.

```rust

fn main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
	
	// Using `if else` as an expression to assign an i32 value to `number`.
	// In this case, the last expression in both `if` and `else` blocks must be the same type.
	let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {}", number);
}
```

### Loops

#### Infinite loop using `loop`

`break` can be used to break out of loop, with a return value.

```rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {}", result);
}
```

#### `while` loops

```rust
fn main() {
    let mut number = 3;

    while number != 0 {
        println!("{}!", number);

        number -= 1;
    }
}
```

### `for` loops

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a.iter() {
        println!("the value is: {}", element);
    }
	
	for number in (1..4).rev() {
        println!("{}!", number);
    }
}
```


