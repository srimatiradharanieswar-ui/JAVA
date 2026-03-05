# Module 1: Programming Foundations - Compilers & Binary Representation

## Topic: Compilers vs Interpreters & The Pipeline

### Concept Explanation
The journey from Source Code to Machine Code involves a sophisticated multi-stage pipeline.

### Internal Working: The Compiler Pipeline
1.  **Lexical Analysis (Scanning)**: Converts a stream of characters into **Tokens** (e.g., `if`, `(`, `x`, `==`, `10`).
2.  **Syntax Analysis (Parsing)**: Checks tokens against language rules and builds an **Abstract Syntax Tree (AST)**.
3.  **Semantic Analysis**: Type checking and scope verification (e.g., "Is variable 'x' declared?").
4.  **Intermediate Code Generation**: Translates AST to a platform-independent IR (like JVM Bytecode or LLVM IR).
5.  **Optimization**: Rewriting code to be more efficient (e.g., Constant Folding: `5 + 2` -> `7`).
6.  **Code Generation**: Producing the final platform-specific machine code.

### JVM Behavior: De-optimization
The JVM JIT compiler can compile code based on assumptions. If those assumptions change (e.g., a new class is loaded that overrides a method), the JVM can **De-optimize** and revert to interpreted mode.

---

## Topic: Binary Representation & Floating Point (IEEE 754)

### Concept Explanation
Computers use Binary, but representing real numbers (fractions) is difficult.

### Internal Working: IEEE 754 Standard
A float is stored in 3 parts:
1.  **Sign Bit**: 0 for positive, 1 for negative.
2.  **Exponent**: Scaled to move the decimal point.
3.  **Mantissa (Significand)**: The actual digits of the number.

### Memory Behavior: Precision Loss
Some numbers, like `0.1`, cannot be represented exactly in binary (they become infinite repeating fractions). This is why `0.1 + 0.2 != 0.3` in Java.

### Best Practices
- Never use `float` or `double` for monetary calculations. Use **BigDecimal**.
- For bitwise flags, use powers of 2 (1, 2, 4, 8) and the bitwise AND/OR operators.

### Code Example: Bitwise Magic
```java
int READ = 1;  // 0001
int WRITE = 2; // 0010
int permissions = READ | WRITE; // 0011
boolean canRead = (permissions & READ) != 0; // true
```

### Exercises
1. Draw the Abstract Syntax Tree for the expression `result = (a + b) * 5`.
2. Convert the binary `1101.101` to decimal.
3. Why does Java have both `>>` (arithmetic shift) and `>>>` (logical shift)?
