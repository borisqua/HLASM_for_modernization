# HLASM Learning Path for Modernization Engineers

This guide distills practical steps for quickly reading, reasoning about, and mapping High-Level Assembler (HLASM) programs into modern languages such as Java. It assumes familiarity with enterprise languages (COBOL, Java) and focuses on pattern recognition for reverse engineering.

## 1. Minimal Foundations (1–2 days)

Gain just enough syntax and runtime knowledge to read common routines:

- Program structure: `CSECT`, `ENTRY`, `END`, `USING`, `DROP`.
- Register roles: R0–R15 (with emphasis on R1, R13, R14, R15).
- Control flow: branch (`B*`), linkage (`BAL`, `BALR`, `BR`), and return conventions.
- Data definition: `DC`, `DS`, and base + displacement addressing.

## 2. Core Idioms to Memorize (2–3 days)

HLASM programs rely on recognizable templates. Knowing them lets you skim boilerplate and focus on business logic.

### Standard register usage

- R15: program return code.
- R14: return address.
- R13: save-area pointer.
- R1: parameter list pointer.
- R12: common base register for addressing.

### Save-area prologue/epilogue

```asm
STM   R14,R12,12(R13)    ; save caller registers
LR    R12,R15            ; establish base
ST    R13,4(R15)         ; forward chain
ST    R15,8(R13)         ; backward chain
LA    R13,SAVEAREA       ; new save area
...
L     R13,8(R13)         ; restore caller save area
LM    R14,R12,12(R13)    ; restore registers
BR    R14                ; return
```

## 3. Data Layout Patterns (2–3 days)

Understand how HLASM data maps to modern types:

- `DC` formats: `AL1`, `AL2`, `F`, `H`, `X`, `P`.
- Packed decimal (`PACK`, `UNPK`) → `BigDecimal` or scaled integers.
- Bit manipulation: `AND`, `OR`, `TM`, `OI`, `NI`.
- Pointers: `LA`, `L`, `ST` used for offset arithmetic and table access.

## 4. Control-Flow Shapes (3–5 days)

Scan for predictable flow structures:

- Compare then branch: `C` / `CLC` paired with `BE`, `BNE`, etc.
- Loops: labeled blocks ending with an unconditional branch to the label.
- Table lookup: base register + displacement, often in `CLC` sequences.
- Subroutine linkage: `CALL` macros, `BAL/BALR` with R14/R15, parameter lists in R1.

## 5. Common Macros to Recognize (3–5 days)

Macro intent matters more than expansion details:

- Program control: `CALL`, `PUSH`/`POP`.
- Movement: `MVC`, `MVCL`, `MVCLE`.
- I/O: `GET`/`PUT` (QSAM/VSAM), `READ`/`WRITE`.
- Storage: `STORAGE OBTAIN/FREE`.
- Numeric editing: `ED`, `EDMK`.

## 6. MVS/LE Runtime Conventions (2–3 days)

Keep a high-level view to map assembler behavior to Java:

- Return codes and condition handling.
- Language Environment (LE) parameter list formats.
- Dynamic storage blocks and task state blocks.
- Common control blocks: PSW, TCB, ASCB.

## 7. Practice with Real Code (1 week)

Build pattern recognition by annotating real programs:

- Parameter list parsing and validation.
- Table processing and search loops.
- DB2/IMS call sequences.
- File access macros for QSAM/VSAM.
- Numeric unpacking/packing routines.

## 8. Map HLASM to Java (2–3 days)

Create a personal cheat sheet linking assembler constructs to modern equivalents:

- Control flow → structured Java methods.
- Packed decimals → `BigDecimal` or `long` with scaling.
- `CLC` byte comparisons → string/byte array comparisons.
- Pointers and offsets → object references with explicit field access.
- Save areas → call stack frames or context objects.
- Registers → clearly named Java variables.

## 9. Optional but Useful Tools

- Hercules or other emulators to test snippets.
- Grammar/parsing tools (e.g., ProLeap, z390) to experiment with conversion pipelines.

## Suggested Timeline

| Block       | Focus                                 | Outcome                               |
|-------------|---------------------------------------|---------------------------------------|
| Days 1–2    | Syntax, registers, base addressing     | Can read simple routines              |
| Days 3–5    | Idioms and data layout patterns        | Can follow 70% of business logic      |
| Week 2      | Control flow and macro recognition     | Can navigate full programs            |
| Week 3      | Practice and HLASM→Java mapping        | Ready for modernization automation    |

## Next Steps

To deepen expertise:

- Build a glossary of the 40 most common idioms you encounter.
- Draft an intermediate representation (IR) schema capturing control flow, data flow, and linkage metadata.
- Collect annotated examples of typical routines (parameter handling, table search, file I/O) for quick reference.
