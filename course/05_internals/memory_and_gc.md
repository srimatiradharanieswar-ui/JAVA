# Module 5: Java Internals - GC & JIT Deep Dive

## Topic: Garbage Collection (G1 & ZGC Internals)

### Deep Explanation
Garbage Collection (GC) is the automated process of reclaiming heap memory by destroying objects that are no longer reachable. Modern GCs focus on minimizing "Stop-The-World" (STW) pauses.

### Code Example: Forcing GC (Not Recommended)
```java
System.gc(); // Hint to the JVM, not a command.
// Instead, use -Xlog:gc to monitor behavior
```

### Internal Working: Modern Algorithms
1. **G1 GC (Garbage First)**: Splits the heap into regions. It prioritizes regions with the most garbage ("Garbage First"). It uses **SATB** to track live objects concurrently.
2. **ZGC (Zero GC)**: Designed for sub-millisecond pauses. It uses **Colored Pointers** and **Load Barriers**. When a thread reads an object reference, the load barrier checks if the object needs moving and helps the GC do its work.

### Real Use Case
**Large-Scale Microservices**: Systems with 100GB+ heaps use ZGC to ensure that GC pauses don't cause latency spikes in API response times, which could trigger timeouts in a distributed system.

### Exercise
1. What is the difference between a "Minor GC" and a "Full GC"?
2. Explain how "Generational Hypothesis" (most objects die young) influences GC design.

---

## Topic: JIT Compilation (C1, C2, and Graal)

### Deep Explanation
The JIT (Just-In-Time) compiler translates bytecode to native machine code at runtime. It focuses on "hot code" (methods called frequently or loops with many iterations).

### Code Example: Performance Warmup
```java
// The first 10,000 iterations are interpreted.
// Then C1 compiles it.
// After 100,000, C2 performs aggressive optimization.
for (int i = 0; i < 1000000; i++) {
    compute();
}
```

### Internal Working: Tiered Compilation
1. **Level 0-3 (C1)**: Fast compilation with basic optimizations.
2. **Level 4 (C2)**: Slow, aggressive optimization. It uses **Escape Analysis** to decide if an object can be allocated on the stack (Scalar Replacement) and **Inlining** to replace method calls with the actual code.

### Real Use Case
**Serverless Functions**: In AWS Lambda, the "Cold Start" problem is partly caused by the JVM needing time to JIT-compile the code. Developers use "GraalVM Native Image" to AOT (Ahead-of-Time) compile Java into a native binary for instant startup.

### Exercise
1. Explain how "Escape Analysis" can eliminate locking (Lock Elision).
2. What is "De-optimization" and when does the JVM perform it?
