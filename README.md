# Shale - Namma Pride

School Transparency and Pride Portal for Karnataka government schools.

## What is Included

- Kotlin Android app targeting API 28+
- Jetpack Compose + Material 3 UI
- MVVM-oriented feature packages
- Hilt dependency injection
- Firebase Auth, Realtime Database, Storage, FCM, Analytics, Crashlytics, Performance, App Check dependencies
- Room offline cache for meals, gallery, achievements, and feedback
- DataStore language and school preferences
- WorkManager sync lane
- Firebase Realtime Database and Storage rule templates
- GitHub Actions Android build workflow

## Project Shape

```text
app/src/main/java/in/shale/nammapride
  core/data      Room, DataStore, Firebase repositories, sync worker
  core/di        Hilt providers
  core/model     Domain models and UI state
  core/ui        Theme, navigation, reusable UI, language toggle
  feature/auth   Admin login shell
  feature/dashboard
  feature/meals
  feature/gallery
  feature/stars
  feature/feedback
firebase/
  database.rules.json
  storage.rules
docs/
  architecture.md
  firebase-setup.md
  release-checklist.md
```

## Firebase Setup

1. Create a Firebase Android app with package `in.shale.nammapride`.
2. Download `google-services.json` into `app/`.
3. Enable Phone Authentication, Realtime Database, Storage, App Check, FCM, Analytics, Crashlytics, and Performance Monitoring.
4. Uncomment the Google Services, Crashlytics, and Performance plugins in `app/build.gradle.kts`.
5. Publish `firebase/database.rules.json` to Realtime Database.
6. Publish `firebase/storage.rules` to Storage.
7. Issue custom claims for approved admins:

```json
{
  "approvedAdmin": true,
  "schoolId": "demo-school",
  "role": "Headmaster"
}
```

The app also reads `adminProfiles/{uid}` from Realtime Database for in-app session validation.

## Build

Use Android Studio Ladybug or newer, or install a Gradle wrapper and run:

```powershell
gradle :app:assembleDebug
```

The repository currently does not include `google-services.json`, so Firebase Gradle plugins are intentionally commented until a real Firebase project is attached.
