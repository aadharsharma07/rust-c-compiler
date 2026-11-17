# Unit 12 — A Real Type System (tests: ch. 11–18)

**Part:** 3 — Build the Compiler · **Est. time:** ~80–120 h (two to three months at 8 h/week)

## Goal
Until now every value in your compiler was a 32-bit `int`. This unit adds the rest of C's type system, one type per lesson.
Since you have never written C, each lesson first explains the C feature from a Python point of view, then how to compile
it through *every* pass, from lexer to emitter: operand sizes, sign vs. zero extension, a second register file for floating
point, addresses, memory layout, and the System V rules for passing structs.

## What exists at the end of this unit
- A recursive `Type` and a **typed AST** in which every implicit conversion is an explicit cast.
- `int`, `long`, `unsigned int`, `unsigned long`, `double`, and the three `char` types, with correctly sized code for each.
- Pointers, multi-dimensional arrays, string literals, `void`, `sizeof`, and heap memory via `malloc`/`calloc`/`free`.
- Structs that can be copied, passed to and returned from functions, linking correctly against code built by `clang`/`gcc`.

## Lessons
| Lesson | Type | Time | Tests |
|---|---|---|---|
| [12.1 Types in a compiler](12.1-types-in-a-compiler.md) | Builds `Type` + typed AST | 4–6 h | ch. 11 (`--stage validate`) |
| [12.2 long](12.2-long.md) | Builds `long` | 10–14 h | ch. 11 |
| [12.3 unsigned](12.3-unsigned.md) | Builds `unsigned` | 8–12 h | ch. 12 |
| [12.4 Floating point](12.4-floating-point.md) | Builds `double` | 12–18 h | ch. 13 |
| [12.5 Pointers](12.5-pointers.md) | Builds `&`, `*` | 10–14 h | ch. 14 |
| [12.6 Arrays](12.6-arrays.md) | Builds arrays | 10–14 h | ch. 15 |
| [12.7 Characters and strings](12.7-characters-and-strings.md) | Builds `char`, strings | 6–8 h | ch. 16 |
| [12.8 Memory](12.8-memory.md) | Builds `void`, `sizeof`, `malloc` | 5–8 h | ch. 17 |
| [12.9 Structs](12.9-structs.md) | Builds structs | 15–25 h | ch. 18 |

## Before you start
Chapters 1–10 pass. Re-read 6.1 (two's complement, extension) and 6.4 (calling convention). After every lesson, run the
whole suite up to that chapter, not just the new one: a new type often breaks something two passes away.

## What comes next
You may stop partway: every lesson ends with a compiler that passes all tests up to its chapter, and stopping after 12.4 or
12.8 leaves a coherent compiler. Units 13 (optimisation) and 14 (register allocation) work on whatever subset you have.
