# Module 8: Android Basics - Core Components

## Topic: The Big Four Components

### 1. Activity
**Concept**: A single screen with a user interface.

### 2. Service
**Concept**: A component for long-running operations in the background.
- **Foreground Service**: Shows a notification.
- **Background Service**: Less visible, subject to OS background limits.

### 3. Broadcast Receiver
**Concept**: Allows the app to listen for system-wide announcements.

### 4. Content Provider
**Concept**: Manages access to a structured set of data.

---

## Topic: Fragments

### Concept Explanation
A modular portion of an Activity. Represents a "sub-activity" that can be reused.

---

## Topic: Intent System

### Concept Explanation
Intents are "messages" used to request an action from another component.
- **Explicit Intent**: Launch a specific class.
- **Implicit Intent**: Ask the system to find an app that can perform an action.

### Code Example: Starting an Activity
```java
Intent intent = new Intent(this, SecondActivity.class);
intent.putExtra("key", "data");
startActivity(intent);
```

### Common Mistakes
- Not declaring a component in `AndroidManifest.xml`.
- Performing network operations on the Main Thread.

### Exercises
1. Difference between a `Started Service` and a `Bound Service`?
2. Create an Intent that opens the phone's dialer with a specific number.
