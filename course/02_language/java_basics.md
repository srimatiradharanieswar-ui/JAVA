# Module 2: Java Language Mastery - Basics

## Topic: Variables & Data Types

### Concept Explanation
Variables are named containers for data. Java is **Strongly Typed**, meaning every variable must have a declared type.

### Internal Working
- **Primitives**: Stored directly on the **Stack**. (int, double, boolean, etc.)
- **Reference Types**: The variable stores a memory address (on the Stack) that points to the actual object on the **Heap**.

### Data Types Table
| Type | Size | Range |
| :--- | :--- | :--- |
| byte | 8-bit | -128 to 127 |
| int | 32-bit | -2B to 2B |
| long | 64-bit | Very large |
| float | 32-bit | Decimal |
| double| 64-bit | Precise decimal |
| char | 16-bit | Unicode character |

### JVM Behavior: Type Promotion
In operations like `int + long`, Java automatically promotes the smaller type to the larger one to prevent overflow.

---

## Topic: Control Flow & Loops

### Concept Explanation
- **If/Else**: Decision making.
- **Switch**: Multi-way branch.
- **For/While/Do-While**: Iteration.

### Code Example: The Fibonacci Sequence
```java
public void printFibonacci(int count) {
    int n1 = 0, n2 = 1;
    for (int i = 0; i < count; i++) {
        System.out.print(n1 + " ");
        int sum = n1 + n2;
        n1 = n2;
        n2 = sum;
    }
}
```

---

## Topic: Strings & Arrays

### Concept Explanation
- **Arrays**: Fixed-size sequences of elements of the same type.
- **Strings**: Objects representing sequences of characters.

### Internal Working: String Pool
Strings in Java are **Immutable**. When you create a literal string (`String s = "Hello"`), the JVM puts it in the **String Constant Pool** in the Heap. If you create another string with the same value, it points to the same memory address.

### Code Example
```java
String s1 = "Java";
String s2 = "Java";
System.out.println(s1 == s2); // true (same reference)

int[] numbers = {1, 2, 3};
System.out.println(numbers.length); // 3
```

### Exercises
1. Write a program to find the largest number in an array.
2. Write a program to reverse a String without using `StringBuilder.reverse()`.
