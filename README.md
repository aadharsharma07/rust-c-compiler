# rust-c-compiler

A learning project in three parts: **learn Rust → learn how compilers work → build a C compiler (`rcc`) by hand in Rust.**

The finished compiler turns a large subset of C into x86-64 assembly, then uses the system assembler and linker to produce executables. It includes an optimiser and a graph-colouring register allocator.

## How this repo is organised
| Path | What it is |
|---|---|
| `curriculum/README.md` | The syllabus: 3 parts, 14 units, 76 lessons, with time estimates |
| `curriculum/part-1-learn-rust/` | Rust from zero, for a Python programmer, through small projects |
| `curriculum/part-2-learn-compilers/` | Compiler concepts and how the machine runs code (no compiler code yet) |
| `curriculum/part-3-build-the-compiler/` | Building `rcc` lesson by lesson, checked by the official test suite |
| `LEARNER.md` | Who the course is pitched at, and how to teach it |
| `PROGRESS.md` | Where I am right now |
| `JOURNAL.md` | What I've learned, in my own words |
| `CLAUDE.md` / `AGENTS.md` | Rules for AI tutors: explain, then let me build; never write my code |

## Ground rules
- I write every line of code myself. AI is used only as a tutor.
- In Part 3, the test suite at [nlsandler/writing-a-c-compiler-tests](https://github.com/nlsandler/writing-a-c-compiler-tests) is the source of truth. Part 3 follows the chapter order of Nora Sandler's *Writing a C Compiler* (No Starch Press, 2024).

## Running on Apple Silicon
`rcc` emits x86-64 assembly. On an M-series Mac, assemble and run its output under Rosetta 2 (`clang -arch x86_64`, then `arch -x86_64 ./prog`), or use an x86-64 Linux Docker container. Lesson 6.3 covers the setup.
