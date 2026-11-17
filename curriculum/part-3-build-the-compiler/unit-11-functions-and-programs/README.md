# Unit 11 — Functions and Whole Programs (tests: ch. 9–10)

**Part:** 3 — Build the Compiler · **Est. time:** ~23–35 h

## Goal
Until now every program you compiled was a single function called `main`. This unit turns `rcc` into a compiler
for real programs: many functions that call each other (including recursively), calls into the C standard library
(`putchar`), programs split across several files, and variables that live outside any function. Along the way you add
the compiler's first **type checker** and a program-wide **symbol table**, generate code that obeys the System V
calling convention so your output can talk to code built by `clang`/`gcc`, and emit data sections for global and
`static` variables. Start once chapters 1–8 pass, after re-reading 6.4 (calling convention) and 6.5 (linking).

## What exists at the end of this unit
- A parser for function declarations, definitions, parameters, calls and the `static`/`extern` storage-class specifiers.
- An identifier-resolution pass that understands **linkage**: names shared across scopes and files are not renamed.
- A type-checker pass and a symbol table that later passes query (codegen now, Unit 12's real types next).
- Code generation for calls: argument registers, stack arguments, alignment padding, caller clean-up, return values.
- A driver flag `-c` that produces an object file, so the test suite can link your output with `clang`-built files.
- Global and `static` variables emitted into `.data`/`.bss` and reached with RIP-relative addressing.
- Programs that print text through libc. **At this point `rcc` is a real, working compiler** for an `int`-only C subset.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [11.1 Functions in the front end](11.1-functions-in-the-front-end.md) | Builds function decls/calls | 4–6 h |
| [11.2 Type checking basics](11.2-type-checking-basics.md) | Builds type checker | 5–7 h |
| [11.3 Calls in assembly](11.3-calls-in-assembly.md) | Builds function codegen (calling convention) | 6–10 h |
| [11.4 Storage and linkage](11.4-storage-and-linkage.md) | Builds globals/static/extern | 8–12 h |

## What comes next
Unit 12 replaces "everything is an `int`" with a real type system: `long`, `unsigned`, `double`, pointers, arrays,
strings and structs. It extends the symbol table you build here with a recursive `Type`, so design that table to grow.
Before moving on, you should pass `--chapter 10` (and all earlier chapters) and be able to draw the stack at the moment
of a `call` with seven or more arguments.
