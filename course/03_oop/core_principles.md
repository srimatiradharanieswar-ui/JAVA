# Module 3: Object Oriented Programming (OOP) Deep Dive

## Topic: Classes, Objects, and Constructors

### Concept Explanation
- **Class**: A blueprint or template for creating objects (e.g., `Car`).
- **Object**: An instance of a class (e.g., `MyTesla`).
- **Constructor**: A special method used to initialize objects.

### Internal Working
When `new Car()` is called:
1.  **Memory Allocation**: Space is allocated on the **Heap**.
2.  **Initialization**: Default values are assigned to fields.
3.  **Constructor Execution**: The constructor logic runs.
4.  **Reference Return**: The memory address is returned to the variable on the **Stack**.

---

## Topic: The Four Pillars of OOP

### 1. Encapsulation
**Concept**: Hiding the internal state of an object and requiring all interaction to be performed through public methods (Getters/Setters).

### 2. Inheritance
**Concept**: One class acquiring the properties and behaviors of another (`extends`).
**JVM Behavior**: Java uses **Single Inheritance** for classes. Every class in Java implicitly extends `java.lang.Object`.

### 3. Polymorphism
**Concept**: "Many forms."
- **Static Polymorphism**: Method Overloading.
- **Dynamic Polymorphism**: Method Overriding. Resolved at **runtime** via the **Virtual Method Table (V-Table)**.

### 4. Abstraction
**Concept**: Hiding complex implementation details and showing only functionality.
- **Abstract Classes**: Can have both abstract and concrete methods.
- **Interfaces**: Contracts that define "what" a class can do.

---

## Code Example: Polymorphism & Abstraction
```java
abstract class Animal {
    abstract void makeSound();
}

class Dog extends Animal {
    @Override
    void makeSound() { System.out.println("Bark"); }
}

public class TestOOP {
    public static void main(String[] args) {
        Animal myAnimal = new Dog();
        myAnimal.makeSound(); // Prints "Bark"
    }
}
```
