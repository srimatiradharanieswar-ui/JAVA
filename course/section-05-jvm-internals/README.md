# Section 5: Java Internals & JVM

## Module 1: JVM Architecture

### Deep Explanation
The JVM is divided into three main subsystems:
1. **Class Loader Subsystem:** Loads, links, and initializes class files.
2. **Runtime Data Areas:** Memory allocated during execution.
3. **Execution Engine:** Executes the bytecode.

### Internal Working
- **Class Loader:** Uses Delegation Hierarchy (Bootstrap -> Extension -> Application).
- **Execution Engine:** Contains the Interpreter, JIT Compiler, and Garbage Collector.

---

## Module 2: Java Memory Model (Stack vs Heap)

### 1. The Stack
- **What:** Stores local variables and method call frames.
- **Behavior:** LIFO (Last In, First Out). Each thread has its own stack.
- **Lifecycle:** Memory is reclaimed automatically when the method returns.

### 2. The Heap
- **What:** Stores all objects and arrays.
- **Behavior:** Shared across all threads.
- **Lifecycle:** Managed by the Garbage Collector.

### 3. Metaspace
- Stores class metadata (Static variables, method data). Replaced the PermGen space in Java 8.

---

## Module 3: Garbage Collection (GC)

### Deep Explanation
GC is the process of reclaiming heap memory by destroying unreachable objects.

### How it Works
1. **Marking:** Identify which objects are in use.
2. **Deletion/Compacting:** Remove unused objects and move remaining objects together to reduce fragmentation.

### Generational Hypothesis
Most objects die young. Memory is divided into:
- **Young Generation:** Eden Space, Survivor Spaces (S0, S1).
- **Old (Tenured) Generation:** For long-lived objects.

### GC Algorithms
- **Serial GC:** Single-threaded.
- **Parallel GC:** Multi-threaded for Young Gen.
- **G1 (Garbage First):** Designed for large heaps with low latency.

---

## Module 4: Bytecode Execution

### Deep Explanation
Bytecode is the instruction set for the JVM.
- `aload_0`: Load 'this' onto stack.
- `invokevirtual`: Invoke instance method.

### Real World Use Case
Understanding bytecode helps in profiling, security analysis, and building tools like Lombok or MapStruct.

### Interview Questions
- Explain the difference between Stack and Heap.
- How does the Garbage Collector know which objects to delete?
- What are the different types of Class Loaders?
- What is the Stop-The-World event in GC?

### Exercise
1. Use `javap -c MyClass` to inspect the bytecode of a simple Java class.
2. Run a Java program with `-verbose:gc` and analyze the output.
