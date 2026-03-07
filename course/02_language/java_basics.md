# Module 2: Java Language Mastery - Basics & Memory Layout

## Topic: Primitive vs. Wrapper Types

### Deep Explanation
Java distinguishes between primitive types (like `int`) and their object-oriented wrappers (like `Integer`). While primitives are lightweight, wrappers allow primitives to be used in Collections and Generics.

### Code Example: Performance Pitfall (Autoboxing)
```java
long start = System.currentTimeMillis();
Long sum = 0L; // Wrapper!
for (long i = 0; i <= Integer.MAX_VALUE; i++) {
    sum += i; // 2 billion unnecessary Long objects created here!
}
System.out.println(System.currentTimeMillis() - start);
```

### Internal Working: Memory Layout
- **int (Primitive)**: 4 bytes of raw data.
- **Integer (Wrapper)**: 16-24 bytes. Contains a 12-byte header (Mark Word + Klass Pointer), the 4-byte int value, and padding for 8-byte alignment.

### Real Use Case
**Android Memory Optimization**: In Android, memory is scarce. Using `SparseArray<String>` instead of `HashMap<Integer, String>` avoids the overhead of `Integer` objects by using primitive arrays for keys.

### Exercise
1. Calculate the memory footprint of an `ArrayList<Integer>` with 1,000 elements vs an `int[1000]`.
2. Research the "Integer Cache" (`Integer.valueOf`) and how it affects memory and equality checks.

---

## Topic: Strings - The Pool & Internal Representation

### Deep Explanation
Strings in Java are immutable and stored in a special area of the heap called the **String Constant Pool**. This allows multiple variables to point to the same string literal, saving memory.

### Code Example: String Interning
```java
String s1 = "Hello";
String s2 = "Hello";
String s3 = new String("Hello");

System.out.println(s1 == s2);      // true (same reference in pool)
System.out.println(s1 == s3);      // false (s3 is a new heap object)
System.out.println(s1 == s3.intern()); // true (intern() returns pool ref)
```

### Internal Working: Compact Strings (Java 9+)
Previously, Strings used `char[]` (2 bytes per char). Modern JVMs use `byte[]` plus an encoding flag. If the string contains only Latin-1 characters, it uses 1 byte per char, cutting memory usage in half for most applications.

### Real Use Case
**Large Scale Web Apps**: By interning frequently occurring strings (like Country Names or Status Codes), large-scale applications can reduce their heap footprint significantly.

### Exercise
1. Why is it a bad idea to use `String += "more text"` in a large loop?
2. What is the difference between `StringBuilder` and `StringBuffer`?
