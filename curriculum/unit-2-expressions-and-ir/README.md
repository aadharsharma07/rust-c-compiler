# Unit 2 — Expressions and an IR

**Goal:** grow `rcc` from "return a constant" to full integer expressions: unary `-` and `~`,
arithmetic, relational operators and short-circuiting `&&`/`||`. Along the way you add the
course's central intermediate representation, **TACKY** (three-address code), and the back-end
passes every later unit relies on: pseudoregister allocation, stack frames and instruction fix-up.

**Est. time:** ~25–37 h · **Tests:** chapters 2–4 (`--chapter N` also reruns earlier chapters; `--latest-only` skips them).

## What exists at the end of this unit
- A lexer for the operator tokens `-` `~` `--` `+` `*` `/` `%` `!` `&&` `||` `==` `!=` `<` `>` `<=` `>=`
  (plus `&` `|` `^` `<<` `>>` if you do the optional bitwise extension).
- A precedence-climbing expression parser and an AST with unary and binary expressions.
- A TACKY IR with temporaries, labels and jumps, an AST→TACKY pass, and a `--tacky` stage flag.
- An assembly back end with pseudoregisters → stack slots, a prologue/epilogue, and a fix-up pass
  that legalises `mov`, `add`/`sub`, `imul`, `idiv` and `cmp` operands using `%r10d`/`%r11d`.
- Code generation for `cmp`/`setcc`/`jmp`/`jcc` with platform-correct local labels.

## Lessons

| Lesson | Type | Time |
|---|---|---|
| [2.1 Unary operators](2.1-unary-operators.md) | Builds unary `-`, `~` | 2–3 h |
| [2.2 Why IRs exist](2.2-why-irs-exist.md) | Builds TACKY IR + AST→TACKY | 5–7 h |
| [2.3 Stack frames](2.3-stack-frames.md) | Builds pseudoregister + fix-up passes | 5–8 h |
| [2.4 Precedence climbing](2.4-precedence-climbing.md) | Builds binary-expression parser | 4–6 h |
| [2.5 Arithmetic in assembly](2.5-arithmetic-in-assembly.md) | Builds arithmetic codegen (optional: bitwise ops) | 3–5 h |
| [2.6 Comparisons & control flow](2.6-comparisons-and-control-flow.md) | Builds relational + logical ops | 6–8 h |

## Before starting Unit 3 you should
- Pass `./test_compiler ./target/debug/rcc --chapter 4` (chapters 1–4).
- Be able to hand-translate any expression into TACKY and then into fixed-up assembly.
- Explain why `idiv`, `imul`, `cmp` and two-memory-operand `mov` need fix-ups.
- Have a TACKY generator whose labels and temporaries are guaranteed unique: Unit 3 adds
  variables, `if` and loops on top of exactly this machinery.
