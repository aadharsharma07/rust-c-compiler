# Unit 4 — Abstraction and Organisation

**Part:** 1 — Learn Rust · **Est. time:** ~27–38 h · **Tests:** none

## Goal
Move from "Rust that compiles" to Rust that is organised, reusable and idiomatic. Python's
abstractions (duck typing, lambdas, generators, packages) are checked as the program runs; Rust's
(traits, generics, closures, iterators, modules) are all checked before it runs. The unit also
fills the last gaps before a compiler: recursive trees with `Box`, shared ownership with
`Rc`/`RefCell`, lifetimes, and a real project layout with tests, `clippy`, `rustfmt` and docs.

## What exists at the end
- Tested scratch crates for traits, generics, iterators, smart pointers and lifetimes.
- A toy tree (a file-system or family tree) built with `Box`, and a shared-ownership version
  with `Rc`/`RefCell`, plus a clear sense of when each is worth the cost.
- A working **file search CLI** (a small `grep`) split into modules, with its own error type,
  iterator pipelines, unit tests and integration tests, clean under `cargo clippy`.
- The habit of running `cargo fmt`, `cargo clippy` and `cargo test` before every commit.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [4.1 Traits](4.1-traits.md) | Learning | 3–5 h |
| [4.2 Generics](4.2-generics.md) | Learning | 3–4 h |
| [4.3 Closures and iterators](4.3-closures-and-iterators.md) | Learning | 4–5 h |
| [4.4 Smart pointers and recursive types](4.4-smart-pointers.md) | Learning | 4–6 h |
| [4.5 Lifetimes](4.5-lifetimes.md) | Learning | 4–6 h |
| [4.6 Modules, testing and tooling](4.6-modules-testing-tooling.md) | Learning | 3–4 h |
| [4.7 Project: file search tool](4.7-project-file-search.md) | Project | 6–8 h |

Lessons 4.3 (`peekable`) and 4.4 (`Box`, recursive enums) matter most: your lexer and syntax trees build on them.

## What comes next
That's the end of Part 1. Part 2, Unit 5 (How Languages Are Processed) puts Rust aside to teach
what a compiler does (lexing, grammars, parsing, syntax trees, IRs), practised by hand and with
Python's `tokenize`, `ast` and `dis`.
