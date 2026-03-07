# Module 4: Advanced Java - Data & Errors

## Topic: Java Collections Deep Dive

### Deep Explanation
The Collections framework is a set of classes and interfaces that implement commonly used data structures. Understanding the underlying implementation (Array vs Linked List vs Hash Table) is key to performance.

### Code Example: HashMap Performance
```java
Map<String, Integer> map = new HashMap<>();
map.put("Key", 1); // O(1) average time
```

### Internal Working: HashMap Internals
A `HashMap` uses an array of "buckets".
1. **Hash Function**: `key.hashCode()` is shuffled to calculate a bucket index.
2. **Collision Handling**: If two keys land in the same bucket, they are stored in a LinkedList (or a Red-Black Tree in Java 8+ if the bucket is large).
3. **Load Factor**: When the map is 75% full, it resizes (doubles the array), which is an (n)$ operation.

### Real Use Case
**Caching**: HashMaps are the foundation of most in-memory caches. Choosing the right initial capacity can prevent expensive resizing operations in high-throughput systems.

### Exercise
1. Why must you override both `equals()` and `hashCode()` together?
2. Compare the time complexity of `ArrayList.get(i)` vs `LinkedList.get(i)`.

---

## Topic: Generics & Type Erasure

### Deep Explanation
Generics provide compile-time type safety. However, to maintain backward compatibility with older Java versions, the JVM uses "Type Erasure".

### Code Example: Type Erasure Proof
```java
List<String> strings = new ArrayList<>();
List<Integer> ints = new ArrayList<>();

// At runtime, both are just List!
System.out.println(strings.getClass() == ints.getClass()); // true
```

### Internal Working: Bridge Methods
Since the JVM erases types to `Object`, it sometimes generates "Bridge Methods" in the bytecode to ensure that polymorphism still works correctly with generic classes and interfaces.

### Real Use Case
**Retrofit/Gson**: These Android libraries use Reflection and "TypeTokens" to rediscover the generic type information that was erased, allowing them to map JSON directly to `List<User>`.

### Exercise
1. What is the difference between `List<Object>` and `List<?>`?
2. Explain "PECS" (Producer Extends, Consumer Super).

---

## Topic: Exception Architecture

### Deep Explanation
Exceptions are used to handle "exceptional" conditions. Java forces a distinction between Checked Exceptions (must be handled) and Unchecked Exceptions (programming errors).

### Internal Working: The Exception Table
Every method in the bytecode has an **Exception Table**. It maps ranges of bytecode offsets to handler code. When an exception is thrown, the JVM searches this table to find the appropriate `catch` block. This is why `try-catch` has zero overhead if no exception is thrown.

### Real Use Case
**Global Error Handling**: In Android, you can set an `UncaughtExceptionHandler` to catch any crash in your app, allowing you to log the error to a service like Firebase Crashlytics before the process dies.

### Exercise
1. Why is it considered bad practice to use exceptions for flow control?
2. What is "Try-with-resources" and how does it work under the hood?
