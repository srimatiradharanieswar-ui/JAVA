# Module 4: Advanced Java - Data & Errors

## Topic: Collections Framework
- **List**: `ArrayList`, `LinkedList`.
- **Set**: `HashSet`, `TreeSet`.
- **Map**: `HashMap`, `TreeMap`.

---

## Topic: Generics
**JVM Behavior: Type Erasure**: Java Generics are replaced with `Object` at compile-time to ensure backward compatibility.

---

## Topic: Exception Handling
- **Throwable**
    - **Error**: Fatal problems (`StackOverflowError`).
    - **Exception**
        - **Checked**: `IOException`.
        - **Unchecked**: `NullPointerException`.

### Code Example
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.err.println("Error!");
} finally {
    System.out.println("Done.");
}
```
