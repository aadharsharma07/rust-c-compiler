# Unit 1 — The Whole Pipeline for `return 2;`

**Goal:** build every stage of a real compiler, end to end, for the smallest C program there is:
`int main(void) { return 2; }`. Each stage is tiny, but the shape of the pipeline (driver → lexer →
parser → assembly generation → emission → assembler/linker) is the one you will extend for the
rest of the course.

**Est. time:** ~20–30 h · **Tests:** chapter 1 of the test suite (`./test_compiler ./target/debug/rcc --chapter 1`).

## What exists at the end of this unit
- A working x86-64 toolchain on your machine (native, Rosetta on Apple Silicon, or Docker) and a
  cloned, passing `--check-setup` test suite.
- An `rcc` binary that preprocesses with `gcc -E -P`, compiles, then assembles and links, and that
  supports `--lex`, `--parse`, `--codegen` and `-S`, exiting non-zero on any error.
- A lexer, an AST plus recursive-descent parser, an assembly AST plus AST→assembly pass, and an
  emitter that handles the macOS `_` prefix and the Linux `.note.GNU-stack` section.
- Separate modules for each stage, with `cargo test` unit tests and a clean `cargo clippy`.

## Lessons

| Lesson | Type | Time |
|---|---|---|
| [1.1 The target machine](1.1-the-target-machine.md) | Learning only | 3–4 h |
| [1.2 The compiler driver](1.2-the-compiler-driver.md) | Builds `rcc` CLI + stage flags | 3–5 h |
| [1.3 Lexing C](1.3-lexing-c.md) | Builds lexer | 4–6 h |
| [1.4 Grammar & AST](1.4-grammar-and-ast.md) | Builds AST + recursive-descent parser | 5–8 h |
| [1.5 Assembly representation](1.5-assembly-representation.md) | Builds assembly AST + AST→asm pass | 2–3 h |
| [1.6 Code emission](1.6-code-emission.md) | Builds emitter → first executable | 2–4 h |

## Before starting Unit 2 you should
- Pass all of chapter 1 (valid programs, invalid lexing, invalid parsing).
- Be able to draw the whole pipeline from memory and name the data type flowing between each stage.
- Read AT&T syntax fluently enough to explain every line of your own `.s` output.
- Be comfortable adding a variant to a Rust `enum` and following the compiler errors to every
  `match` that needs updating: Unit 2 does this constantly.
