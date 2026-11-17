# Unit 1 — Rust Basics for Python Programmers

**Part:** 1 — Learn Rust · **Est. time:** ~13–19 h · **Tests:** none (you check your own programs by running them)

## Goal
Go from "I have never written Rust" to "I can write, compile and run a small interactive Rust
program". Along the way you learn the biggest differences from Python: Rust is **compiled**
ahead of time, **statically typed**, and manages memory **without a garbage collector**. Every
new idea is introduced by contrast with the Python you already know.

## What exists at the end of this unit
- A working Rust toolchain (`rustup`, `rustc`, `cargo`) and the habit of `cargo check` / `cargo run`.
- A folder of small scratch crates where you tried out variables, types, functions and loops.
- A finished **guessing game**: a command-line program that reads your guesses from the
  keyboard, parses them, loops until you win, and uses an external crate (`rand`).
- The ability to read a basic `rustc` error message and say which rule it enforces.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [1.1 How Rust differs from Python](1.1-rust-vs-python.md) | Learning | 2–3 h |
| [1.2 Variables and types](1.2-variables-and-types.md) | Learning | 3–4 h |
| [1.3 Functions and expressions](1.3-functions-and-expressions.md) | Learning | 2–3 h |
| [1.4 Control flow](1.4-control-flow.md) | Learning | 2–3 h |
| [1.5 Project: guessing game](1.5-project-guessing-game.md) | Project | 4–6 h |

## How this unit connects to the compiler
A compiler is a large program that reads text, makes decisions with `match` and loops, and
produces more text. Everything here is raw material you will use daily in Part 3, and you'll
be running `rustc` long before you write a compiler yourself.

## What comes next
**Unit 2 — Ownership and Memory.** You'll learn where values actually live (the stack and the
heap), how Python manages memory for you, and how Rust's ownership and borrowing rules let it
free memory safely with no garbage collector. That is the idea that makes Rust *Rust*.
