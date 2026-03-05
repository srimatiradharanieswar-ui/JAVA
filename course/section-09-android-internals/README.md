# Section 9: Android System Internals

## Module 1: Activity & Fragment Lifecycles

### Deep Explanation
Managing the state of the UI components is crucial for resource management.
**Activity Lifecycle:**
- `onCreate()`: Initialize.
- `onStart()`: Visible.
- `onResume()`: Interaction starts.
- `onPause()`: Part of it is visible, or about to stop.
- `onStop()`: No longer visible.
- `onDestroy()`: Reclaiming memory.

### Internal Working
The **ActivityManagerService (AMS)** manages the stack of activities and their states.

---

## Module 2: Intent System

### Deep Explanation
Intents are messages used to request an action from another component.
- **Explicit:** Targeted at a specific class.
- **Implicit:** Targeted at an action (e.g., "Open Browser").

### Internal Working
The **Intent Resolver** matches implicit intents against **Intent Filters** declared in `AndroidManifest.xml`.

---

## Module 3: Permissions & Security

### Deep Explanation
Android uses a "Sandboxing" model. Each app runs in its own Linux process with a unique User ID (UID).
**Permissions:**
- **Normal:** Granted at install.
- **Dangerous:** Granted at runtime (Location, Camera).

---

## Module 4: Background Tasks

### Deep Explanation
Android restricts background execution to save battery.
- **WorkManager:** Recommended for persistent tasks.
- **Foreground Services:** For tasks the user is aware of (Music player).

---

## Module 5: Storage & Notifications

### Storage
- **Internal:** App-private.
- **External (Scoped Storage):** Shared files (Photos).
- **Preferences:** Key-value pairs.

### Interview Questions
- What happens to an Activity when you rotate the screen?
- Explain the Fragment lifecycle in relation to the Activity lifecycle.
- What is a Context in Android?
- How does the system handle low memory situations?

### Exercise
1. Log every lifecycle stage of an Activity and observe the output when navigating and rotating the screen.
