# Unit 9 — Expressions and an IR

**Part:** 3 — Build the Compiler · **Est. time:** ~25–37 h · **Tests:** ch. 2–4

## Goal
Grow `rcc` from `return <constant>;` to full integer expressions: unary `-` `~`, arithmetic
`+ - * / %`, comparisons `== != < <= > >=` and short-circuiting `! && ||`. On the way you add the
two ideas the rest of Part 3 stands on: the **TACKY** IR (5.5's three-address code, made real) and
a **back end built from small passes** (instruction selection, stack slots, fix-up).

## What exists at the end
- A lexer for every operator token in the list above, plus `--` (lexed so it can be rejected).
- A precedence-climbing parser that builds unary and binary expression trees with the right
  precedence and associativity.
- A TACKY IR with temporaries, labels and jumps; an AST→TACKY pass; a `--tacky` stage flag.
- A back end with pseudoregisters, stack frames, and a fix-up pass using `%r10d`/`%r11d`.
- Code generation for `cmp`, `setcc`, `jmp` and `jcc`, with platform-correct local labels.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [9.1 Unary operators](9.1-unary-operators.md) | Builds unary `-`, `~` | 2–3 h |
| [9.2 The TACKY IR](9.2-tacky-ir.md) | Builds TACKY + AST→TACKY | 5–7 h |
| [9.3 Stack frames and fix-ups](9.3-stack-frames.md) | Builds pseudoregister + fix-up passes | 5–8 h |
| [9.4 Precedence climbing](9.4-precedence-climbing.md) | Builds binary-expression parser | 4–6 h |
| [9.5 Arithmetic in assembly](9.5-arithmetic-in-assembly.md) | Builds arithmetic codegen | 3–5 h |
| [9.6 Comparisons and control flow](9.6-comparisons-and-control-flow.md) | Builds relational + logical ops | 6–8 h |

Lessons 9.2 and 9.3 are the heart of the unit: every later unit extends them, so make them clean.

## What comes next
Unit 10 adds variables, `if`, blocks and loops, mostly front-end work on top of 9.6's jumps.
First pass `./test_compiler ./target/debug/rcc --chapter 4`, and be able to hand-translate any
expression into TACKY and then into fixed-up assembly.
