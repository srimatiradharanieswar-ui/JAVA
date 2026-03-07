# Module 2: Java Language Mastery - Fundamentals & Bytecode

## Topic: The Java Class File Structure

### Deep Explanation
When you compile `MyFile.java`, you get `MyFile.class`. This is a binary file with a platform-independent format that the JVM understands. It contains the "blueprint" of your class.

### Code Example: Magic Number Check
```bash
# Use hexdump to see the magic number of a class file
hexdump -n 4 -C MyClass.class
# Output: 00000000  ca fe ba be
```

### Internal Working: Anatomy of a .class File
1. **Magic Number**: `0xCAFEBABE` - identifies the file as a Java class.
2. **Version**: Minor and Major version (e.g., 61 for Java 17).
3. **Constant Pool**: A table containing all literals and symbolic references.
4. **Access Flags**: `public`, `abstract`, `final`, etc.
5. **Fields & Methods**: Descriptions and the actual **Bytecode**.

### Real Use Case
**Dynamic Class Loading**: Frameworks like OSGi or plugin systems use the class file structure to load and link code at runtime, allowing for hot-swapping of modules without restarting the application.

### Exercise
1. Run `javap -c -v MyClass.class` on any class and identify the Constant Pool.
2. What happens if you change the magic number of a `.class` file manually?

---

## Topic: JVM Bytecode Deep Dive

### Deep Explanation
Bytecode is the intermediate instruction set of the JVM. Unlike x86 which is register-based, the JVM is a "stack-based" architecture, meaning instructions perform operations on an internal operand stack.

### Code Example: Bytecode Breakdown
**Java Source:**
```java
public int add(int a, int b) {
    return a + b;
}
```
**Equivalent Bytecode (`javap -c`):**
```bytecode
0: iload_1     // Load param 'a' onto stack
1: iload_2     // Load param 'b' onto stack
2: iadd        // Pop both, add them, push result
3: ireturn     // Return result from stack
```

### Internal Working: Common Instructions
- **aload_0**: Load reference from local variable index 0 (usually `this`).
- **invokevirtual**: Dispatch a method call based on runtime type.
- **getstatic**: Fetch a static field from a class.

### Real Use Case
**Bytecode Manipulation**: Libraries like **ByteBuddy** or **ASM** modify bytecode at runtime to implement cross-cutting concerns like logging or transaction management in Spring AOP.

### Exercise
1. Explain why the JVM is called a "stack-based" machine vs a "register-based" machine (like Dalvik/ART).
2. Look up the bytecode instruction for creating a new object (`new`).
