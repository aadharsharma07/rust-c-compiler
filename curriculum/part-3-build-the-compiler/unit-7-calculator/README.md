# Unit 7 — Warm-up, a Calculator (no test suite)

**Part:** 3 — Build the Compiler · **Est. time:** ~11–17 h

## Goal
Before you write a single line of the C compiler, you build a complete, tiny language implementation in Rust: a
calculator for integer expressions such as `2 * (3 + 4) - -1`. You already know the *theory* of lexing and parsing
from Part 2 (lessons 5.2–5.4) and the Rust you need from Part 1. This unit is where the two meet: you turn grammars
into Rust types and functions, decide how tokens, trees and errors should look, and organise the result into modules
that mirror the phases of a compiler. Every design question you answer here comes back, slightly bigger, in Unit 8.

## What exists at the end of this unit
- A `calc` crate with a **lexer** (text → tokens with positions), a **recursive-descent parser** (tokens → AST) and an
  **evaluator** (AST → `i64`), each in its own module with a small public surface.
- Error types for every stage, carried as values with `Result` and reported with human-readable messages. No panics on
  bad input, overflow or division by zero.
- A `Display` pretty-printer for the AST, checked by a parse → print → parse round-trip test.
- An interactive **REPL** (read–eval–print loop) that survives errors and exits cleanly at end of input.
- A healthy `cargo test` suite (30+ tests across the modules) and a clean `cargo clippy`.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [7.1 Calculator lexer](7.1-calculator-lexer.md) | Builds lexer | 3–5 h |
| [7.2 Calculator parser](7.2-calculator-parser.md) | Builds recursive-descent parser + AST | 5–8 h |
| [7.3 Evaluator and REPL](7.3-evaluator-and-repl.md) | Builds evaluator + REPL | 3–4 h |

## Before you start
Part 1 and Part 2 are done. Skim lessons 5.2 (lexing) and 5.3 (grammars and recursive descent), and keep Part 1's
lessons 3.2 (enums), 3.3 (`Result`), 4.3 (iterators, `peekable`), 4.4 (`Box`) and 4.6 (modules, tests) at hand.

## What comes next
Unit 8 starts `rcc`, the real compiler, and builds the whole pipeline for `int main(void) { return 2; }`: a driver, a C
lexer, a parser, an assembly generator and an emitter, checked by chapter 1 of the test suite. The calculator's lexer
and parser are the templates you will reach for.
