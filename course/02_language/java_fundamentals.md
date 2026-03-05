# Module 2: Java Language Mastery - Fundamentals & Bytecode

## Topic: The Java Class File Structure

### Concept Explanation
When you compile `MyFile.java`, you get `MyFile.class`. This is a binary file with a very specific, platform-independent format.

### Internal Working: Anatomy of a .class File
1.  **Magic Number**: `0xCAFEBABE` - identifies the file as a Java class.
2.  **Version**: Minor and Major version (e.g., 52 for Java 8, 61 for Java 17).
3.  **Constant Pool**: A heterogeneous table containing all literals (strings, integers) and symbolic references (class names, method names).
4.  **Access Flags**: `public`, `abstract`, `final`, etc.
5.  **Fields & Methods**: Descriptions and the actual **Bytecode**.
6.  **Attributes**: Source file name, Annotations, etc.

---

## Topic: JVM Bytecode Deep Dive

### Concept Explanation
Bytecode is the intermediate instruction set of the JVM. It is a "stack-based" architecture.

### Internal Working: Common Instructions
- **aload_0**: Load reference from local variable index 0 (usually `this`) onto the stack.
- **invokevirtual**: Dispatch a method call based on the runtime type of the object.
- **getstatic**: Fetch a static field from a class.
- **iadd**: Pop two integers, add them, push result back.

### Code Example: Bytecode Breakdown
**Java:**
```java
public int add(int a, int b) {
    return a + b;
}
```
**Equivalent Bytecode (`javap -c`):**
```bytecode
0: iload_1     // Load param 'a'
1: iload_2     // Load param 'b'
2: iadd        // Add them
3: ireturn     // Return int
```

### JVM Behavior: Verification
Before execution, the JVM performs a "Bytecode Verification" pass. It ensures the code doesn't:
- Over/underflow the stack.
- Access private members of other classes.
- Perform illegal casts.

### Real World Use Case: Bytecode Manipulation
Libraries like **ASM** or **ByteBuddy** can generate or modify `.class` files at runtime. This powers frameworks like **Spring** (AOP) and **Mockito** (Mocking).

### Exercises
1. Run `javap -c -v MyClass.class` on any class you've written and find the Constant Pool.
2. Explain why the JVM is called a "stack-based" machine vs a "register-based" machine (like Dalvik/ART).
