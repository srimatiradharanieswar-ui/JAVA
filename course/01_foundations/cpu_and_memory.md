# Module 1: Programming Foundations - CPU & Memory Deep Dive

## Topic: CPU Execution & Architecture Internals

### Deep Explanation
The CPU (Central Processing Unit) is the "brain" of the computer, but its internal operations are far more complex than a simple calculator. Modern performance gains come from architectural optimizations like parallelism and prediction rather than raw transistor speed.

### Code Example: Branch Prediction Impact
```java
import java.util.Arrays;
import java.util.Random;

public class BranchPrediction {
    public static void main(String[] args) {
        int size = 32768;
        int[] data = new int[size];
        Random rnd = new Random(0);
        for (int c = 0; c < size; ++c) data[c] = rnd.nextInt() % 256;

        // With sorting, the "if" branch is predictable, leading to 3x speedup
        Arrays.sort(data);

        long start = System.nanoTime();
        long sum = 0;
        for (int i = 0; i < 100000; ++i) {
            for (int c = 0; c < size; ++c) {
                if (data[c] >= 128) sum += data[c];
            }
        }
        System.out.println((System.nanoTime() - start) / 1000000000.0);
    }
}
```

### Internal Working: Advanced CPU Techniques
1. **Pipelining**: Assembly line processing of instructions (Fetch, Decode, Execute, Store).
2. **Branch Prediction**: Speculative execution of code paths based on history.
3. **Superscalar Execution**: Multiple execution units (ALUs) working in parallel.

### Real Use Case
**Spectre/Meltdown Vulnerabilities**: These security flaws exploited the way CPUs perform speculative execution and caching to leak private data across process boundaries.

### Exercise
1. Explain how sorting the array in the code example above affects the CPU's branch predictor.
2. What is the difference between a pipeline stall and a cache miss?

---

## Topic: Memory Management (Stack vs Heap Deep Dive)

### Deep Explanation
Memory management is the process of allocating and deallocating memory during program execution. It is divided into two main areas: the Stack for short-lived, local data, and the Heap for long-lived, shared objects.

### Code Example: Stack vs Heap
```java
public class MemoryAllocation {
    public void method() {
        int x = 10; // Stored on Stack
        Object obj = new Object(); // Ref on Stack, Instance on Heap
    }
}
```

### Internal Working
- **Stack**: Managed by the CPU Stack Pointer. Contiguous and extremely fast. Every method call creates a "Stack Frame".
- **Heap**: A large pool of memory managed by the JVM. Objects are allocated here and managed by Garbage Collection.
- **Cache Hierarchy (L1, L2, L3)**: Small, fast memory layers that store frequently accessed data to bridge the "Memory Wall" between CPU and RAM.

### Real Use Case
**High-Frequency Trading (HFT)**: HFT systems are optimized for "Cache Locality" using primitive arrays instead of object lists to ensure the CPU rarely has to fetch data from the slow main RAM.

### Exercise
1. Simulate a StackOverflowError using recursion and explain why it occurs.
2. Why is accessing an array sequentially faster than traversing a linked list in terms of CPU cache?
