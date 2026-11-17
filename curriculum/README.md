# Syllabus: Learn Rust → Learn Compilers → Build a C Compiler in Rust

This is the source of truth for the course structure. It has three parts, done in order:

| Part | What | Lessons | Est. time |
|---|---|---|---|
| **1. Learn Rust** | Rust from zero, for a Python programmer, through small Rust projects | 22 | ~80–110 h |
| **2. Learn Compilers** | How languages are processed, and how the machine runs code, practised by hand and with Python's `tokenize`/`ast`/`dis` | 11 | ~40–60 h |
| **3. Build the Compiler** | A C compiler (`rcc`) in Rust that emits x86-64 assembly, checked by the official test suite | 43 | ~240–350 h |

At about 8 hours/week, that's about **11–16 months** in total:
- Part 1: about 3 months
- Part 2: about 1.5 months
- Part 3 to a working compiler (through Unit 11): about 3 months more

**Lesson types:**
- **Learning:** explanation + exercises
- **Project:** a small standalone program
- **Builds X:** adds a piece of the compiler

**Every lesson has the same layout (explain, then build):** Overview · The lesson · Build · Check your understanding · Common pitfalls · Done when · Go deeper.

**Test suite (Part 3):** https://github.com/nlsandler/writing-a-c-compiler-tests. Run `./test_compiler /path/to/rcc --chapter N` (add `--stage lex|parse|tacky|codegen` for partial checks). Part 3 follows the chapter order of Nora Sandler's *Writing a C Compiler*.

---

# Part 1: Learn Rust · [part-1-learn-rust/](part-1-learn-rust/)

