# Module 9: Android System Internals - System Services

## Topic: Android Permissions Architecture

### Deep Explanation
Android uses a permission system to protect sensitive user data. Permissions are categorized by their risk level.

### Code Example: Requesting Runtime Permission
```java
if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA)
        != PackageManager.PERMISSION_GRANTED) {
    ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.CAMERA}, 100);
}
```

### Internal Working: GIDs and UIDs
At the kernel level, permissions are often mapped to Linux Group IDs (GIDs). For example, having the `INTERNET` permission might add your app's UID to the `inet` group, allowing the kernel to let your process open network sockets.

### Real Use Case
**Location Tracking Apps**: Modern Android versions require "Background Location" permission to be granted separately, ensuring apps don't track users without their explicit knowledge when the app is closed.

### Exercise
1. What is the difference between "Normal" and "Dangerous" permissions?
2. Explain the "Signature" permission level.

---

## Topic: Background Tasks & WorkManager

### Deep Explanation
Android has evolved to strictly limit background work to preserve battery life. `WorkManager` is the modern solution for persistent, deferrable background tasks.

### Code Example: WorkRequest
```java
Constraints constraints = new Constraints.Builder()
        .setRequiredNetworkType(NetworkType.UNMETERED)
        .build();

OneTimeWorkRequest syncWork = new OneTimeWorkRequest.Builder(SyncWorker.class)
        .setConstraints(constraints)
        .build();

WorkManager.getInstance(context).enqueue(syncWork);
```

### Internal Working: The Scheduler
WorkManager uses a combination of `JobScheduler` (on newer devices) and `AlarmManager` + `BroadcastReceiver` (on older devices) to ensure your task runs even if the app or device restarts.

### Real Use Case
**Photo Backup**: Apps like Google Photos use WorkManager to upload photos only when the device is charging and connected to Wi-Fi, preventing battery drain and data charges.

### Exercise
1. Why should you avoid long-running work in a `BroadcastReceiver`?
2. Explain the difference between "Exact Alarms" and "Inexact Alarms".

---

## Topic: Notification Manager Service

### Deep Explanation
Notifications are a way to communicate with users outside the normal app UI.

### Internal Working: Channels & Posting
1. **Notification Channels**: Mandatory (Android 8.0+). They allow users to block specific types of notifications (e.g., "Marketing") while keeping others (e.g., "Orders").
2. **Posting**: When an app calls `notify()`, the request is sent via Binder to the `NotificationManagerService`, which interacts with the **SystemUI** process to draw the notification.

### Real Use Case
**Instant Messaging**: Apps like WhatsApp use "High Priority" channels to ensure that the user is immediately notified of new messages even if the device is in "Do Not Disturb" mode.

### Exercise
1. What is a "PendingIntent" and how is it used in notifications?
2. How do "Notification Groups" improve the user experience?
