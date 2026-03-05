# Module 9: Android System Internals - Services

## Topic: Android Permissions

### Concept Explanation
Security mechanism to restrict access to sensitive data (Camera, Location).

### Internal Working
- **Normal Permissions**: Granted at install time.
- **Dangerous Permissions**: Must be requested at runtime (Android 6.0+).

---

## Topic: Background Tasks & WorkManager

### Concept Explanation
Operations that continue even if the user isn't in the app.

### Internal Working: Evolution
1.  **Thread/Handler**: Local to the app process.
2.  **AsyncTask**: Deprecated. Linked to Activity lifecycle.
3.  **JobScheduler/WorkManager**: (Modern) System-managed. Can defer tasks until the device is charging or on Wi-Fi.

---

## Topic: Notifications

### Concept Explanation
Messages shown outside the app UI.
**Internal Working**: Managed by the **Notification Manager Service**. Apps must define **Notification Channels** (Android 8.0+).

### Code Example: Creating a Channel
```java
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    NotificationChannel channel = new NotificationChannel(id, name, importance);
    NotificationManager manager = getSystemService(NotificationManager.class);
    manager.createNotificationChannel(channel);
}
```

### Exercises
1. Why should you avoid long-running work in a `BroadcastReceiver`? (It runs on the main thread and has a 10s limit).
2. Explain the difference between "Exact Alarms" and "Inexact Alarms".
