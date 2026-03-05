# Module 9: Android System Internals

## Topic: Activity Lifecycle

### Concept Explanation
An Activity moves through various states managed by the OS.

### Internal Working: The State Machine
1.  **onCreate()**: Initial setup. View creation.
2.  **onStart()**: Visible to the user.
3.  **onResume()**: Interactive. Top of the stack.
4.  **onPause()**: Leaving the screen. Save small amounts of data.
5.  **onStop()**: No longer visible. Release heavy resources.
6.  **onDestroy()**: Final cleanup.

### Memory Behavior: Configuration Changes
When the screen rotates, the Activity is **Destroyed** and **Re-created**.
**Best Practice**: Use `ViewModel` to persist data across these changes.

---

## Topic: Fragment Lifecycle

### Concept Explanation
Similar to Activity but has extra hooks for its host (`onAttach`, `onCreateView`, `onDetach`).

---

## Topic: Intent System (Internal)

### Internal Working: The Binder IPC
Intents are not just local calls. They often cross process boundaries via **Binder**, Android's high-performance Inter-Process Communication (IPC) mechanism.
The **Activity Manager Service (AMS)** in the system process receives the Intent and decides which app component to launch.

---

## Topic: Storage Systems

### Concept Explanation
1.  **Internal Storage**: Private to the app (`data/data/pkg`).
2.  **External Storage**: Shared (Photos, Documents). Requires Scoped Storage (Android 10+).
3.  **SharedPreferences**: XML-based Key-Value store for small settings.

### Exercises
1. What happens to an Activity if you press the "Home" button? (onPause -> onStop).
2. What is the difference between `Serializable` and `Parcelable` in Android? (Parcelable is faster and optimized for IPC).
