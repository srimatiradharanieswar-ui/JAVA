# Module 3: OOP Deep Dive - Core Principles

## Topic: Encapsulation & Data Hiding

### Deep Explanation
Encapsulation is the bundling of data (fields) and the methods that operate on that data into a single unit (class). It involves hiding the internal state of an object and requiring all interaction to be performed through a well-defined interface.

### Code Example: Proper Encapsulation
```java
public class BankAccount {
    private double balance; // Hidden state

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount; // Controlled access
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

### Internal Working: Access Control
The JVM enforces access modifiers (`private`, `protected`, `public`) during both compilation and runtime. Fields marked `private` are not visible in the class's constant pool to external classes, preventing direct byte-level access.

### Real Use Case
**API Design**: By encapsulating internal logic, developers can change how a class works (e.g., switching from a List to a Set internally) without breaking the code of anyone using that class.

### Exercise
1. Explain the difference between "Information Hiding" and "Encapsulation".
2. Create a class where the setter method performs validation logic.

---

## Topic: Polymorphism (Static vs Dynamic)

### Deep Explanation
Polymorphism allows objects of different types to be treated as objects of a common supertype.

### Code Example: Dynamic Method Dispatch
```java
class Animal { void sound() { System.out.println("Noise"); } }
class Dog extends Animal { void sound() { System.out.println("Bark"); } }

Animal myDog = new Dog();
myDog.sound(); // Prints "Bark"
```

### Internal Working: Virtual Method Table (Vtable)
The JVM uses a **vtable** for every class. It is an array of memory addresses for the class's methods. When `invokevirtual` is called, the JVM looks up the method address in the vtable of the *actual* object type at runtime, not the reference type.

### Real Use Case
**UI Frameworks**: Android's `View` system uses polymorphism. The system calls `onDraw()` on a list of `View` objects, and whether it's a `Button`, `TextView`, or `ImageView`, the correct drawing logic is executed.

### Exercise
1. What is the difference between Method Overloading and Method Overriding in terms of when they are resolved?
2. Research how the keyword `final` affects the vtable.
