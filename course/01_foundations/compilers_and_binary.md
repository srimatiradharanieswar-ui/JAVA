# Module 1: Programming Foundations - Compilers & Binary

## Topic: Compilers vs Interpreters

### Concept Explanation
Programs written in high-level languages (Java, C++, Python) must be converted into Machine Code (1s and 0s) to run.
- **Compiler**: Translates the entire source code into machine code at once (e.g., C++).
- **Interpreter**: Translates and executes the code line-by-line (e.g., Python).

### Why It Exists
- **Compilers**: High performance. The translation happens once, resulting in an executable file.
- **Interpreters**: Flexibility and easier debugging. Platform independence.

### Internal Working
- **Compiler Pipeline**: Lexical Analysis -> Syntax Analysis -> Semantic Analysis -> IR Generation -> Optimization -> Code Generation.
- **Interpreter Pipeline**: Reads a line, parses it, executes it immediately via a VM or host environment.

### JVM Behavior: The Hybrid Approach
Java is unique. It is **compiled** into Bytecode (`.class` files). This bytecode is then **interpreted** by the JVM. To improve speed, the JVM uses a **JIT (Just-In-Time) Compiler** to compile frequently used bytecode into native machine code at runtime.

### Real World Use Cases
- **Java**: Used for cross-platform enterprise apps because of the "Compile Once, Run Anywhere" (WORA) philosophy.
- **C++**: Used for game engines where every millisecond of performance counts.

### Code Example (Conceptual)
**Java (Hybrid):**
```bash
javac MyFile.java   # Compiles to Bytecode (MyFile.class)
java MyFile         # JVM interprets/JIT-compiles Bytecode
```

### Common Mistakes
- Thinking Java is "slow" because it's interpreted. Modern JIT compilers make Java nearly as fast as C++ for many tasks.

---

## Topic: Binary & Data Representation

### Concept Explanation
Computers represent all data (numbers, text, images, sound) as a sequence of bits (Binary Digits: 0 and 1).

### Why It Exists
Electronic circuits are most stable when representing two states: ON (1) or OFF (0). High/Low voltage.

### Internal Working
- **Bits & Bytes**: 8 bits = 1 Byte.
- **Number Systems**:
    - **Binary (Base 2)**: 0, 1.
    - **Decimal (Base 10)**: 0-9.
    - **Hexadecimal (Base 16)**: 0-9, A-F (Used for memory addresses).

### Memory Behavior
Integers are stored using **Two's Complement** for signed numbers. Floating points use the **IEEE 754** standard.

### JVM Behavior
Java defines strict sizes for primitive types (e.g., `int` is always 32-bit signed) regardless of the underlying OS. This ensures portability.

### Code Example
```java
int binaryValue = 0b1010; // Binary for 10
int hexValue = 0x0A;      // Hex for 10
System.out.println(binaryValue == hexValue); // true
```

### Exercises
1. Convert the decimal number 25 into Binary and Hexadecimal.
2. What is the maximum value that can be stored in an 8-bit unsigned integer? (Answer: 255).
3. Explain why `0.1 + 0.2 != 0.3` in many programming languages. (Hint: IEEE 754 Floating Point precision).
