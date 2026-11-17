# Unit 13 — Optimisation (tests: ch. 19)

**Goal:** so far `rcc` translates C faithfully. Now it also *improves* the program. You add four classic passes that work on TACKY (the IR from 9.2), and two shared pieces of machinery under them: a control-flow graph and a dataflow-analysis framework. This is the "optimisation" box from the back-end map in Part 2 lesson 6.6.

**Before you start:** test chapters 1–18 pass (Units 8–12). Your TACKY generator and assembly back end are stable. The optimiser sits *between* them and must never change what a program prints or returns.

## What exists at the end of this unit
- An optimisation pipeline between TACKY generation and assembly generation. It runs per function and repeats until the function stops changing.
- Four passes: constant folding, unreachable-code elimination, copy propagation and dead-store elimination.
- A control-flow graph (basic blocks plus index-based edges) that you can build from TACKY and flatten back into TACKY.
- A reusable dataflow framework (forward or backward, meet, transfer function, worklist) that Unit 14 reuses for liveness over assembly.
- New `rcc` flags: `--fold-constants`, `--eliminate-unreachable-code`, `--propagate-copies`, `--eliminate-dead-stores`, and `--optimize` (all four).

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [13.1 What optimisers do](13.1-what-optimisers-do.md) | Learning | 2–3 h |
| [13.2 Constant folding](13.2-constant-folding.md) | Builds constant folding | 4–6 h |
| [13.3 Control-flow graphs](13.3-control-flow-graphs.md) | Builds CFG + unreachable-code elimination | 6–8 h |
| [13.4 Dataflow analysis](13.4-dataflow-analysis.md) | Builds dataflow framework | 6–10 h |
| [13.5 Copy propagation](13.5-copy-propagation.md) | Builds copy propagation | 6–8 h |
| [13.6 Dead stores](13.6-dead-stores.md) | Builds dead-store elimination | 5–7 h |

Total: about 29–42 h.

## How to work through it
13.1 is reading and Godbolt only. 13.2 adds the flags and the pipeline loop. 13.3 and 13.4 build the infrastructure (13.4 has no new flag of its own). 13.5 and 13.6 are the two passes that use it. Do the dataflow tables by hand before you code each analysis: if you can't fill in the table, you can't debug the code.

## What comes next
Run the whole suite with `--optimize` (every earlier chapter as well as 19), and write a `JOURNAL.md` entry comparing one test program's assembly before and after. Then go on to [Unit 14: Register Allocation](../unit-14-register-allocation/README.md). Its liveness analysis is the same idea as 13.6, run on assembly with your 13.4 framework, so keep that framework generic.
