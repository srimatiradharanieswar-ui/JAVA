# Module 9: Android System Internals - Boot & IPC

## Topic: The Boot Process & Zygote

### Concept Explanation
When you launch an app on Android, it starts almost instantly. This is because of the **Zygote** process.

### Internal Working: The Forking Mechanism
1.  **Zygote Initiation**: During system boot, a process called Zygote is started. It pre-loads all core Java classes and resources (ART, Framework libraries).
2.  **App Launch**: When the user clicks an icon, the system doesn't start a new VM. It tells Zygote to **fork()** itself.
3.  **Copy-on-Write (COW)**: The new app process shares all the memory of Zygote. Memory is only copied if the app modifies it. This saves massive amounts of RAM and time.

---

## Topic: Binder IPC (The Handshake)

### Concept Explanation
Android is a multi-process system. Every app, and every system service (Camera, GPS, Window Manager), runs in a separate process. **Binder** is the high-performance glue that connects them.

### Internal Working: The Kernel Driver
Binder is implemented as a Linux Kernel Driver.
1.  **Client-Side**: The app calls a proxy method.
2.  **Kernel-Space**: The Binder driver copies the data once from the Client's memory to the Server's memory (Single-copy IPC).
3.  **Server-Side**: The target process executes the method and returns the result.

### Real World Use Case: `AIDL`
When you want to expose a Service to other apps, you use **Android Interface Definition Language (AIDL)** to generate the Binder proxy/stub code.

---

## Topic: Activity Manager Service (AMS) & Task Management

### Concept Explanation
AMS is the "brain" of Android's UI. It lives in the `system_server` process.

### Internal Working: Starting an Activity
1.  **App Process**: Calls `startActivity()`. This sends a Binder message to AMS.
2.  **AMS Process**: Checks permissions, manages the "Back Stack," and determines if the target process is running.
3.  **AMS Process**: If not running, AMS tells Zygote to fork a new process.
4.  **Target Process**: AMS sends a message to the new process to call `ActivityThread.main()` and then `onCreate()`.

### Interview Questions
1. Why is Binder faster than standard Linux pipes or sockets?
2. What is a "TransactionTooLargeException"? (Binder has a 1MB limit for transaction data).

### Exercises
1. Explain the "Low Memory Killer" (LMK) and how it uses OOM scores to decide which app to kill first.
