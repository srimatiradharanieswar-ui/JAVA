# Module 3: OOP Deep Dive - SOLID & Advanced Patterns

## Topic: SOLID Principles (The Architect's Bible)

### 1. Single Responsibility Principle (SRP)
**Violation**: A `UserManager` class that saves to DB, sends emails, and calculates payroll.
**Solution**: Split into `UserRepository`, `EmailService`, and `PayrollCalculator`.

### 2. Open/Closed Principle (OCP)
**Violation**: An `AreaCalculator` with a huge `if/else` for every shape.
**Solution**: Use an interface `Shape` with an `area()` method. Adding a new shape doesn't require changing the calculator.

### 3. Liskov Substitution Principle (LSP)
**Violation**: `Square extends Rectangle`. Setting width changes height, breaking the rectangle contract.
**Solution**: Use a common `Shape` interface instead.

### 4. Interface Segregation Principle (ISP)
**Violation**: A `Worker` interface with `eat()` and `work()`. A `Robot` implementation is forced to implement `eat()`.
**Solution**: Split into `Workable` and `Eatable`.

### 5. Dependency Inversion Principle (DIP)
**Violation**: `App` class depends on `MySQLDatabase`.
**Solution**: `App` depends on `Database` interface. `MySQLDatabase` implements `Database`.

---

## Topic: Advanced Structural Patterns

### 1. Decorator Pattern
**Concept**: Attach additional responsibilities to an object dynamically.
**Real World Use Case**: Java I/O (`new BufferedReader(new FileReader(file))`).

### 2. Bridge Pattern
**Concept**: Decouple an abstraction from its implementation so the two can vary independently.
**Internal Working**: Uses composition to separate a class from its "driver" logic.

### 3. Strategy Pattern
**Concept**: Define a family of algorithms, encapsulate each one, and make them interchangeable.
**JVM Behavior**: Powers efficient JIT inlining when only one strategy is active.

### Code Example: Bridge Pattern
```java
interface Device { void turnOn(); }
class TV implements Device { public void turnOn() { /* TV logic */ } }

abstract class Remote {
    protected Device device;
    public Remote(Device d) { this.device = d; }
    abstract void power();
}
class SmartRemote extends Remote {
    public SmartRemote(Device d) { super(d); }
    void power() { device.turnOn(); }
}
```

### Exercises
1. Identify which SOLID principle is violated if you use `instanceof` in a loop.
2. Implement the Decorator pattern for a simple "Coffee" class with "Milk" and "Sugar" add-ons.
