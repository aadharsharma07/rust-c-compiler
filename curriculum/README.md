# Syllabus: Building a C Compiler in Rust

This is the source of truth for the course structure. Each lesson either **builds** a piece of the compiler or is **learning only** (background for what comes next). Times are for focused work.

At about 8 hours/week:
- **Units 0–4 (a working compiler):** about 155 hours ≈ 4–5 months
- **Everything:** about 330 hours ≈ 9–11 months

**Test suite:** https://github.com/nlsandler/writing-a-c-compiler-tests. After each building lesson, run:
`./test_compiler /path/to/rcc --chapter N` (add `--stage lex|parse|tacky|codegen` for partial checks).

**Lesson file layout:** Learning goals · Key ideas · Questions the tutor should ask you · What you build · Rust focus · Common pitfalls · Done when · Self-check quiz.

---

## Unit 0: Rust Foundations (~25–37 h) · [unit-0-rust-foundations/](unit-0-rust-foundations/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [0.1 What a compiler is](unit-0-rust-foundations/0.1-what-a-compiler-is.md) | Compiler phases; cargo, rustup, `cargo test`, clippy | Learning only | 2–3 h |
| [0.2 Ownership & borrowing](unit-0-rust-foundations/0.2-ownership-and-borrowing.md) | Moves, `&`/`&mut`, `String` vs. `&str` | Learning only | 4–6 h |
| [0.3 Modelling data](unit-0-rust-foundations/0.3-modelling-data.md) | `struct`, `enum` with data, `match`, `Option`, `Result`, `?` | Learning only | 4–6 h |
| [0.4 Trees in Rust](unit-0-rust-foundations/0.4-trees-in-rust.md) | `Box<T>`, recursive enums; the idea of an AST | Learning only | 3–4 h |
| [0.5 Lexing](unit-0-rust-foundations/0.5-lexing.md) | Tokens, lexemes, longest match; `peekable()` | Calculator lexer | 3–5 h |
| [0.6 Parsing](unit-0-rust-foundations/0.6-parsing.md) | Grammars/BNF, recursive descent, precedence via grammar levels | Calculator parser + evaluator | 5–8 h |
| [0.7 Organising code](unit-0-rust-foundations/0.7-organising-code.md) | Traits (`Display`), modules, `pub` | Calculator REPL in modules | 3–4 h |

## Unit 1: The Whole Pipeline for `return 2;` (tests: ch. 1) (~20–30 h) · [unit-1-whole-pipeline/](unit-1-whole-pipeline/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [1.1 The target machine](unit-1-whole-pipeline/1.1-the-target-machine.md) | x86-64 registers, `mov`/`ret`, assembler vs. linker; Godbolt; Rosetta/Docker | Learning only | 3–4 h |
| [1.2 The compiler driver](unit-1-whole-pipeline/1.2-the-compiler-driver.md) | preprocess → compile → assemble → link; `std::env`/`fs`/`process` | `rcc` CLI + stage flags | 3–5 h |
| [1.3 Lexing C](unit-1-whole-pipeline/1.3-lexing-c.md) | Keywords, identifiers, constants, invalid tokens; lifetimes intro | Lexer | 4–6 h |
| [1.4 Grammar & AST](unit-1-whole-pipeline/1.4-grammar-and-ast.md) | Formal grammar; abstract vs. concrete syntax | AST + recursive-descent parser | 5–8 h |
| [1.5 Assembly representation](unit-1-whole-pipeline/1.5-assembly-representation.md) | Why compilers use several IR levels | Assembly AST + AST→asm pass | 2–3 h |
| [1.6 Code emission](unit-1-whole-pipeline/1.6-code-emission.md) | Assembly syntax, macOS `_` prefix; `fmt::Write` | Emitter → first executable | 2–4 h |

## Unit 2: Expressions and an IR (tests: ch. 2–4) (~25–37 h) · [unit-2-expressions-and-ir/](unit-2-expressions-and-ir/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [2.1 Unary operators](unit-2-expressions-and-ir/2.1-unary-operators.md) | Extending a grammar; why `--` is rejected | Unary `-`, `~` | 2–3 h |
| [2.2 Why IRs exist](unit-2-expressions-and-ir/2.2-why-irs-exist.md) | Three-address code, temporaries, flattening trees | TACKY IR + AST→TACKY | 5–7 h |
| [2.3 Stack frames](unit-2-expressions-and-ir/2.3-stack-frames.md) | `rbp`/`rsp`, prologue/epilogue, instruction constraints | Pseudoregister + fix-up passes | 5–8 h |
| [2.4 Precedence climbing](unit-2-expressions-and-ir/2.4-precedence-climbing.md) | Precedence and associativity | Binary-expression parser | 4–6 h |
| [2.5 Arithmetic in assembly](unit-2-expressions-and-ir/2.5-arithmetic-in-assembly.md) | `add`/`sub`/`imul`/`idiv`/`cdq` | Arithmetic codegen (optional: bitwise ops) | 3–5 h |
| [2.6 Comparisons & control flow](unit-2-expressions-and-ir/2.6-comparisons-and-control-flow.md) | `cmp`/`setcc`, jumps, labels, short-circuit evaluation | Relational + logical ops | 6–8 h |

