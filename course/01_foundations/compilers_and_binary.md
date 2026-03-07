# Module 1: Programming Foundations - Compilers & Binary Representation

## Topic: Compilers vs Interpreters & The Pipeline

### Deep Explanation
The journey from Source Code to Machine Code involves a sophisticated multi-stage pipeline. A compiler translates the entire source code into machine code before execution, while an interpreter translates and executes it line-by-line. Java uses a hybrid approach (JIT).

### Code Example: Constant Folding Optimization
```java
// Original Code
int x = 60 * 60 * 24;

// After Compiler Optimization (Constant Folding)
int x = 86400;
```

### Internal Working: The Compiler Pipeline
1. **Lexical Analysis**: Converts characters into Tokens.
2. **Syntax Analysis**: Builds an Abstract Syntax Tree (AST).
3. **Semantic Analysis**: Performs type checking.
4. **Intermediate Code Generation**: Produces IR (like Bytecode).
5. **Optimization**: Rewrites code for efficiency.
6. **Code Generation**: Produces machine code.

### Real Use Case
**ProGuard/R8**: These tools act as "Optimizing Compilers" for Android, performing shrinking, optimization, and obfuscation by analyzing the AST and removing unused code paths.

### Exercise
1. Draw the Abstract Syntax Tree for the expression `result = (a + b) * 5`.
2. Research the difference between "AOT" (Ahead-of-Time) and "JIT" (Just-in-Time) compilation.

---

## Topic: Binary Representation & Floating Point (IEEE 754)

### Deep Explanation
Computers use Binary (base-2), but representing real numbers (fractions) is difficult due to the finite number of bits. The IEEE 754 standard defines how these are stored using a sign bit, exponent, and mantissa.

### Code Example: Floating Point Precision Issue
```java
public class PrecisionDemo {
    public static void main(String[] args) {
        double a = 0.1;
        double b = 0.2;
        System.out.println(a + b); // Prints 0.30000000000000004
        System.out.println(a + b == 0.3); // Prints false
    }
}
```

### Internal Working: IEEE 754 Standard
- **Sign Bit**: 0 for positive, 1 for negative.
- **Exponent**: Scaled value to move the decimal (binary) point.
- **Mantissa**: The fractional part of the number in scientific notation.
- **Precision Loss**: Since 0.1 has no finite binary representation, it is approximated, leading to rounding errors.

### Real Use Case
**Banking Systems**: In financial software, using `double` for currency leads to catastrophic rounding errors over millions of transactions. Developers must use `BigDecimal` or store amounts in cents as `long`.

### Exercise
1. Convert the binary `1101.101` to decimal.
2. Why does Java have both `>>` (arithmetic shift) and `>>>` (logical shift)?
