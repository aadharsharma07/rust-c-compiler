# Unit 0 — Rust Foundations

**Goal:** become productive enough in Rust to write a compiler, and meet the shape of a compiler
front end (characters → tokens → tree → result) on a problem small enough to finish in a weekend:
an integer calculator.

**Est. time:** ~25–37 h · **Tests:** none from the C test suite; you write your own `cargo test` unit tests.

## What exists at the end of this unit
- A working Rust toolchain (`rustup`, `cargo`, `clippy`, `rustfmt`) and a habit of `cargo test` + `cargo clippy`.
- A `calc` cargo project with separate modules for tokens/lexer, AST, parser, evaluator and a REPL.
- A REPL that reads lines like `2 * (3 + 4) - -1`, prints `15`, and reports errors
  (bad character, unexpected token, division by zero) without crashing.
- Unit tests for each stage, and the ability to explain every phase without notes.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [0.1 What a compiler is](0.1-what-a-compiler-is.md) | Learning only | 2–3 h |
| [0.2 Ownership & borrowing](0.2-ownership-and-borrowing.md) | Learning only | 4–6 h |
| [0.3 Modelling data](0.3-modelling-data.md) | Learning only | 4–6 h |
| [0.4 Trees in Rust](0.4-trees-in-rust.md) | Learning only | 3–4 h |
| [0.5 Lexing](0.5-lexing.md) | Builds calculator lexer | 3–5 h |
| [0.6 Parsing](0.6-parsing.md) | Builds calculator parser + evaluator | 5–8 h |
| [0.7 Organising code](0.7-organising-code.md) | Builds calculator REPL in modules | 3–4 h |

## Prerequisites for Unit 1
- You can read and fix borrow-checker errors involving `&str`, `String` and `&mut`.
- You can model data with `enum`s carrying data, `Box` for recursion, and handle errors with `Result` and `?`.
- You can hand-write a lexer and a recursive-descent parser, and split a crate into modules.
- An environment that can assemble, link and **run x86-64** binaries: Linux x86-64, an Intel Mac,
  or Apple Silicon with Rosetta 2 (`arch -x86_64`) or an x86-64 Docker container.
- Python 3 and a clone of the test suite (`nlsandler/writing-a-c-compiler-tests`), ready for Unit 1.
