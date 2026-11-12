# Unit 3 — Variables, Scope and Control Flow

**Tests:** chapters 5–8 · **Est. time:** 25–37 h (+4–6 h optional)

## Goal
Turn the expression calculator from Units 1–2 into a language with *state* and *control*:
named local variables, assignment, `if`/`else`, `?:`, nested blocks with shadowing, and
`while`/`do`/`for` with `break`/`continue`. Along the way you add the first **semantic-analysis**
stage, which checks things a grammar cannot express, and is exposed by a new `--validate` driver flag.

## What exists at the end of this unit
- A parser that distinguishes *statements*, *declarations* and *expressions*, with block items.
- A variable-resolution pass that renames every local to a unique name and rejects undeclared
  variables, duplicate declarations and invalid lvalues.
- Scoped resolution (blocks, shadowing) and a loop-labelling pass that attaches every
  `break`/`continue` to its enclosing loop.
- TACKY lowering for conditionals and loops built only from `Jump`, `JumpIfZero`,
  `JumpIfNotZero` and `Label`, so the assembly back end barely changes.
- Optionally: `goto` with labelled statements and `switch`/`case`/`default`.

## Lessons
| Lesson | Builds | Time |
|---|---|---|
| [3.1 Statements vs. expressions](3.1-statements-vs-expressions.md) | Local vars + assignment | 4–6 h |
| [3.2 Semantic analysis](3.2-semantic-analysis.md) | Variable-resolution pass | 5–7 h |
| [3.3 Conditionals](3.3-conditionals.md) | `if`/`else`, `?:` | 3–5 h |
| [3.4 Scope](3.4-scope.md) | Compound statements | 4–6 h |
| [3.5 Loops](3.5-loops.md) | Loops + loop-labelling pass | 5–7 h |
| [3.6 *(optional)* goto & switch](3.6-goto-and-switch.md) | `goto`, `switch` | 4–6 h |

## Before starting Unit 4 you should
- Pass `./test_compiler ./target/debug/rcc --chapter 8` (and, if you did 3.6, the `--goto`/`--switch` extra credit).
- Be able to explain why resolution renames variables, and how your scope structure handles shadowing.
- Have a semantic-analysis module that can grow new passes (Unit 4 adds a type checker after resolution).
- Have a `cargo clippy` clean tree and a unique-name/label generator shared by all passes.
