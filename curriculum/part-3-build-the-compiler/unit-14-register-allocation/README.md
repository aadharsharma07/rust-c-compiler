# Unit 14 — Register Allocation (tests: ch. 20)

**Part:** 3 — Build the Compiler · **Est. time:** ~28–41 h

## Goal
Since Unit 9, every pseudoregister has had its own stack slot, so almost every instruction your compiler emits touches
memory. This unit keeps values in the CPU's registers instead. You run liveness analysis over assembly, build an
**interference graph** recording which values can't share a register, **colour** it with the Chaitin–Briggs algorithm
to assign registers, and finally **coalesce** away most register-to-register moves.

## Before you start
Unit 13 is done, including a CFG and a dataflow framework you can reuse over *assembly* instructions. Your back end
still produces assembly with pseudoregisters, followed by pseudo replacement and fix-ups. Re-read 6.4 (caller- vs.
callee-saved registers) and 13.6 (liveness).

## What exists at the end of this unit
- A register allocator that runs per function between assembly generation and pseudo replacement:
  liveness → interference graph → coalescing → colouring → rewrite.
- Pseudos that fit get hardware registers; the rest, and every static or address-taken variable, still go to memory.
- Callee-saved registers a function uses are saved in its prologue and restored before every return, with the stack still 16-byte aligned.
- Most `mov`s between coalesced values are gone.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [14.1 Why registers matter](14.1-why-registers-matter.md) | Learning | 2–3 h |
| [14.2 Interference](14.2-interference.md) | Builds interference graph | 6–8 h |
| [14.3 Graph colouring](14.3-graph-colouring.md) | Builds register allocator | 12–18 h |
| [14.4 Coalescing](14.4-coalescing.md) | Builds coalescing | 8–12 h |

## What comes next: a capstone
The syllabus ends here, but one project is worth doing to close the loop:
1. Write (or adapt) a real C program in the subset `rcc` supports. Conway's Game of Life on a fixed grid is a good
   choice: arrays, nested loops, calls and `putchar` output.
2. Compile it three ways: `rcc` with all optimisations, `clang -O0` and `clang -O1`. Check all three print identical output.
3. Benchmark over many generations (`hyperfine`, or `time` over several runs). Compare instruction counts and stack use in the hottest function.
4. Write a postmortem in `JOURNAL.md`: what was faster or slower and why, which passes mattered most, three bugs that
   taught you something, and what you would redesign if you started again.
