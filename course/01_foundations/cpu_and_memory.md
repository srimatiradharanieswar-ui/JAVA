# Module 1: Programming Foundations - CPU & Memory Deep Dive

## Topic: CPU Execution & Architecture Internals

### Concept Explanation
The CPU (Central Processing Unit) is the "brain" of the computer, but its internal operations are far more complex than a simple calculator. It utilizes advanced techniques to maximize throughput and minimize latency.

### Why It Exists
Raw transistor speed has physical limits (Heat, Light speed). Modern performance gains come from architectural optimizations like parallelism and prediction.

### Internal Working: Advanced CPU Techniques

#### 1. Pipelining
Imagine an assembly line. Instead of waiting for one instruction to finish all stages (Fetch, Decode, Execute, Store) before starting the next, the CPU starts Fetching instruction #2 while instruction #1 is being Decoded.
- **Problem**: **Pipeline Stalls** (Hazards). If instruction #2 depends on the result of instruction #1, the pipeline must pause.

#### 2. Branch Prediction
Modern CPUs try to guess which way an `if` statement will go.
- **Speculative Execution**: The CPU executes the guessed branch *before* the `if` condition is actually resolved.
- **Misprediction**: If the guess is wrong, the CPU must flush the pipeline and restart, causing a significant performance penalty.

#### 3. Superscalar Execution
The CPU has multiple execution units (ALUs). It can execute multiple *independent* instructions in the same clock cycle.

### Memory Behavior: The Cache Hierarchy

Memory speed has not kept up with CPU speed. This "Memory Wall" is solved by Caching:
- **L1 Cache**: Small (KB), extremely fast, integrated into the core.
- **L2 Cache**: Larger (MB), slightly slower, usually dedicated per core.
- **L3 Cache**: Largest (MBs), shared across all cores.

**Cache Lines**: Memory is not fetched byte-by-byte, but in "Lines" (usually 64 bytes).
**Best Practice**: Accessing memory sequentially (like in an Array) is much faster than jumping around (like in a Linked List) because it maximizes **Cache Hits**.

### Virtual Memory & Paging
Apps don't see physical RAM addresses. They see **Virtual Addresses**.
- **Page Table**: A map maintained by the OS/CPU (MMU) that translates virtual addresses to physical ones.
- **TLB (Translation Lookaside Buffer)**: A cache for these translations.

### JVM Behavior
The JVM's JIT compiler understands these CPU features. It can **Unroll Loops** to fill pipelines and **Inlining** methods to reduce the overhead of branch mispredictions.

### Real World Use Case
- **Spectre/Meltdown Vulnerabilities**: Exploited the way CPUs perform speculative execution and caching to leak private data.

### Interview Questions
1. What is a CPU cache miss and why is it expensive?
2. How does Branch Prediction affect the speed of processing sorted vs. unsorted arrays?

---

## Topic: Memory Management (Stack vs Heap Deep Dive)

### Internal Working
- **Stack**: Contiguous memory block. Managed by the `ESP` (Stack Pointer) register. Extremely fast (Increment/Decrement pointer).
- **Heap**: Fragmented pool. Managed by complex allocation algorithms (e.g., `malloc` or JVM TLABs).

### Memory Behavior
- **Stack Frames**: Every method call creates a Frame containing local variables, parameters, and the return address.
- **Heap Objects**: Objects exist until no reference points to them.

### JVM Behavior: TLAB (Thread Local Allocation Buffer)
To avoid locking the Heap for every new object, the JVM gives each thread a small private slice of the Heap (TLAB) for fast, lock-free allocations.

### Exercises
1. Calculate the L1 Cache Hit Ratio if out of 100 memory accesses, 95 are found in L1.
2. Simulate a Stack Overflow by writing a recursive function without a base case.
