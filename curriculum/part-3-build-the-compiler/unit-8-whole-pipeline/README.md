# Unit 8 — The Whole Pipeline for `return 2;` (tests: ch. 1)

**Part:** 3 — Build the Compiler · **Est. time:** ~16–26 h

## Goal
Build every stage of a real compiler, end to end, for the smallest C program there is:
`int main(void) { return 2; }`. Each stage is tiny, but the shape of the pipeline is the one you will extend for the rest of the course:
driver → lexer → parser → assembly generation → emission → assembler and linker. By the end, `rcc` turns that C file
into an x86-64 executable whose exit status is `2`, and passes chapter 1 of the test suite.

## What exists at the end of this unit
- An `rcc` binary that preprocesses with `gcc -E -P`, compiles, then assembles and links with `gcc`, supporting the
  stage flags `--lex`, `--parse`, `--codegen` and `-S`, and exiting non-zero on any error.
- A C lexer, a C AST with a recursive-descent parser, an assembly AST with a C-AST→assembly pass, and an emitter that
  handles the macOS `_` symbol prefix and the Linux `.note.GNU-stack` section.
- One module per stage, `cargo test` unit tests for each, and a clean `cargo clippy`.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [8.1 The compiler driver](8.1-compiler-driver.md) | Builds `rcc` CLI + stage flags | 3–5 h |
| [8.2 Lexing C](8.2-lexing-c.md) | Builds C lexer | 4–6 h |
| [8.3 Parsing C](8.3-parsing-c.md) | Builds AST + parser | 5–8 h |
| [8.4 Assembly generation](8.4-assembly-generation.md) | Builds assembly AST + codegen | 2–3 h |
| [8.5 Code emission](8.5-code-emission.md) | Builds emitter → first executable | 2–4 h |

## Before you start
Unit 7 is done. Your x86-64 toolchain and the test suite from lesson 6.5 work (`./test_compiler --check-setup`, or see
`--help`). Re-read lessons 6.3 (AT&T syntax) and 6.4 (return values in `%eax`): this unit relies on both.

## What comes next
Unit 9 adds unary and binary operators, and with them a proper intermediate representation (TACKY), stack frames and
precedence climbing. You will add enum variants to almost every type you build here and follow `rustc`'s errors to
every `match` that needs updating. Before moving on, pass `--chapter 1` in full and be able to draw the pipeline from
memory, naming the data type that flows between each pair of stages.
