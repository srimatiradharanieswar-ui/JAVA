# Section 3: Object Oriented Programming (OOP) Deep Dive

## Module 1: The Core Pillars

### 1. Encapsulation
**Concept:** Wrapping data (variables) and code (methods) together as a single unit. It involves hiding the internal state of an object and requiring all interaction to be performed through public methods.
**Internal Working:** Uses Access Modifiers to restrict access.
**Memory Behavior:** Protects the integrity of fields on the heap.

### 2. Inheritance
**Concept:** One class acquiring the properties and behaviors of another.
**Why it exists:** For code reusability and establishing a "is-a" relationship.
**Internal Working:** In Java, uses the `extends` keyword. Java supports **Single Inheritance** for classes but **Multiple Inheritance** through interfaces.

### 3. Polymorphism
**Concept:** The ability of an object to take on many forms.
- **Static (Compile-time):** Method Overloading.
- **Dynamic (Runtime):** Method Overriding.
**JVM Behavior:** Uses **Virtual Method Invocation**. The JVM determines which method to call at runtime based on the actual object type, not the reference type.

### 4. Abstraction
**Concept:** Hiding complex implementation details and showing only the necessary features of an object.
**Mechanism:** Abstract classes and Interfaces.

---

## Module 2: Classes, Objects, & Constructors

### Deep Explanation
- **Class:** A blueprint for an object.
- **Object:** An instance of a class.
- **Constructor:** A special method called when an object is initialized. It has no return type.

### Memory Behavior
When you call `new MyClass()`, memory is allocated on the **Heap**. The constructor is then executed to initialize that memory. A reference to that memory is returned.

### Code Example
```java
public class Car {
    private String model;

    public Car(String model) {
        this.model = model;
    }

    public void display() {
        System.out.println("Model: " + model);
    }
}
```

---

## Module 3: Interfaces vs Abstract Classes

### Comparison
| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| Inheritance | `extends` (one class) | `implements` (many) |
| Variables | Can have instance variables | Only `public static final` (constants) |
| Methods | Can have concrete methods | Mostly abstract (can have default/static since Java 8) |
| Purpose | For related objects (shared identity) | For unrelated objects (shared behavior) |

---

## Module 4: SOLID Principles

### Deep Explanation
1. **Single Responsibility (SRP):** A class should have one reason to change.
2. **Open/Closed (OCP):** Open for extension, closed for modification.
3. **Liskov Substitution (LSP):** Derived classes must be substitutable for their base classes.
4. **Interface Segregation (ISP):** Better to have many specific interfaces than one general-purpose one.
5. **Dependency Inversion (DIP):** Depend on abstractions, not concretions.

---

## Module 5: Composition vs Inheritance

### Deep Explanation
Inheritance is "is-a", Composition is "has-a".
**Best Practice:** Favor composition over inheritance to make code more flexible and less tightly coupled.

### Code Example (Composition)
```java
class Engine {}
class Car {
    private Engine engine; // Car HAS-A Engine
}
```

### Interview Questions
- Difference between Overloading and Overriding.
- Why does Java not support multiple inheritance with classes?
- What is a "Diamond Problem"?
- Explain the `static` and `final` keywords.

### Exercise
1. Design a system for a Library Management using OOP principles. Include classes for `Book`, `Member`, and `Librarian`.
2. Implement a `Shape` interface and classes like `Circle` and `Rectangle` that implement it.
