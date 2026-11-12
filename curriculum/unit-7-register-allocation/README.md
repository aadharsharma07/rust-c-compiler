# Unit 7 — Register Allocation (tests: ch. 20)

**Goal:** stop giving every pseudoregister its own stack slot. Instead, keep values in hardware registers wherever possible, using liveness, an interference graph and Chaitin–Briggs graph colouring, then remove most `mov`s with conservative coalescing.

**Before you start:** Unit 6 is done, including a generic CFG and dataflow framework you can run over *assembly* instructions. Your assembly AST still uses pseudoregisters, and pseudo replacement + fix-up still work.

## What exists at the end of this unit
- A register allocator that runs per function between assembly generation and pseudo replacement: liveness → interference graph → coalescing → colouring → rewrite.
- Pseudos that fit get hardware registers; the rest (and every static or aliased variable) still get stack slots or data-section addresses as before.
- Callee-saved registers used by a function are pushed in its prologue and popped before every return, with stack alignment preserved.
- Most register-to-register `mov`s between coalesced values disappear.

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [7.1 Why registers matter](7.1-why-registers-matter.md) | Learning only | 2–3 h |
| [7.2 Interference](7.2-interference.md) | Builds interference-graph builder | 6–8 h |
| [7.3 Graph colouring](7.3-graph-colouring.md) | Builds register allocator | 12–18 h |
| [7.4 Coalescing](7.4-coalescing.md) | Builds coalescing | 8–12 h |

Total: about 28–41 h.

## What to do next: the capstone
1. Write (or adapt) a real C program in the subset `rcc` supports: Conway's Game of Life on a fixed grid is a good choice (arrays, loops, function calls, `putchar`).
2. Compile it with `rcc --optimize`, `clang -O0` and `clang -O1`. Check all three print identical output.
3. Benchmark with many generations (`hyperfine`, or `time` over several runs). Also compare instruction counts and stack usage in the hottest function.
4. Write a postmortem in `JOURNAL.md`: what was faster or slower and why, which passes mattered most, three bugs that taught you something, and what you would redesign if you started again.
