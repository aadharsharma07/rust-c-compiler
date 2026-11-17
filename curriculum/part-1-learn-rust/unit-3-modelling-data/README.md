# Unit 3 — Modelling Data

**Part:** 1 — Learn Rust · **Est. time:** ~20–28 h · **Tests:** none

## Goal
Learn how Rust describes the *shape* of data, and how it makes "missing" and "failed" values
impossible to ignore. In Python you reach for classes, dicts, `None` and exceptions; in Rust you
reach for structs, enums, `Option`, `Result` and the standard collections. These are the tools
every later part of the course is built from: a compiler is, more than anything, a program that
turns one carefully modelled data structure into another.

## What exists at the end
- A set of tested scratch crates covering structs, enums, error handling and collections.
- A working **todo CLI** (`todo add`, `todo list`, `todo done`, …) that saves to a file and
  reports every failure as a clear error message instead of crashing.
- The ability to look at a problem and say "this is a struct, this is an enum, this can be
  absent, this can fail", which is the habit you will use on every compiler data structure.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [3.1 Structs and methods](3.1-structs-and-methods.md) | Learning | 3–4 h |
| [3.2 Enums and pattern matching](3.2-enums-and-match.md) | Learning | 4–5 h |
| [3.3 Option, Result and error handling](3.3-option-and-result.md) | Learning | 4–6 h |
| [3.4 Collections](3.4-collections.md) | Learning | 3–5 h |
| [3.5 Project: todo CLI](3.5-project-todo-cli.md) | Project | 6–8 h |

Lesson 3.2 is the most important lesson in Part 1 for the compiler later on. Don't rush it.

## What comes next
Unit 4 (Abstraction and Organisation) adds traits, generics, iterators, `Box` for recursive
types, lifetimes and proper project structure. You will use `Box` to turn the enums from 3.2
into real trees, the shape a compiler uses for programs.
