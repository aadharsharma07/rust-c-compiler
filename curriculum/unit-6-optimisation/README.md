# Unit 6 — Optimisation (tests: ch. 19)

**Goal:** turn `rcc` from a compiler that translates faithfully into one that also *improves* the program, by adding four classic TACKY-level passes on a shared control-flow graph and dataflow framework.

**Before you start:** test chapters 1–10 pass (11–18 too if you did Unit 5). Your TACKY generator and back end are stable; this unit sits *between* them and must never change what a program prints or returns.

## What exists at the end of this unit
- An optimisation pipeline between TACKY generation and assembly generation, run per function, repeated until the function stops changing.
- Constant folding, unreachable-code elimination, copy propagation and dead-store elimination.
- A control-flow graph (basic blocks + index-based edges) you can build from TACKY and flatten back into TACKY.
- A reusable dataflow framework (forward and backward, meet, transfer, worklist) that Unit 7 will reuse for liveness over assembly.
- CLI flags: `--fold-constants`, `--eliminate-unreachable-code`, `--propagate-copies`, `--eliminate-dead-stores`, and `--optimize` (all four).

## Lessons
| Lesson | Type | Time |
|---|---|---|
| [6.1 What optimisers do](6.1-what-optimisers-do.md) | Learning only | 2–3 h |
| [6.2 Constant folding](6.2-constant-folding.md) | Builds constant folding | 4–6 h |
| [6.3 Control-flow graphs](6.3-control-flow-graphs.md) | Builds CFG + unreachable-code elimination | 6–8 h |
| [6.4 Dataflow analysis](6.4-dataflow-analysis.md) | Builds dataflow framework | 6–10 h |
| [6.5 Copy propagation](6.5-copy-propagation.md) | Builds copy propagation | 6–8 h |
| [6.6 Dead stores](6.6-dead-stores.md) | Builds dead-store elimination | 5–7 h |

Total: about 29–42 h.

## What to do next
Run the whole suite with `--optimize` once more (all earlier chapters as well as 19), and write a `JOURNAL.md` entry comparing one test program's assembly before and after. Then go on to [Unit 7: Register Allocation](../unit-7-register-allocation/README.md). Its liveness analysis runs on the dataflow framework you build here, so keep that framework generic.
