# Module 9: Android System Internals - Lifecycles & Intents

## Topic: Activity Lifecycle Internals

### Deep Explanation
The Activity lifecycle is the set of states an Activity transitions through, from creation to destruction.

### Code Example: Lifecycle Observer
```java
public class MyObserver implements DefaultLifecycleObserver {
    @Override
    public void onStart(LifecycleOwner owner) {
        // Automatically called when Activity starts
    }
}
```

### Internal Working: LifecycleRegistry
The system doesn't just call `onCreate()`. It uses a `LifecycleRegistry` that maintains the state as an enum. When the OS triggers a state change, the registry notifies all registered observers. This allows "Lifecycle-aware" components (like LiveData) to automatically clean up resources when the Activity is destroyed.

### Real Use Case
**Camera Management**: Apps must release the Camera hardware in `onPause()` or `onStop()` to ensure that other apps can use it. Failing to do so can lead to system-wide hardware freezes.

### Exercise
1. What is the difference between `onStop()` and `onDestroy()`?
2. Why is it dangerous to perform UI updates in `onSaveInstanceState()`?

---

## Topic: Binder IPC (Inter-Process Communication)

### Deep Explanation
Android apps run in isolated processes. Binder is the high-performance mechanism that allows processes to communicate and share data safely.

### Code Example: AIDL Interface
```aidl
// IMyAidlInterface.aidl
interface IMyAidlInterface {
    void performAction(int value);
}
```

### Internal Working: The Kernel Driver
Binder is implemented as a Linux Kernel Driver.
1. **Client-Side**: The app calls a method on a "Proxy" object.
2. **Kernel-Space**: The Binder driver copies the data once from the Client's memory to the Server's memory (Single-copy IPC).
3. **Server-Side**: The target process executes the method on a "Stub" and returns the result.

### Real Use Case
**System Services**: Every time you call `getSystemService()`, you are using Binder to talk to a separate system process (like the `LocationManagerService`).

### Exercise
1. Why is Binder faster than standard Linux pipes or sockets?
2. What is a "TransactionTooLargeException"?

---

## Topic: Activity Manager Service (AMS)

### Deep Explanation
AMS is the "brain" of Android's UI, responsible for starting activities, managing tasks (the "Back Stack"), and handling low-memory situations.

### Internal Working: Starting a Process
1. App calls `startActivity()`.
2. A message is sent via Binder to **AMS**.
3. AMS checks if the target process exists.
4. If not, AMS sends a socket message to **Zygote**.
5. Zygote forks a new process and starts the `ActivityThread`.

### Real Use Case
**Task Switching**: When you press the "Recents" button, you are interacting with AMS, which manages the "Task Records" and decides which app to bring to the foreground.

### Exercise
1. Explain the "Low Memory Killer" (LMK) and how it uses OOM scores.
2. What is the difference between a "Task" and a "Process" in Android?
