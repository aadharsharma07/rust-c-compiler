# Unit 6 — The Machine

**Part:** 2 — Learn Compilers · **Est. time:** ~21–29 h · **Tests:** none

## Goal
Turn a "conceptual and rusty" picture of the computer into a working one, since `rcc` emits
x86-64 assembly. Bottom up: numbers in bits, how a CPU executes instructions, x86-64 in AT&T
syntax, the stack and the System V calling convention, and the toolchain. It ends with a map of
the compiler back end, which is the plan for Part 3.

## What exists at the end
- An x86-64 toolchain on your Mac (Rosetta 2 with `clang -arch x86_64`, or a Docker container),
  able to build and run x86-64 programs.
- The `writing-a-c-compiler-tests` test suite cloned and working, verified against a real compiler.
- Notes full of hand conversions, annotated `clang -S` and Godbolt output, and step-by-step
  stack diagrams of function calls.
- The ability to read the assembly for a small C function (variables, `if`, `while`, calls) and
  explain every line.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [6.1 Numbers in binary](6.1-numbers-in-binary.md) | Learning | 3–4 h |
| [6.2 How a CPU runs code](6.2-how-a-cpu-runs-code.md) | Learning | 3–4 h |
| [6.3 Reading x86-64 assembly](6.3-reading-x86-64-assembly.md) | Learning | 5–7 h |
| [6.4 The stack and function calls](6.4-the-stack-and-calls.md) | Learning | 4–6 h |
| [6.5 The toolchain](6.5-the-toolchain.md) | Learning | 3–4 h |
| [6.6 The back end at a glance](6.6-back-end-overview.md) | Learning | 3–4 h |

Lessons 6.3 and 6.4 matter most: most back-end bugs are a misread instruction or stack slot.

## What comes next
Part 3 starts with Unit 7, a calculator built from Unit 5's lexing and parsing ideas. Unit 8 then
builds the whole pipeline for `int main(void) { return 2; }`, checked by the test suite from 6.5.
