# Module 2: Java Language Mastery - Basics & Memory Layout

## Topic: Primitive vs. Wrapper Types (Memory Overhead)

### Concept Explanation
Java provides 8 primitives (`int`, `long`, etc.) and corresponding Wrapper classes (`Integer`, `Long`).

### Internal Working: Memory Layout
- **int (Primitive)**: Always 32-bits (4 bytes). Stored directly on the stack or as part of an object on the heap.
- **Integer (Wrapper)**: An Object on the heap.
    - **Header**: 12 bytes (Mark Word + Klass Pointer).
    - **Data**: 4 bytes (The actual int).
    - **Padding**: 0-4 bytes to align to 8-byte boundaries.
    - **Total**: Usually **16 or 24 bytes** for a single integer!

### Why It Exists: Autoboxing
The automatic conversion between primitives and wrappers. Convenient but can cause performance bottlenecks if done in a loop (creating millions of garbage objects).

---

## Topic: Array Memory Layout & Bounds Checking

### Concept Explanation
An array in Java is an **Object**.

### Internal Working: Heap Layout
1.  **Object Header**: 12 bytes.
2.  **Array Length**: 4 bytes.
3.  **Data**: Elements of the array.
4.  **Padding**: Alignment.

### JVM Behavior: Bounds Checking
For every array access (`arr[i]`), the JVM performs a range check at runtime.
- **Optimization**: The JIT compiler can "Hoist" these checks out of loops if it can prove `i` is always safe, reducing overhead.

### Code Example: Memory Usage Calculation
An `int[1000]` array:
- Header + Length: 16 bytes.
- Data: 000 \times 4 = 4000$ bytes.
- Total: ~4016 bytes.

An `Integer[1000]` array:
- Array of References: 000 \times 4$ (or 8) bytes = 4000 bytes.
- Plus 1000 Integer Objects on the heap: 000 \times 16 = 16000$ bytes.
- **Total: ~20,000 bytes!** (5x more than primitive array).

---

## Topic: Strings - The Pool & Internal Representation

### Internal Working: Compact Strings (Java 9+)
Previously, Java used `char[]` (2 bytes per char) for Strings. Now, if a string only contains Latin-1 characters, it uses `byte[]` (1 byte per char) to save 50% memory.

### Best Practices
- Use `ArrayList<Integer>` only when necessary; use primitive arrays or libraries like FastUtil for performance-critical data.
- Avoid String concatenation in loops; use `StringBuilder`.

### Exercises
1. Calculate the memory footprint of a `String` object containing the text "Hello".
2. Explain the "Integer Cache" (Integer.valueOf) and how it affects memory.
