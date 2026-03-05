# Module 12: Real World Projects - Part 1

## Project 1: Notes Application (MVVM + Room)

### Overview
A classic application to master the core Android Jetpack components.

### Architecture
- **View**: `MainActivity` and `AddNoteActivity`.
- **ViewModel**: `NoteViewModel` uses LiveData to provide data to UI.
- **Repository**: Handles the logic between the DAO and ViewModel.
- **Database**: Room Database with a `Note` entity (title, description, priority).

### Key Features
- CRUD operations (Create, Read, Update, Delete).
- Sorting notes by priority.
- Swipe-to-delete using `ItemTouchHelper`.

---

## Project 2: Secure DNS Android App

### Overview
A systems-level app to change the device's DNS settings for privacy.

### Core Technologies
- **VpnService**: The Android API used to intercept network traffic and route it to a DNS-over-HTTPS (DoH) server.
- **JNI (Java Native Interface)**: (Optional) Using C++ for high-performance packet processing.
- **Foreground Service**: Necessary to keep the VPN running.

### Challenges
- Handling network transitions (Wi-Fi to LTE).
- Managing app-level permissions and system VPN dialogues.
