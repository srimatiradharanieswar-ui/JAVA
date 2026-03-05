# Module 3: OOP Deep Dive - Advanced Concepts

## Topic: Interfaces vs Abstract Classes

### Concept Explanation
- **Abstract Class**: Represents an "is-a" relationship and can hold state.
- **Interface**: Represents a "can-do" relationship and defines a contract.

---

## Topic: Access Modifiers

### Concept Explanation
- **private**: Class only.
- **default**: Package only.
- **protected**: Package + Subclasses.
- **public**: Everywhere.

---

## Topic: Static and Final Keywords

### Static
**Memory Behavior**: Stored in the **Metaspace**. Created when the class is loaded.

### Final
- **Final Variable**: Constant.
- **Final Method**: Cannot be overridden.
- **Final Class**: Cannot be extended.

---

## Topic: Composition vs Inheritance

### Concept Explanation
- **Inheritance**: "Is-a" (`Car is a Vehicle`).
- **Composition**: "Has-a" (`Car has an Engine`).

### Best Practice
**Favor Composition over Inheritance.**
