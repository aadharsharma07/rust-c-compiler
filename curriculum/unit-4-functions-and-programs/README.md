# Unit 4 — Functions and Whole Programs

**Tests:** chapters 9–10 · **Est. time:** 26–39 h

## Goal
Go from "one function called `main`" to real multi-function, multi-file C programs that call each other,
call into libc, and share global state. You add the first type checker with a persistent **symbol table**,
learn the System V AMD64 calling convention well enough to interoperate with code compiled by `gcc`/`clang`,
and implement storage classes, linkage and static storage in `.data`/`.bss`.

## What exists at the end of this unit
- Parsing of function declarations, definitions, parameters, calls, and `static`/`extern` specifiers.
- Identifier resolution that understands linkage (functions and `extern` names are not renamed).
- A type-checker pass and symbol table recording types, definitions, linkage and initial values.
- Assembly for calls: argument registers, stack arguments, alignment padding, caller clean-up.
- A driver that supports `-c` (object file only) so the test suite can link your output with `gcc`-built files.
- File-scope and `static` local variables emitted with `.globl`, `.data`, `.bss` and RIP-relative operands.
- Programs that print via libc `putchar`. At this point `rcc` is a real, working compiler for an `int`-only subset of C.

## Lessons
| Lesson | Builds | Time |
|---|---|---|
| [4.1 Functions in the front end](4.1-functions-in-the-front-end.md) | Function decls/calls in parser + resolver | 4–6 h |
| [4.2 Type checking basics](4.2-type-checking-basics.md) | Type-checker pass | 5–7 h |
| [4.3 The System V calling convention](4.3-system-v-calling-convention.md) | Learning only | 3–4 h |
| [4.4 Calls in assembly](4.4-calls-in-assembly.md) | Function codegen → printing programs | 6–10 h |
| [4.5 Storage & linkage](4.5-storage-and-linkage.md) | Global/static variables | 8–12 h |

## Before starting Unit 5 you should
- Pass `./test_compiler ./target/debug/rcc --chapter 10` (and all earlier chapters).
- Be able to draw a stack frame at the moment of a `call` with seven or more arguments.
- Have a symbol table that later passes can query, because Unit 5 adds a real `Type` enum to it.
- Be comfortable adding a field to every AST node of one kind (types will annotate expressions next).