## Unit 3: Variables, Scope and Control Flow (tests: ch. 5–8) (~25–37 h, +4–6 h optional) · [unit-3-variables-and-control-flow/](unit-3-variables-and-control-flow/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [3.1 Statements vs. expressions](unit-3-variables-and-control-flow/3.1-statements-vs-expressions.md) | Declarations, assignment, lvalues; refactoring enums | Local vars + assignment | 4–6 h |
| [3.2 Semantic analysis](unit-3-variables-and-control-flow/3.2-semantic-analysis.md) | Why checking is separate from parsing; `HashMap` | Variable-resolution pass | 5–7 h |
| [3.3 Conditionals](unit-3-variables-and-control-flow/3.3-conditionals.md) | Dangling else; branches lowered to jumps | `if`/`else`, `?:` | 3–5 h |
| [3.4 Scope](unit-3-variables-and-control-flow/3.4-scope.md) | Block scope, shadowing, scope chains; clone vs. borrow | Compound statements | 4–6 h |
| [3.5 Loops](unit-3-variables-and-control-flow/3.5-loops.md) | How `break`/`continue` find their loop | Loops + loop-labelling pass | 5–7 h |
| [3.6 *(optional)* goto & switch](unit-3-variables-and-control-flow/3.6-goto-and-switch.md) | Label resolution; jump tables | `goto`, `switch` | 4–6 h |

## Unit 4: Functions and Whole Programs (tests: ch. 9–10) (~26–39 h) · [unit-4-functions-and-programs/](unit-4-functions-and-programs/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [4.1 Functions in the front end](unit-4-functions-and-programs/4.1-functions-in-the-front-end.md) | Prototypes vs. definitions | Function decls/calls in parser + resolver | 4–6 h |
| [4.2 Type checking basics](unit-4-functions-and-programs/4.2-type-checking-basics.md) | Symbol tables, arity, conflicting declarations | Type-checker pass | 5–7 h |
| [4.3 The System V calling convention](unit-4-functions-and-programs/4.3-system-v-calling-convention.md) | Argument registers, stack args, alignment, saved registers | Learning only | 3–4 h |
| [4.4 Calls in assembly](unit-4-functions-and-programs/4.4-calls-in-assembly.md) | `call`, parameter copy-in, linking libc | Function codegen → printing programs | 6–10 h |
| [4.5 Storage & linkage](unit-4-functions-and-programs/4.5-storage-and-linkage.md) | `static`/`extern`, tentative definitions, `.data`/`.bss`, RIP-relative addressing | Global/static variables | 8–12 h |

> At this point you have a real, working compiler.

## Unit 5: A Real Type System (tests: ch. 11–18) (~80–120 h) · [unit-5-type-system/](unit-5-type-system/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [5.1 Types in a compiler](unit-5-type-system/5.1-types-in-a-compiler.md) | Typed ASTs, implicit conversions | `Type` enum + typed AST | 4–6 h |
| [5.2 long](unit-5-type-system/5.2-long.md) | Sign extension, 32- vs. 64-bit operands | `long` | 10–14 h |
| [5.3 unsigned](unit-5-type-system/5.3-unsigned.md) | Promotion, unsigned compare/divide, zero extension | `unsigned` | 8–12 h |
| [5.4 Floating point](unit-5-type-system/5.4-floating-point.md) | IEEE 754, SSE `xmm` registers, float calling convention | `double` | 12–18 h |
| [5.5 Pointers](unit-5-type-system/5.5-pointers.md) | Addresses, lvalue conversion, load/store in IR | `&`, `*` | 10–14 h |
| [5.6 Arrays](unit-5-type-system/5.6-arrays.md) | Decay, scaled indexing, `lea` | Arrays, subscripts, initialisers | 10–14 h |
| [5.7 Characters & strings](unit-5-type-system/5.7-characters-and-strings.md) | Escapes, `.rodata` | `char`, string literals | 6–8 h |
| [5.8 Memory](unit-5-type-system/5.8-memory.md) | Incomplete types, the heap via libc | `void`, `sizeof`, `malloc` | 5–8 h |
| [5.9 Structs](unit-5-type-system/5.9-structs.md) | Layout, alignment, padding, ABI classification | Structs | 15–25 h |

## Unit 6: Optimisation (tests: ch. 19) (~29–42 h) · [unit-6-optimisation/](unit-6-optimisation/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [6.1 What optimisers do](unit-6-optimisation/6.1-what-optimisers-do.md) | `-O0` vs. `-O1`; running passes until nothing changes | Learning only | 2–3 h |
| [6.2 Constant folding](unit-6-optimisation/6.2-constant-folding.md) | Compile-time evaluation | Constant folding | 4–6 h |
| [6.3 Control-flow graphs](unit-6-optimisation/6.3-control-flow-graphs.md) | Basic blocks; arena/index graphs in Rust | CFG + unreachable-code elimination | 6–8 h |
| [6.4 Dataflow analysis](unit-6-optimisation/6.4-dataflow-analysis.md) | Lattices, meet, fixpoints, worklists | Dataflow framework | 6–10 h |
| [6.5 Copy propagation](unit-6-optimisation/6.5-copy-propagation.md) | Forward analysis (reaching copies) | Copy propagation | 6–8 h |
| [6.6 Dead stores](unit-6-optimisation/6.6-dead-stores.md) | Backward analysis (liveness) | Dead-store elimination | 5–7 h |

## Unit 7: Register Allocation (tests: ch. 20) (~28–41 h) · [unit-7-register-allocation/](unit-7-register-allocation/)
| Lesson | Learning goal | Builds | Time |
|---|---|---|---|
| [7.1 Why registers matter](unit-7-register-allocation/7.1-why-registers-matter.md) | Spills, register pressure | Learning only | 2–3 h |
| [7.2 Interference](unit-7-register-allocation/7.2-interference.md) | Interference graphs from liveness | Interference-graph builder | 6–8 h |
| [7.3 Graph colouring](unit-7-register-allocation/7.3-graph-colouring.md) | Chaitin–Briggs simplify/select, spilling, callee-saved registers | Register allocator | 12–18 h |
| [7.4 Coalescing](unit-7-register-allocation/7.4-coalescing.md) | Briggs/George conservative coalescing | Coalescing | 8–12 h |
