# VoltPulse

VoltPulse is an Android battery intelligence application that combines live hardware telemetry, charging estimates, battery protection alerts, health history, and cable/adapter diagnostics in one dashboard.

> **Current release:** v1.0  
> **APK:** `VoltPulse.-.v1.0.apk`  
> **Minimum Android:** 7.0 (API 24)  
> **Target Android:** API 36  
> **Package:** `com.aistudio.voltpulse.bqkxvy`  
> **Version:** 1.0 (version code 1)

## Features

- **Live battery dashboard** — battery percentage, charging state, estimated time remaining or to full, temperature, voltage, current, power, cycle status, and charging speed.
- **Longevity alerts** — configurable 80% charging alarm and low-battery warning with sound and vibration support.
- **Lock-screen monitoring** — foreground notification for ongoing progress, live power, and charging countdown.
- **Cable and adapter diagnostics** — live impedance-oriented benchmark, voltage sag, estimated resistance, wattage, charging protocol, and A–F compatibility grade.
- **Health history** — locally stored battery measurements and diagnostic benchmark history.
- **Battery optimization controls** — guided request for exclusion from Android battery optimization where supported.
- **Health and maintenance guidance** — practical charging and battery care recommendations.

## APK Information

The published release asset is an Android package archive named **`VoltPulse.-.v1.0.apk`**. The APK is distributed through the repository’s GitHub Releases page, under the `v1.0` release.

**Release asset URL:**

https://github.com/Senterprisehub/Volt-Pulse/releases/download/v1.0/VoltPulse.-.v1.0.apk

**Latest release URL:**

https://github.com/Senterprisehub/Volt-Pulse/releases/latest

The signing configuration in the source supports separate debug and release keystores. Release builds use `my-upload-key.jks` by default unless `KEYSTORE_PATH` is supplied by the build environment. Signing passwords and aliases are read from `STORE_PASSWORD`, `KEY_PASSWORD`, and fixed alias configuration in `app/build.gradle.kts`.

## Installation

1. Download the latest APK from **[GitHub Releases](https://github.com/Senterprisehub/Volt-Pulse/releases/latest)**.
2. On Android, open the downloaded file.
3. If prompted, allow installation from the browser or file manager used to download it.
4. Launch **VoltPulse** from the app drawer.
5. Grant notification permission when requested for lock-screen alerts and the foreground monitoring service.

APK installation may require **Install unknown apps** permission for the browser or file manager used to open the package. Only install APKs from trusted sources.

## Requirements

- Android 7.0 (API 24) or newer.
- Android device that exposes battery telemetry through the Android framework.
- Some hardware values can vary by device and may not be available on all models.
- A charger is required for cable and adapter benchmark measurements.

## Permissions

VoltPulse declares the following permissions:

| Permission | Purpose |
|---|---|
| `INTERNET` | Network access for app dependencies and potential remote integrations. |
| `FOREGROUND_SERVICE` | Keeps battery monitoring active in a foreground service. |
| `FOREGROUND_SERVICE_SPECIAL_USE` | Identifies VoltPulse's live battery telemetry service as a special-use service. |
| `POST_NOTIFICATIONS` | Displays lock-screen charging progress and battery alerts on Android 13+. |
| `VIBRATE` | Provides haptic feedback for configured alerts. |
| `RECEIVE_BOOT_COMPLETED` | Allows boot-time initialization where supported. |
| `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` | Supports battery optimization exemption configuration. |

No location, camera, microphone, contacts, or storage permission is declared.

## Project Structure

```text
Volt-Pulse/
├── app/
│   ├── build.gradle.kts
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml
│       │   ├── java/com/example/
│       │   │   ├── MainActivity.kt
│       │   │   ├── data/
│       │   │   ├── hardware/
│       │   │   ├── model/
│       │   │   ├── receiver/
│       │   │   ├── service/
│       │   │   └── ui/
│       │   └── res/
│       └── test/
├── build.gradle.kts
├── gradle/
├── settings.gradle.kts
└── metadata.json
```

### Main components

- `MainActivity.kt` — application entry point and Compose host.
- `data/` — Room persistence, repositories, settings, and battery history storage.
- `hardware/` — battery hardware interface, robust estimation, and optional charging control.
- `model/` — battery telemetry and diagnostic data models.
- `receiver/` — device boot handling.
- `service/` — foreground monitoring and voice alert management.
- `ui/` — Compose screens, view model, navigation scaffold, and theme.

## Technology Stack

- Kotlin
- Jetpack Compose and Material 3
- AndroidX Activity, Lifecycle, Core KTX, and Room
- Retrofit, OkHttp, and Moshi
- Kotlin Coroutines
- Firebase App Check / Firebase BOM integration
- Gradle Kotlin DSL
- Unit tests with JUnit and Robolectric
- Instrumentation tests with AndroidX Test and Espresso

## Build from Source

### Prerequisites

- JDK 11 or newer
- Android SDK Platform 36
- Android Gradle Plugin and Gradle dependencies available to the project
- An Android device or emulator running API 24+

### Build

```bash
git clone https://github.com/Senterprisehub/Volt-Pulse.git
cd Volt-Pulse
./gradlew assembleDebug
```

The debug APK is produced under:

```text
app/build/outputs/apk/debug/
```

For a release build, configure the signing environment variables and key file:

```bash
export KEYSTORE_PATH=/absolute/path/to/my-upload-key.jks
export STORE_PASSWORD='keystore-password'
export KEY_PASSWORD='key-password'
./gradlew assembleRelease
```

The release APK is produced under:

```text
app/build/outputs/apk/release/
```

## Testing

Run local unit tests:

```bash
./gradlew test
```

Run instrumented tests on a connected device or emulator:

```bash
./gradlew connectedAndroidTest
```

## Privacy

VoltPulse reads Android battery and device telemetry needed for its dashboard and diagnostics. Persistence is implemented with local Room data structures. Network dependencies are present in the build, but the app description and source indicate no repository-defined account or user-authentication flow.

## Release

| Item | Value |
|---|---|
| Release | v1.0 |
| Version name | 1.0 |
| Version code | 1 |
| Package ID | `com.aistudio.voltpulse.bqkxvy` |
| Publish date | 2026-11-21 |

## License

No license file is currently included in this repository. Copyright and reuse terms should be confirmed with the repository owner before redistribution or commercial use.

## Support

Report bugs or request features through the repository’s [GitHub Issues](https://github.com/Senterprisehub/Volt-Pulse/issues).