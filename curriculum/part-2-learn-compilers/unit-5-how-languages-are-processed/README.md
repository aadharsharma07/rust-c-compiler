# Unit 5 — How Languages Are Processed

**Part:** 2 — Learn Compilers · **Est. time:** ~18–26 h · **Tests:** none

## Goal
Understand the *front half* of every language implementation: how a program goes from a file of
characters to a structure a computer can reason about. You will follow your own Python code
through CPython's pipeline (source → tokens → AST → bytecode → virtual machine) and then see how a
native C compiler differs. No compiler code is written in this unit. Instead you practise every
phase by hand, on paper, and poke at CPython's real phases with the `tokenize`, `ast` and `dis`
modules, so that when you build `rcc` in Part 3 you already know *what* each phase must do and
only have to learn *how* to do it in Rust.

## What exists at the end
- A notebook (paper or a `notes/` folder) full of hand-written token streams, grammars, parse
  trees, ASTs, symbol tables and three-address code for small C and Python snippets.
- A few tiny Python scripts that print the tokens, AST and bytecode of any Python file.
- The ability to read a short C program (`int main(void) { ... }`, variables, `if`, `while`,
  functions) and explain what each phase of a compiler would produce for it.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [5.1 Compilers and interpreters](5.1-compilers-and-interpreters.md) | Learning | 3–4 h |
| [5.2 Lexing](5.2-lexing.md) | Learning | 3–5 h |
| [5.3 Grammars and parsing](5.3-grammars-and-parsing.md) | Learning | 5–7 h |
| [5.4 ASTs and semantic analysis](5.4-asts-and-semantic-analysis.md) | Learning | 4–5 h |
| [5.5 Intermediate representations](5.5-intermediate-representations.md) | Learning | 3–5 h |

Lesson 5.3 is the heart of the unit: you'll code recursive descent in Rust in Units 7 and 8.

## What comes next
Unit 6 (The Machine) goes underneath: binary numbers, how a CPU executes instructions, x86-64
assembly, the stack, calling conventions and the toolchain. Together, Units 5 and 6 cover both
ends of the compiler you will build: the front end that reads C, and the machine it must target.
