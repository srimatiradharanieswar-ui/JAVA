# Module 3: OOP Deep Dive - Object Internals & Dispatch

## Topic: Object Memory Layout (The Object Header)

### Concept Explanation
When you create an object, the JVM doesn't just store your fields. It adds metadata.

### Internal Working: The Header Structure
1.  **Mark Word (8 bytes on 64-bit)**:
    - **Hashcode**: Identity hashcode.
    - **GC Age**: Used by Generational GC.
    - **Lock State**: Bias lock, Lightweight lock, Heavyweight lock.
2.  **Klass Pointer (4 or 8 bytes)**: A reference to the Class metadata in the Metaspace.
3.  **Fields**: Your instance variables.
4.  **Padding**: Alignment to 8 bytes.

### JVM Behavior: Compressed Oops
On 64-bit JVMs with < 32GB RAM, the JVM uses **Compressed Ordinary Object Pointers (Oops)** to shrink 8-byte references to 4 bytes, saving massive amounts of Heap space.

---

## Topic: Dynamic Dispatch & The V-Table

### Concept Explanation
How does the JVM know which `makeSound()` to call when the variable is `Animal` but the object is `Dog`?

### Internal Working: Virtual Method Table (V-Table)
Every class has a V-Table in the Metaspace.
- **V-Table**: An array of pointers to the actual bytecode of methods.
- **Inheritance**: `Dog`'s V-Table copies `Animal`'s V-Table and replaces the entry for `makeSound()` with its own implementation.

### JVM Behavior: De-virtualization
Dispatching via V-Table is slow. The JIT compiler uses **Inlining Cache**.
- If a call site always calls the same class (`Monomorphic`), the JIT compiles it as a direct call (no lookup).
- If it calls 2 classes (`Bimorphic`), it uses a simple `if/else`.
- If many (`Megamorphic`), it reverts to slow V-Table lookup.

---

## Topic: The Finalizer & Phantom References

### Concept Explanation
The `finalize()` method is deprecated and dangerous.

### Internal Working
Objects with `finalize()` are placed in a special queue by the GC. A separate "Finalizer Thread" runs them, often too slowly, leading to `OutOfMemoryError` because the memory cannot be reclaimed until the finalizer finishes.

### Best Practices
- Use `try-with-resources` or `Cleaner` instead of `finalize()`.
- Use `private final` for fields to allow JIT to perform better optimizations.

### Exercises
1. Why is the Klass Pointer necessary in the object header?
2. Explain how Method Overloading (Static) differs from Overriding (Dynamic) at the JVM level.
