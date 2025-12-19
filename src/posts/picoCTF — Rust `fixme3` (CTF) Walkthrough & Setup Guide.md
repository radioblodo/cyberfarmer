This short guide explains how to set up Rust using `rustup`, fix the **picoCTF Rust `fixme3`** challenge, and run the project successfully using Cargo.  
The challenge itself is intentionally simple and focuses on understanding Rust’s `unsafe` blocks.

---

## Prerequisites: Install Rust (rustup + stable Cargo)

### Install `rustup`

#### Linux / macOS
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
````

Reload your shell so that `cargo` and `rustc` are available:

```bash
source ~/.cargo/env
```

#### Windows

Download and run **rustup-init** from the official Rust website.  
Once installed, open a new terminal.

---

### Set the Stable Toolchain as Default

This ensures you are using the stable version of Rust and Cargo.

```bash
rustup default stable
```

Verify the installation:

```bash
rustc --version
cargo --version
```

---

## picoCTF Rust `fixme3` — Puzzle Overview

The `fixme3` challenge is a **Rust compilation fix** challenge.  
The solution requires **uncommenting an `unsafe` block** and its corresponding closing brace.

Rust enforces strict memory safety rules, and `unsafe` blocks explicitly tell the compiler that you are intentionally bypassing some of these checks.

---

## How to Solve the `fixme3` Challenge
Before we can move on to solve the fixme3 challenge, we need to understand a little bit about unsafe rust. To put it simply, unsafe rust is basically telling the rust compiler to allow the programmer to execute code that would otherwise be deemed by the compiler as unsafe, like telling the compiler "trust me bro". There are 5 use cases where we might need to use unsafe rust. 
## The 5 use cases of Unsafe Rust

We should note that unsafe Rust does not disable the borrow checker, but it grants you five specific abilities that are otherwise restricted.

### 1. Dereferencing a Raw Pointer

Unlike references (`&`), raw pointers can be null or pointing to invalid memory. You can create them in safe code, but you must use `unsafe` to see what is inside.

Rust

```
let mut num = 5;
let r1 = &raw const num; // Immutable raw pointer

unsafe {
    println!("r1 is: {}", *r1);
}
```

### 2. Calling an Unsafe Function

Functions marked `unsafe` require the caller to verify they are meeting specific requirements.

Rust

```
unsafe fn danger() { /* ... */ }

unsafe {
    danger();
}
```

### 3. Modifying a Mutable Static Variable

Global variables in Rust are called `static`. If they are mutable, they are unsafe because multiple threads could access them simultaneously, causing a data race.

Rust

```
static mut TOTAL: i32 = 0;

unsafe {
    TOTAL += 1;
}
```

### 4. Implementing an Unsafe Trait

A trait is unsafe if its implementation must uphold invariants that the compiler cannot verify.

Rust

```
unsafe trait Secret {}
unsafe impl Secret for i32 {}
```

### 5. Accessing Fields of a Union

Unions are used primarily for interfacing with C code. Since a union field shares memory with other fields, the compiler cannot guarantee the type of the data you are reading.

Rust

```
union MyUnion { f1: u32, f2: f32 }
let u = MyUnion { f1: 1 };

unsafe {
    println!("{}", u.f1);
}
```

### Rust fixme3 Guide:

Now, how do we solve the challenge? We will first need to `cd` into the project directory after unzipping the file. This is also where you will see `Cargo.toml` .

```bash
cd path/to/fixme3
ls
```

You should see:

```text
Cargo.toml
src/
```

---

Next we need to locate the file with the `.rs` extension, that's where the rust code is. On Linux, we can run a `cat main.rs` command to read the contents of the code to get some basic understanding first. Then, we need to make some changes to the file to correct the syntax error. Here, it really doesn't matter the editor you use but I used vim to edit the code right in the terminal. 

Open it using your preferred editor:

```bash
nano src/main.rs
# or
vim src/main.rs
# or
code src/main.rs
```

This is the important step and that is to uncomment the `unsafe` keyword, along with the closing brace. 

Look for a commented `unsafe` block that looks similar to this:

```rust
// unsafe {
    // some Rust code here
// }
```

Uncomment **both** the `unsafe` keyword **and** the matching closing brace:

```rust
unsafe {
    // some Rust code here
}
```

> ⚠️ Important:  
> If you uncomment `unsafe {` but forget to uncomment the closing `}`, the code will not compile.

Save the file after making the changes.

Lastly, run the program using the command below and you will see the flag printed in your terminal:

```bash
cargo run
```

![[Pasted image 20251219233613.png]]
---

## Common Issues & Fixes

### `cargo: command not found`

Your environment variables may not be loaded. Run:

```bash
source ~/.cargo/env
```

### Compilation Errors Persist

- Ensure **both** `unsafe {` and `}` are uncommented.
    
- Confirm you edited the correct file inside the `src/` directory.
    
- Make sure you are running `cargo run` from the directory containing `Cargo.toml`.
    

---

## Summary

1. Install Rust using `rustup`
    
2. Set stable toolchain: `rustup default stable`
    
3. Uncomment the `unsafe` block and its closing brace
    
4. Run the project with:
    

```bash
cargo run
```

That’s it — a clean and simple Rust CTF fix. I hope this write-up is useful to you and you have learn something by reading it. Happy hacking! :)