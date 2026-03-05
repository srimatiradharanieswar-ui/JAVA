# Section 8: Android Development Using Java

## Module 1: Android Architecture & Ecosystem

### Deep Explanation
Android is a Linux-based open-source operating system.
**Layers:**
1. **Linux Kernel:** Hardware abstraction, memory/process management.
2. **HAL (Hardware Abstraction Layer):** Interfaces for hardware vendors.
3. **Android Runtime (ART):** Replaced Dalvik. Uses AOT (Ahead-of-Time) and JIT compilation.
4. **Java API Framework:** The toolkit used by developers.
5. **System Apps.**

---

## Module 2: Core Components

### 1. Activity
A single screen with a user interface.
### 2. Fragment
A reusable portion of the UI within an Activity.
### 3. Service
Background task without a UI.
### 4. Broadcast Receiver
System-wide announcements (e.g., Battery Low).
### 5. Content Provider
Managing access to a central repository of data.

---

## Module 3: UI System & XML

### Deep Explanation
Android UI is defined in XML files.
- **ViewGroup:** Container for Views (LinearLayout, ConstraintLayout).
- **View:** Individual UI elements (TextView, Button).

### RecyclerView
A flexible and efficient way to display large datasets.
**Internal Working:** It recycles view holders to save memory and CPU, preventing the creation of hundreds of view objects.

### Code Example (Simple Layout)
```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello Android!" />

</LinearLayout>
```

---

## Module 4: Gradle & Build System

### Deep Explanation
Gradle is the build automation tool used by Android Studio.
- `build.gradle (Project)`: Global configuration.
- `build.gradle (Module)`: App-specific dependencies and versions.

---

## Module 5: View Lifecycle

### Deep Explanation
Views go through stages: `onMeasure()`, `onLayout()`, and `onDraw()`.

### Interview Questions
- What is ART?
- Difference between Activity and Fragment.
- Why is `ConstraintLayout` preferred over `RelativeLayout`?
- How does `RecyclerView` work internally?

### Exercise
1. Create a simple Activity with a Button that changes a TextView message when clicked.