## Unit 1: Rust Basics for Python Programmers (~13–19 h)
| Lesson | Type | Time |
|---|---|---|
| [1.1 How Rust differs from Python](part-1-learn-rust/unit-1-rust-basics/1.1-rust-vs-python.md) (compiled vs. interpreted, static types, no GC; install rustup, cargo, hello world) | Learning | 2–3 h |
| [1.2 Variables and types](part-1-learn-rust/unit-1-rust-basics/1.2-variables-and-types.md) (`let`, `mut`, shadowing, integer/float/bool/char types, annotations vs. Python's dynamic typing) | Learning | 3–4 h |
| [1.3 Functions and expressions](part-1-learn-rust/unit-1-rust-basics/1.3-functions-and-expressions.md) (`fn`, parameter/return types, expressions vs. statements, blocks have values) | Learning | 2–3 h |
| [1.4 Control flow](part-1-learn-rust/unit-1-rust-basics/1.4-control-flow.md) (`if` as an expression, `loop`/`while`/`for`, ranges, a first look at `match`) | Learning | 2–3 h |
| [1.5 Project: guessing game](part-1-learn-rust/unit-1-rust-basics/1.5-project-guessing-game.md) (stdin, parsing, a loop, an external crate) | Project | 4–6 h |

## Unit 2: Ownership and Memory (~18–25 h)
| Lesson | Type | Time |
|---|---|---|
| [2.1 The stack and the heap](part-1-learn-rust/unit-2-ownership-and-memory/2.1-stack-and-heap.md) (how Python manages memory vs. how Rust does) | Learning | 3–4 h |
| [2.2 Ownership and moves](part-1-learn-rust/unit-2-ownership-and-memory/2.2-ownership-and-moves.md) (ownership rules, move, `Copy`, `Clone`, drop) | Learning | 4–5 h |
| [2.3 References and borrowing](part-1-learn-rust/unit-2-ownership-and-memory/2.3-references-and-borrowing.md) (`&`, `&mut`, borrow rules, reading borrow-checker errors) | Learning | 4–6 h |
| [2.4 Slices and strings](part-1-learn-rust/unit-2-ownership-and-memory/2.4-slices-and-strings.md) (`String` vs. `&str` vs. Python `str`, UTF-8, slices) | Learning | 3–4 h |
| [2.5 Project: text statistics tool](part-1-learn-rust/unit-2-ownership-and-memory/2.5-project-text-stats.md) (read a file, count words/lines/frequencies) | Project | 4–6 h |

## Unit 3: Modelling Data (~20–28 h)
| Lesson | Type | Time |
|---|---|---|
| [3.1 Structs and methods](part-1-learn-rust/unit-3-modelling-data/3.1-structs-and-methods.md) (vs. Python classes/dataclasses; `impl`, associated functions) | Learning | 3–4 h |
| [3.2 Enums and pattern matching](part-1-learn-rust/unit-3-modelling-data/3.2-enums-and-match.md) (variants with data, exhaustive `match`, `if let`) | Learning | 4–5 h |
| [3.3 Option, Result and error handling](part-1-learn-rust/unit-3-modelling-data/3.3-option-and-result.md) (no `None` surprises or exceptions; `?`, custom error enums, `panic!`) | Learning | 4–6 h |
| [3.4 Collections](part-1-learn-rust/unit-3-modelling-data/3.4-collections.md) (`Vec`/`HashMap`/`HashSet` vs. list/dict/set; the entry API) | Learning | 3–5 h |
| [3.5 Project: todo CLI](part-1-learn-rust/unit-3-modelling-data/3.5-project-todo-cli.md) (commands, file persistence, proper error handling) | Project | 6–8 h |

## Unit 4: Abstraction and Organisation (~27–38 h)
| Lesson | Type | Time |
|---|---|---|
| [4.1 Traits](part-1-learn-rust/unit-4-abstraction-and-organisation/4.1-traits.md) (vs. duck typing/ABCs/Protocols; `Display`, `Debug`, `derive`) | Learning | 3–5 h |
| [4.2 Generics](part-1-learn-rust/unit-4-abstraction-and-organisation/4.2-generics.md) (generic functions/structs, trait bounds) | Learning | 3–4 h |
| [4.3 Closures and iterators](part-1-learn-rust/unit-4-abstraction-and-organisation/4.3-closures-and-iterators.md) (vs. lambdas/comprehensions/generators; adapters, `collect`, `peekable`) | Learning | 4–5 h |
| [4.4 Smart pointers and recursive types](part-1-learn-rust/unit-4-abstraction-and-organisation/4.4-smart-pointers.md) (`Box`, recursive enums/trees, `Rc`, `RefCell`) | Learning | 4–6 h |
| [4.5 Lifetimes](part-1-learn-rust/unit-4-abstraction-and-organisation/4.5-lifetimes.md) (what they are, when you must write them, `'static`) | Learning | 4–6 h |
| [4.6 Modules, testing and tooling](part-1-learn-rust/unit-4-abstraction-and-organisation/4.6-modules-testing-tooling.md) (`mod`, `pub`, crates, unit/integration tests, clippy, fmt, docs) | Learning | 3–4 h |
| [4.7 Project: file search tool](part-1-learn-rust/unit-4-abstraction-and-organisation/4.7-project-file-search.md) (a grep-like CLI with modules, errors, iterators and tests) | Project | 6–8 h |

---

# Part 2: Learn Compilers · [part-2-learn-compilers/](part-2-learn-compilers/)

## Unit 5: How Languages Are Processed (~18–26 h)
| Lesson | Type | Time |
|---|---|---|
| [5.1 Compilers and interpreters](part-2-learn-compilers/unit-5-how-languages-are-processed/5.1-compilers-and-interpreters.md) (phases; compiler vs. interpreter vs. bytecode VM; how CPython runs your code) | Learning | 3–4 h |
| [5.2 Lexing](part-2-learn-compilers/unit-5-how-languages-are-processed/5.2-lexing.md) (tokens, regular expressions, finite automata, longest match; Python's `tokenize`) | Learning | 3–5 h |
| [5.3 Grammars and parsing](part-2-learn-compilers/unit-5-how-languages-are-processed/5.3-grammars-and-parsing.md) (BNF, derivations, parse trees, ambiguity, precedence/associativity, recursive descent by hand) | Learning | 5–7 h |
| [5.4 ASTs and semantic analysis](part-2-learn-compilers/unit-5-how-languages-are-processed/5.4-asts-and-semantic-analysis.md) (AST vs. parse tree; Python's `ast`; scopes, symbol tables, type checking) | Learning | 4–5 h |
| [5.5 Intermediate representations](part-2-learn-compilers/unit-5-how-languages-are-processed/5.5-intermediate-representations.md) (three-address code, why IRs exist; Python's `dis` bytecode as an IR) | Learning | 3–5 h |

## Unit 6: The Machine (~21–29 h)
| Lesson | Type | Time |
|---|---|---|
| [6.1 Numbers in binary](part-2-learn-compilers/unit-6-the-machine/6.1-numbers-in-binary.md) (binary, hex, two's complement, overflow, sign/zero extension) | Learning | 3–4 h |
| [6.2 How a CPU runs code](part-2-learn-compilers/unit-6-the-machine/6.2-how-a-cpu-runs-code.md) (fetch–decode–execute, registers, memory, flags) | Learning | 3–4 h |
| [6.3 Reading x86-64 assembly](part-2-learn-compilers/unit-6-the-machine/6.3-reading-x86-64-assembly.md) (AT&T syntax, core instructions, Godbolt; running x86-64 on Apple Silicon) | Learning | 5–7 h |
| [6.4 The stack and function calls](part-2-learn-compilers/unit-6-the-machine/6.4-the-stack-and-calls.md) (stack frames, `rbp`/`rsp`, `call`/`ret`, the System V calling convention) | Learning | 4–6 h |
| [6.5 The toolchain](part-2-learn-compilers/unit-6-the-machine/6.5-the-toolchain.md) (preprocessor, compiler, assembler, linker, object files, symbols; setting up the test suite) | Learning | 3–4 h |
| [6.6 The back end at a glance](part-2-learn-compilers/unit-6-the-machine/6.6-back-end-overview.md) (code generation, optimisation, register allocation; a map of Part 3) | Learning | 3–4 h |

---

# Part 3: Build the Compiler in Rust · [part-3-build-the-compiler/](part-3-build-the-compiler/)

## Unit 7: Warm-up, a Calculator (~11–17 h · no test suite)
| Lesson | Type | Time |
|---|---|---|
| [7.1 Calculator lexer](part-3-build-the-compiler/unit-7-calculator/7.1-calculator-lexer.md) | Builds lexer | 3–5 h |
| [7.2 Calculator parser](part-3-build-the-compiler/unit-7-calculator/7.2-calculator-parser.md) | Builds recursive-descent parser + AST | 5–8 h |
| [7.3 Evaluator and REPL](part-3-build-the-compiler/unit-7-calculator/7.3-evaluator-and-repl.md) | Builds evaluator + REPL | 3–4 h |

## Unit 8: The Whole Pipeline for `return 2;` (tests: ch. 1) (~16–26 h)
| Lesson | Type | Time |
|---|---|---|
| [8.1 The compiler driver](part-3-build-the-compiler/unit-8-whole-pipeline/8.1-compiler-driver.md) | Builds `rcc` CLI + stage flags | 3–5 h |
| [8.2 Lexing C](part-3-build-the-compiler/unit-8-whole-pipeline/8.2-lexing-c.md) | Builds C lexer | 4–6 h |
| [8.3 Parsing C](part-3-build-the-compiler/unit-8-whole-pipeline/8.3-parsing-c.md) | Builds AST + parser | 5–8 h |
| [8.4 Assembly generation](part-3-build-the-compiler/unit-8-whole-pipeline/8.4-assembly-generation.md) | Builds assembly AST + codegen | 2–3 h |
| [8.5 Code emission](part-3-build-the-compiler/unit-8-whole-pipeline/8.5-code-emission.md) | Builds emitter → first executable | 2–4 h |

## Unit 9: Expressions and an IR (tests: ch. 2–4) (~25–37 h)
| Lesson | Type | Time |
|---|---|---|
| [9.1 Unary operators](part-3-build-the-compiler/unit-9-expressions-and-ir/9.1-unary-operators.md) | Builds unary `-`, `~` | 2–3 h |
| [9.2 The TACKY IR](part-3-build-the-compiler/unit-9-expressions-and-ir/9.2-tacky-ir.md) | Builds TACKY + AST→TACKY | 5–7 h |
| [9.3 Stack frames and fix-ups](part-3-build-the-compiler/unit-9-expressions-and-ir/9.3-stack-frames.md) | Builds pseudoregister + fix-up passes | 5–8 h |
| [9.4 Precedence climbing](part-3-build-the-compiler/unit-9-expressions-and-ir/9.4-precedence-climbing.md) | Builds binary-expression parser | 4–6 h |
| [9.5 Arithmetic in assembly](part-3-build-the-compiler/unit-9-expressions-and-ir/9.5-arithmetic-in-assembly.md) | Builds arithmetic codegen | 3–5 h |
| [9.6 Comparisons and control flow](part-3-build-the-compiler/unit-9-expressions-and-ir/9.6-comparisons-and-control-flow.md) | Builds relational + logical ops | 6–8 h |

## Unit 10: Variables, Scope and Control Flow (tests: ch. 5–8) (~25–37 h, +4–6 h optional)
| Lesson | Type | Time |
|---|---|---|
| [10.1 Statements and declarations](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.1-statements-and-declarations.md) | Builds local vars + assignment | 4–6 h |
| [10.2 Semantic analysis](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.2-semantic-analysis.md) | Builds variable-resolution pass | 5–7 h |
| [10.3 Conditionals](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.3-conditionals.md) | Builds `if`/`else`, `?:` | 3–5 h |
| [10.4 Scope](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.4-scope.md) | Builds compound statements | 4–6 h |
| [10.5 Loops](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.5-loops.md) | Builds loops + loop labelling | 5–7 h |
| [10.6 *(optional)* goto and switch](part-3-build-the-compiler/unit-10-variables-and-control-flow/10.6-goto-and-switch.md) | Builds `goto`, `switch` | 4–6 h |

## Unit 11: Functions and Whole Programs (tests: ch. 9–10) (~23–35 h)
| Lesson | Type | Time |
|---|---|---|
| [11.1 Functions in the front end](part-3-build-the-compiler/unit-11-functions-and-programs/11.1-functions-in-the-front-end.md) | Builds function decls/calls | 4–6 h |
| [11.2 Type checking basics](part-3-build-the-compiler/unit-11-functions-and-programs/11.2-type-checking-basics.md) | Builds type checker | 5–7 h |
| [11.3 Calls in assembly](part-3-build-the-compiler/unit-11-functions-and-programs/11.3-calls-in-assembly.md) | Builds function codegen (calling convention) | 6–10 h |
| [11.4 Storage and linkage](part-3-build-the-compiler/unit-11-functions-and-programs/11.4-storage-and-linkage.md) | Builds globals/static/extern | 8–12 h |

> At this point you have a real, working compiler.

## Unit 12: A Real Type System (tests: ch. 11–18) (~80–120 h)
| Lesson | Type | Time |
|---|---|---|
| [12.1 Types in a compiler](part-3-build-the-compiler/unit-12-type-system/12.1-types-in-a-compiler.md) | Builds `Type` + typed AST | 4–6 h |
| [12.2 long](part-3-build-the-compiler/unit-12-type-system/12.2-long.md) | Builds `long` | 10–14 h |
| [12.3 unsigned](part-3-build-the-compiler/unit-12-type-system/12.3-unsigned.md) | Builds `unsigned` | 8–12 h |
| [12.4 Floating point](part-3-build-the-compiler/unit-12-type-system/12.4-floating-point.md) | Builds `double` | 12–18 h |
| [12.5 Pointers](part-3-build-the-compiler/unit-12-type-system/12.5-pointers.md) | Builds `&`, `*` | 10–14 h |
| [12.6 Arrays](part-3-build-the-compiler/unit-12-type-system/12.6-arrays.md) | Builds arrays | 10–14 h |
| [12.7 Characters and strings](part-3-build-the-compiler/unit-12-type-system/12.7-characters-and-strings.md) | Builds `char`, strings | 6–8 h |
| [12.8 Memory](part-3-build-the-compiler/unit-12-type-system/12.8-memory.md) | Builds `void`, `sizeof`, `malloc` | 5–8 h |
| [12.9 Structs](part-3-build-the-compiler/unit-12-type-system/12.9-structs.md) | Builds structs | 15–25 h |

## Unit 13: Optimisation (tests: ch. 19) (~29–42 h)
| Lesson | Type | Time |
|---|---|---|
| [13.1 What optimisers do](part-3-build-the-compiler/unit-13-optimisation/13.1-what-optimisers-do.md) | Learning | 2–3 h |
| [13.2 Constant folding](part-3-build-the-compiler/unit-13-optimisation/13.2-constant-folding.md) | Builds constant folding | 4–6 h |
| [13.3 Control-flow graphs](part-3-build-the-compiler/unit-13-optimisation/13.3-control-flow-graphs.md) | Builds CFG + unreachable-code elimination | 6–8 h |
| [13.4 Dataflow analysis](part-3-build-the-compiler/unit-13-optimisation/13.4-dataflow-analysis.md) | Builds dataflow framework | 6–10 h |
| [13.5 Copy propagation](part-3-build-the-compiler/unit-13-optimisation/13.5-copy-propagation.md) | Builds copy propagation | 6–8 h |
| [13.6 Dead stores](part-3-build-the-compiler/unit-13-optimisation/13.6-dead-stores.md) | Builds dead-store elimination | 5–7 h |

## Unit 14: Register Allocation (tests: ch. 20) (~28–41 h)
| Lesson | Type | Time |
|---|---|---|
| [14.1 Why registers matter](part-3-build-the-compiler/unit-14-register-allocation/14.1-why-registers-matter.md) | Learning | 2–3 h |
| [14.2 Interference](part-3-build-the-compiler/unit-14-register-allocation/14.2-interference.md) | Builds interference graph | 6–8 h |
| [14.3 Graph colouring](part-3-build-the-compiler/unit-14-register-allocation/14.3-graph-colouring.md) | Builds register allocator | 12–18 h |
| [14.4 Coalescing](part-3-build-the-compiler/unit-14-register-allocation/14.4-coalescing.md) | Builds coalescing | 8–12 h |
