# Unit 2 — Ownership and Memory

**Part:** 1 — Learn Rust · **Est. time:** ~18–25 h · **Tests:** none (you check your own programs by running them)

## Goal
Understand where your program's data actually lives in memory, and the rules Rust uses to free
that memory safely without a garbage collector. You'll start from the machine (the stack and
the heap), compare it with how Python manages memory for you, and then learn ownership, moves,
borrowing and string slices. This is the hardest unit in Part 1, and the most important.

## What exists at the end of this unit
- Clear mental pictures (you can draw them) of the stack, the heap, and what a `String` looks like in memory.
- Scratch crates where you predicted, triggered and explained ownership and borrow errors.
- A finished **text statistics tool**: a command-line program that reads a file and reports
  line, word and character counts and the most frequent words.
- The ability to read a borrow-checker error and say which rule it enforces.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [2.1 The stack and the heap](2.1-stack-and-heap.md) | Learning | 3–4 h |
| [2.2 Ownership and moves](2.2-ownership-and-moves.md) | Learning | 4–5 h |
| [2.3 References and borrowing](2.3-references-and-borrowing.md) | Learning | 4–6 h |
| [2.4 Slices and strings](2.4-slices-and-strings.md) | Learning | 3–4 h |
| [2.5 Project: text statistics tool](2.5-project-text-stats.md) | Project | 4–6 h |

## How this unit connects to the compiler
Your compiler will read C source into one `String`, chop it into tokens and build trees: each
step raises the question of who owns what. The stack picture from 2.1 returns in 6.4 and in
Part 3, where your compiler lays out stack frames itself.

## What comes next
**Unit 3 — Modelling Data.** Structs, enums with data, `Option` and `Result` for errors, and
the standard collections (`Vec`, `HashMap`, `HashSet`). With ownership in hand, you'll be able
to design your own types, which is how you'll represent tokens and syntax trees later.
