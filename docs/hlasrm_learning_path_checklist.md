# HLASM Learning Path Checklist

Use this checklist to track progress through the learning path described in `docs/hlasrm_learning_path.md`. The steps follow the suggested timeline and highlight outcomes to verify along the way.

## Week 1: Minimal Foundations (Days 1–2)
- [ ] Review program structure (`CSECT`, `ENTRY`, `END`, `USING`, `DROP`).
- [ ] Map register roles (R0–R15) with emphasis on R1, R13, R14, and R15.
- [ ] Practice basic control flow (`B*`, `BAL`, `BALR`, `BR`) and return conventions.
- [ ] Define data with `DC` and `DS`; practice base + displacement addressing.
- [ ] Outcome: able to read simple routines and explain register usage aloud.

## Week 1–2: Core Idioms (Days 3–5)
- [ ] Memorize standard register usage patterns (R15 return code, R14 return address, R13 save-area pointer, R1 parameter list, R12 base register).
- [ ] Write and rehearse the save-area prologue/epilogue sequence until it is fluent.
- [ ] Identify and annotate base-register setup and teardown in sample code.
- [ ] Outcome: can follow 70% of business logic without pausing on boilerplate.

## Week 2: Data Layout Patterns (Days 4–5)
- [ ] Catalog `DC` formats (`AL1`, `AL2`, `F`, `H`, `X`, `P`) and when to use each.
- [ ] Convert packed decimals (`PACK`, `UNPK`) into modern equivalents (`BigDecimal` or scaled integers).
- [ ] Practice bit manipulation instructions (`AND`, `OR`, `TM`, `OI`, `NI`).
- [ ] Trace pointer arithmetic with `LA`, `L`, and `ST` on table data.
- [ ] Outcome: comfortable mapping assembler data definitions to Java types.

## Week 2–3: Control-Flow Shapes (Week 2 focus)
- [ ] Translate compare-and-branch pairs (`C` / `CLC` with `BE`, `BNE`, etc.) into structured flow.
- [ ] Rewrite loop patterns that end with unconditional branches as structured loops.
- [ ] Step through table lookups using base register + displacement addressing.
- [ ] Follow subroutine linkage via `CALL` macros or `BAL/BALR` with parameter lists in R1.
- [ ] Outcome: able to navigate full programs and predict flow from labels and branches.

## Week 3: Common Macros and Runtime Conventions
- [ ] Recognize macro intent for program control (`CALL`, `PUSH`, `POP`).
- [ ] Practice movement macros (`MVC`, `MVCL`, `MVCLE`) and their typical use cases.
- [ ] Note I/O macro sequences (`GET`/`PUT`, `READ`/`WRITE`) for QSAM/VSAM.
- [ ] Observe storage management (`STORAGE OBTAIN/FREE`) and numeric editing (`ED`, `EDMK`).
- [ ] Map return codes, LE parameter list formats, and dynamic storage blocks to Java error handling and context objects.
- [ ] Outcome: can relate macros and runtime conventions to higher-level constructs.

## Week 3–4: Practice with Real Code
- [ ] Annotate parameter list parsing and validation routines.
- [ ] Trace table processing and search loops in existing programs.
- [ ] Walk through DB2/IMS call sequences and note register/prolog usage.
- [ ] Review file access macros for QSAM/VSAM and document control block usage.
- [ ] Deconstruct numeric packing/unpacking routines and record Java equivalents.
- [ ] Outcome: ready to modernize routines by pattern rather than line-by-line translation.

## Week 4: Map HLASM to Java
- [ ] Build a personal cheat sheet mapping assembler constructs to Java patterns (control flow, data types, comparisons, pointers/offsets, save areas, registers).
- [ ] Refactor one small routine into structured Java, keeping naming aligned with register intent.
- [ ] Validate that packed decimal and byte comparison logic behaves identically in Java tests.
- [ ] Outcome: produce modernization-ready Java stubs from assembler routines.

## Tools and Next Steps (Ongoing)
- [ ] Experiment with Hercules or similar emulators to run and observe snippets.
- [ ] Prototype parsing or conversion pipelines with tools like ProLeap or z390.
- [ ] Build a glossary of the top 40 idioms encountered in the codebase.
- [ ] Draft an intermediate representation capturing control flow, data flow, and linkage metadata.
- [ ] Collect and store annotated examples of parameter handling, table search, and file I/O routines for quick reference.
- [ ] Outcome: maintain reusable assets and pipelines that accelerate modernization.
