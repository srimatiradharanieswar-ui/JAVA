# Module 1: Programming Foundations - CPU & Memory

## Topic: How Programming Works & CPU Execution

### Concept Explanation
Programming is the process of creating a set of instructions that tell a computer how to perform a task. At its core, it is about translating human logic into a format that electronic circuits can execute.

### Why It Exists
Computers are fundamentally "dumb" switching machines (billions of transistors). Programming provides the abstraction layer necessary to solve complex problems without manually toggling electrical signals.

### Internal Working: The Fetch-Decode-Execute Cycle
The CPU (Central Processing Unit) follows a relentless cycle:
1.  **Fetch**: Retrieve an instruction from memory (RAM) based on the Program Counter (PC).
2.  **Decode**: The Control Unit interprets what the instruction means (e.g., "Add two numbers").
3.  **Execute**: The Arithmetic Logic Unit (ALU) performs the operation.
4.  **Store**: The result is written back to a register or memory.

### Memory Behavior
Data moves from slow storage (SSD/HDD) to faster RAM, then into extremely fast CPU Caches (L1, L2, L3), and finally into Registers for immediate processing.

### JVM Behavior
The JVM abstracts this physical CPU. It uses a "Virtual" instruction set called Bytecode. The JVM's Execution Engine (JIT Compiler) eventually translates this Bytecode into the specific machine code of the underlying CPU (x86, ARM, etc.).

### Real World Use Cases
- **High-frequency trading**: Optimization at the CPU cache level to reduce latency.
- **Embedded systems**: Direct manipulation of registers to control hardware.

### Code Example (Conceptual Assembly vs Java)
**Java:**
```java
int a = 5 + 2;
```
**Conceptual Assembly:**
```assembly
MOV R1, 5    ; Load 5 into Register 1
ADD R1, 2    ; Add 2 to Register 1
STR R1, [mem]; Store result back to memory
```

### Best Practices
- Understand **Spatial and Temporal Locality**: Write code that accesses memory in predictable patterns to leverage CPU caching.

### Common Mistakes
- Thinking Java code runs directly on the CPU. It runs on the JVM, which then communicates with the CPU.

### Interview Questions
1. What is the Fetch-Decode-Execute cycle?
2. How does the CPU know which instruction to execute next? (Answer: Program Counter).

---

## Topic: Memory Basics (RAM, Stack, Heap)

### Concept Explanation
Memory is a linear array of bytes, each with a unique address. In programming, we divide it into different regions for efficiency and safety.

### Why It Exists
To manage the lifecycle of data. Some data is short-lived (function variables), while some persists (objects).

### Internal Working
- **RAM (Random Access Memory)**: Volatile storage. Fast access to any address.
- **Addressing**: 64-bit systems can address up to ^{64}$ bytes of memory.

### Memory Behavior: Stack vs Heap
- **Stack**: LIFO (Last-In-First-Out). Fast, managed by the CPU/OS automatically. Stores local variables and function calls.
- **Heap**: Large, unorganized pool. Slower, requires manual or garbage-collected management. Stores objects.

### JVM Behavior
Java heavily utilizes this. The JVM Stack holds local variables and "Frames" for each method call. The JVM Heap holds all objects created with the `new` keyword.

### Real World Use Cases
- **Memory Leaks**: Occur when objects in the Heap are no longer needed but still referenced, preventing the system from reclaiming memory.

### Code Example
```java
public void calculate() {
    int x = 10;          // Stored on the Stack
    User user = new User(); // 'user' reference on Stack, User object on Heap
}
```

### Exercises
1. Draw a diagram showing the state of the Stack and Heap after the execution of three nested method calls.
2. Calculate how many bytes are required to store an array of 1000 64-bit integers.
