# Module 8: Android Development Using Java - Platform

## Topic: Android OS Architecture

### Concept Explanation
Android is a multi-layered software stack based on the Linux Kernel.

### Internal Working: The Stack
1.  **Linux Kernel**: Manages hardware drivers, memory, and process management.
2.  **Hardware Abstraction Layer (HAL)**: Interfaces between Java API and hardware.
3.  **Android Runtime (ART)**: Executes app bytecode. Uses AOT (Ahead-Of-Time) compilation.
4.  **Native C++ Libraries**: Graphics (OpenGL), SQLite, Webkit.
5.  **Java API Framework**: The components we use to build apps (Activity, WindowManager).
6.  **System Apps**: Dialer, Email, Browser.

---

## Topic: Gradle & Build System

### Concept Explanation
Gradle is the build automation tool used by Android Studio.

### Internal Working
- **Build Types**: `debug` vs `release` (ProGuard/R8 shrinking).
- **Flavors**: Creating different versions of an app.
- **Dependencies**: Managed via `implementation` in `build.gradle`.

---

## Topic: Android SDK & Android Studio

### Concept Explanation
- **Android Studio**: The official IDE based on IntelliJ.
- **SDK (Software Development Kit)**: The collection of libraries and tools (ADB, Emulator) needed to build apps.

### Code Example: AndroidManifest.xml
Every app must have this file. It describes the app's components, permissions, and required hardware.
```xml
<manifest ...>
    <application ...>
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

### Exercises
1. What is the difference between `minSdkVersion`, `targetSdkVersion`, and `compileSdkVersion`?
2. Explain the role of the `R.java` file.
