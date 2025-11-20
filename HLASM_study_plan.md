# HLASM Study Plan

## Objectives
- Build foundational knowledge of IBM High Level Assembler (HLASM) syntax, instructions, and macros.
- Learn to work with z/OS development tools, assemble and link programs, and debug effectively.
- Practice reading and modernizing existing HLASM code bases with clean coding practices.

## Prerequisites and Setup (Week 0)
- Install a z/OS or MVS emulator (e.g., Hercules) or arrange access to a mainframe sandbox.
- Set up an assembler toolchain (HLASM on z/OS or open-source alternatives like ASMA90 for local practice).
- Become comfortable with 3270 terminal emulators and source-control workflows (Git).

## Week-by-Week Roadmap
### Week 1: Language Fundamentals
- Study assembler structure (CSECT, DSECT), storage classes, and standard assembler directives.
- Learn instruction formats, registers, base/displacement addressing, and literal pools.
- Exercises: write simple arithmetic and data-movement routines; practice base register setup.

### Week 2: Data Definition and Macros
- Explore DC/DS statements, alignment, and declarative constants.
- Create and invoke simple macros; understand conditional assembly and &SYSLIST processing.
- Exercises: write macros for parameter validation and reusable prolog/epilog code.

### Week 3: Control Flow and System Services
- Review branching, loops, and subroutine linkage conventions (save areas, BALR/BR R14, R15 usage).
- Learn SVC/PC instructions and common system services (GETMAIN/FREEMAIN, I/O basics).
- Exercises: implement subroutines with standard linkage; add basic error handling.

### Week 4: I/O and Data Conversion
- Study QSAM/VSAM file handling patterns and related control blocks.
- Practice data conversion (EBCDIC/ASCII), packed decimal, and binary arithmetic instructions.
- Exercises: read and write sequential files; convert and validate numeric fields.

### Week 5: Debugging and Testing
- Use interactive debuggers/trace facilities; set and interpret dumps and TRACE macros.
- Learn to read ABEND codes and IPCS basics; practice diagnosing storage overlays and loops.
- Exercises: create failing programs and step through fixes; write unit-style test drivers.

### Week 6: Performance and Modernization
- Study instruction costs, alignment, and cache considerations; apply optimization idioms.
- Introduce reentrancy, reusability, and LE-conformant callable modules.
- Explore modernization: documenting legacy routines, refactoring macros, and wrapping HLASM in higher-level interfaces.

## Ongoing Practice
- Contribute to open-source assembler samples; review others' code for patterns and anti-patterns.
- Maintain a personal cookbook of macros and reusable snippets.
- Schedule weekly code katas focusing on file I/O, data validation, and performance tuning.

## Recommended Resources
- IBM HLASM Language Reference and Programmer’s Guide.
- MVS/370, z/OS community tutorials, and CBT tape materials.
- Books or courses on z/Architecture Principles of Operation for deeper instruction semantics.

## Milestones and Assessment
- By Week 2: Write programs that perform arithmetic and string manipulation with correct register discipline.
- By Week 4: Successfully assemble and execute programs that read/write files and handle conversion edge cases.
- By Week 6: Refactor a small legacy module for reentrancy and document modernization opportunities.
- Ongoing: Pair with peers or mentors for periodic code reviews; track improvements in readability and defect rates.
