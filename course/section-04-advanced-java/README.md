# Section 4: Advanced Java

## Module 1: Collections Framework

### Deep Explanation
A unified architecture for representing and manipulating collections.
- **List:** Ordered (ArrayList, LinkedList).
- **Set:** Unique elements (HashSet, TreeSet).
- **Map:** Key-Value pairs (HashMap, TreeMap).

### Internal Working of HashMap
Uses an array of "buckets". It calculates the `hashCode()` of the key to find the index. If multiple keys map to the same index (Collision), it uses a LinkedList or Balanced Tree (since Java 8).

### Code Example
```java
Map<String, Integer> map = new HashMap<>();
map.put("Apple", 10);
```

---

## Module 2: Generics

### Deep Explanation
Allows types (classes and methods) to be parameters.
**Why it exists:** Type safety and eliminating the need for casting.

### JVM Behavior
**Type Erasure:** The compiler replaces all type parameters with their bounds or `Object`. The JVM doesn't know about generics at runtime.

### Code Example
```java
public class Box<T> {
    private T t;
    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```

---

## Module 3: Exception Handling

### Deep Explanation
Handling runtime errors to prevent application crashes.
- **Checked:** Compile-time (IOException).
- **Unchecked:** Runtime (NullPointerException).

### Best Practices
- Catch specific exceptions, not `Exception`.
- Use **Try-with-resources** for I/O.

---

## Module 4: Multithreading & Concurrency

### Deep Explanation
- **Process:** An executing program with its own memory.
- **Thread:** A lightweight sub-process.

### Memory Behavior
Each thread has its own **Stack**, but they share the same **Heap**. This leads to race conditions.

### Synchronization
Using `synchronized` keyword or `Lock` API to ensure only one thread accesses a resource at a time.

### Code Example
```java
Thread t1 = new Thread(() -> System.out.println("Running in thread"));
t1.start();
```

---

## Module 5: Streams API & Lambdas

### Deep Explanation
Functional-style programming in Java.
- **Lambdas:** Anonymous functions.
- **Streams:** A sequence of elements supporting sequential and parallel aggregate operations.

### Code Example
```java
List<String> names = Arrays.asList("Jack", "Jill", "John");
names.stream()
     .filter(n -> n.startsWith("J"))
     .forEach(System.out::println);
```

---

## Module 6: Reflection & Serialization

### Reflection
Examining or modifying the runtime behavior of applications. Used by frameworks like Spring or Retrofit.

### Serialization
Converting an object into a byte stream for storage or transmission.

### Interview Questions
- How does HashMap handle collisions?
- Difference between `Runnable` and `Callable`.
- What is the `volatile` keyword?
- What is Type Erasure?
