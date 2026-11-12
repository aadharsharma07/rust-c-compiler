# rust-c-compiler

A C compiler (`rcc`) written by hand in Rust. It's a learning project to understand how compilers work and to learn Rust along the way.

The compiler turns a growing subset of C into x86-64 assembly, then uses the system assembler and linker to build executables. Work proceeds lesson by lesson, from a calculator up to an optimising compiler with register allocation.

## How this repo is organised
| Path | What it is |
|---|---|
| `curriculum/README.md` | The syllabus: every unit and lesson, with time estimates and test chapters |
| `curriculum/unit-*/` | One self-contained file per lesson |
| `PROGRESS.md` | Where I am right now |
| `JOURNAL.md` | What I've learned, in my own words |
| `CLAUDE.md` / `AGENTS.md` | Rules for AI tutors: they explain and review, they never write the code |

## Ground rules
- I write every line of code myself. AI is used only as a tutor.
- The test suite at [nlsandler/writing-a-c-compiler-tests](https://github.com/nlsandler/writing-a-c-compiler-tests) is the source of truth.
- The lesson order follows Nora Sandler's *Writing a C Compiler* (No Starch Press, 2024).

## Running on Apple Silicon
`rcc` emits x86-64 assembly. On an M-series Mac, assemble and run its output under Rosetta 2 (`arch -x86_64 ...`), or use an x86-64 Linux Docker container. Lesson 1.1 covers the setup.
