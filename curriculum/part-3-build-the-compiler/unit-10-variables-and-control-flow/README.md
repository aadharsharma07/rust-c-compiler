# Unit 10 — Variables, Scope and Control Flow

**Part:** 3 — Build the Compiler · **Est. time:** ~25–37 h (+4–6 h optional) · **Tests:** ch. 5–8

## Goal
Give `rcc` **state** and **control**: local variables and assignment, `if`/`else` and `?:`,
nested blocks with shadowing, and `while`/`do`/`for` with `break`/`continue`. You also add the
first **semantic-analysis** stage (5.4 made real), behind a new `--validate` flag. The back end
barely changes: a C variable is a TACKY variable, and new statements become 9.6's jumps.

## What exists at the end
- A parser that tells declarations, statements and expressions apart, with block items and blocks.
- A variable-resolution pass that renames every local to a unique name and rejects undeclared
  variables, duplicate declarations and invalid assignment targets, with full block scoping.
- A loop-labelling pass that connects every `break` and `continue` to its loop.
- TACKY lowering for `if`, `?:` and all three loops, using only `Jump`, `JumpIfZero`,
  `JumpIfNotZero` and `Label`.
- Optionally: `goto` with labelled statements, and `switch`/`case`/`default`.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [10.1 Statements and declarations](10.1-statements-and-declarations.md) | Builds local vars + assignment | 4–6 h |
| [10.2 Semantic analysis](10.2-semantic-analysis.md) | Builds variable-resolution pass | 5–7 h |
| [10.3 Conditionals](10.3-conditionals.md) | Builds `if`/`else`, `?:` | 3–5 h |
| [10.4 Scope](10.4-scope.md) | Builds compound statements | 4–6 h |
| [10.5 Loops](10.5-loops.md) | Builds loops + loop labelling | 5–7 h |
| [10.6 *(optional)* goto and switch](10.6-goto-and-switch.md) | Builds `goto`, `switch` | 4–6 h |

Lesson 10.6 is optional: nothing later depends on it.

## What comes next
Unit 11 adds functions, calls, a type checker and globals: a real compiler. First pass
`./test_compiler ./target/debug/rcc --chapter 8` and be able to explain why resolution renames
variables and how your scopes handle shadowing.
