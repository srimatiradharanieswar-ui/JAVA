# Module 5: Java Internals - GC & JIT Deep Dive

## Topic: Garbage Collection (G1 & ZGC Internals)

### Concept Explanation
The JVM uses complex algorithms to manage memory without "Stopping the World" for too long.

### 1. G1 GC (Garbage First)
**Internal Working**:
- The Heap is split into ~2048 **Regions**.
- **SATB (Snapshot-At-The-Beginning)**: Used to track live objects during concurrent marking.
- **Copying**: G1 identifies the regions with the most "garbage" and copies the survivors into new regions, compacting memory.

### 2. ZGC (Zero Garbage Collector)
**Concept**: A scalable, low-latency GC designed for multi-terabyte heaps.
**Internal Working: Colored Pointers**:
- ZGC uses 64-bit pointers where some bits represent the "Color" (state) of the object (e.g., `marked`, `remapped`).
- **Load Barriers**: When a thread reads a pointer, it checks the color. If it's incorrect, the thread helps fix the pointer before using it. This allows ZGC to perform almost all work concurrently.

---

## Topic: JIT Compilation (C1, C2, and Graal)

### Concept Explanation
The JIT (Just-In-Time) compiler translates bytecode to native code during execution.

### Internal Working: Tiered Compilation
1.  **Level 0**: Interpreted code.
2.  **Level 1-3 (C1 Compiler)**: Quick compilation with simple optimizations.
3.  **Level 4 (C2 Compiler)**: High-performance compilation with aggressive optimizations (Inlining, Escape Analysis).

### Aggressive Optimizations
- **Escape Analysis**: If an object doesn't "escape" a method, the JVM can allocate it on the **Stack** instead of the Heap (Scalar Replacement).
- **Intrinsics**: Replacing standard Java code with hand-optimized assembly instructions for the specific CPU.

---

## Topic: Safe Points

### Concept Explanation
The JVM cannot stop a thread at any random instruction (it might be in the middle of updating a pointer).

### Internal Working
**Safe Points** are specific locations in the code where the JVM can safely pause a thread for GC or de-optimization. The JVM puts "Safe Point Polling" instructions in loops and method exits.

### Best Practices
- Monitor GC logs using `-Xlog:gc*`.
- Use `jhsdb jmap --heap` to analyze heap regions.

### Exercises
1. Difference between a "Minor GC" and a "Full GC"?
2. Explain how "Escape Analysis" can eliminate locking (Lock Elision).
