# Module 8: Android Development - Platform & Tooling

## Topic: The Android Architecture Stack

### Deep Explanation
Android is a multi-layered software stack based on the Linux kernel. Understanding each layer—from the hardware abstraction to the application framework—is essential for high-level engineering.

### Code Example: Check Android Version
```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.S) {
    // Execute code specific to Android 12 (API 31)
}
```

### Internal Working: The 5 Layers
1. **Linux Kernel**: Handles drivers (Camera, Audio), Power Management, and Security.
2. **HAL (Hardware Abstraction Layer)**: Standard interfaces for hardware vendors to implement.
3. **Android Runtime (ART)**: Executes APK/AAB files using JIT and AOT compilation.
4. **Native C/C++ Libraries**: Low-level libraries like SQLite, OpenGL, and WebKit.
5. **Java API Framework**: The high-level APIs (`Activity`, `Service`, `ContentProvider`) used by developers.

### Real Use Case
**Custom ROM Development**: Developers working on LineageOS or Pixel Experience spend most of their time in the HAL and Kernel layers to ensure Android runs smoothly on specific hardware.

### Exercise
1. What is the role of the "Zygote" process in Android?
2. Explain the difference between Dalvik and ART (Android Runtime).

---

## Topic: Android Build System (Gradle & R8)

### Deep Explanation
Android uses Gradle as its build tool. The build process involves compiling Java/Kotlin code, processing resources, and packaging everything into an APK or Android App Bundle (AAB).

### Code Example: ProGuard/R8 Rule
```gradle
# keep the names of classes that implement Serializable
-keepclassmembers class * implements java.io.Serializable {
    static final long serialVersionUID;
    private static final java.io.ObjectStreamField[] serialPersistentFields;
}
```

### Internal Working: R8 Shrinking
R8 is the replacement for ProGuard. It performs:
- **Shrinking**: Removes unused code and resources.
- **Optimization**: Rewrites bytecode for better performance.
- **Obfuscation**: Renames classes and members to short, cryptic names to reduce file size and hinder reverse engineering.

### Real Use Case
**App Bundle (AAB)**: Using AABs instead of APKs allows the Google Play Store to generate optimized APKs for each user's device configuration, significantly reducing the download size.

### Exercise
1. What is "Transitive Dependency" in Gradle?
2. Why is obfuscation important for a commercial Android application?
