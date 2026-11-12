# Unit 5 — A Real Type System (tests: ch. 11–18)

**Goal:** turn your int-only compiler into one that understands C's type system. Each lesson adds a type
(or a way of building types) and pushes it through *every* pass: lexer → parser → type checker → TACKY →
assembly → fix-ups → emitter. You will learn how one language feature becomes many machine-level decisions:
operand sizes, sign vs. zero extension, a second register file for floating point, addresses, memory layout and
the System V ABI rules for passing aggregates.

**At the end of this unit `rcc` supports:** `int`, `long`, `unsigned int`, `unsigned long`, `double`, `char`
(all three kinds), pointers, multi-dimensional arrays with initialisers, string literals, `void`, `sizeof`,
heap memory through `malloc`/`free`, and structs that can be copied, passed to and returned from functions
in a way that links correctly against code compiled by `gcc`/`clang`.

| Lesson | Builds | Time | Tests |
|---|---|---|---|
| [5.1 Types in a compiler](5.1-types-in-a-compiler.md) | `Type` enum + typed AST | 4–6 h | ch. 11 (front end) |
| [5.2 long](5.2-long.md) | `long` | 10–14 h | ch. 11 |
| [5.3 unsigned](5.3-unsigned.md) | `unsigned` | 8–12 h | ch. 12 |
| [5.4 Floating point](5.4-floating-point.md) | `double` | 12–18 h | ch. 13 |
| [5.5 Pointers](5.5-pointers.md) | `&`, `*` | 10–14 h | ch. 14 |
| [5.6 Arrays](5.6-arrays.md) | Arrays, subscripts, initialisers | 10–14 h | ch. 15 |
| [5.7 Characters & strings](5.7-characters-and-strings.md) | `char`, string literals | 6–8 h | ch. 16 |
| [5.8 Memory](5.8-memory.md) | `void`, `sizeof`, `malloc` | 5–8 h | ch. 17 |
| [5.9 Structs](5.9-structs.md) | Structs | 15–25 h | ch. 18 |

**Total:** about 80–120 hours, which is two to three months at 8 h/week.

> **This unit is long, and you may stop partway.** Every lesson ends with a compiler that passes all tests
> up to its chapter. Stopping after 5.4 (numeric types) or 5.8 (everything except structs) still leaves
> you with a coherent compiler. Units 6 and 7 work on whatever subset you have, so you can come back to
> 5.9 later.

**Working habit for this unit:** after each lesson, run the *whole* suite up to that chapter, not just
the new chapter. Adding a type often breaks something two passes away.
