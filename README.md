# DNS Proxy — Android App

[![Build APK](https://github.com/gasciljh/dnscrypt-proxy-app/actions/workflows/build.yml/badge.svg)](https://github.com/gasciljh/dnscrypt-proxy-app/actions/workflows/build.yml)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Android%205%2B-brightgreen.svg)](https://www.android.com/)

A lightweight native Android app that wraps the
[DNSCrypt Smart Filter](https://github.com/gasciljh/dnscrypt-proxy-webui)
WebUI in a WebView.

## 🎯 Purpose

Provides a native-feeling experience for the DNSCrypt WebUI
**without requiring Chrome, Firefox, or any specific browser**.
Works on any Android device with a modern WebView runtime
(Android 5.0+).

## ✨ Features

- 🚀 **Native WebView** — no browser dependency
- 🎨 **Dark theme** matching the WebUI
- 📊 **Progress bar** while pages load
- ⚠️ **Connection error screen** with helpful hints
- 🔗 **External links** open in the user's browser
- ⬅️ **Back button** navigates WebView history
- 🔒 **Only 127.0.0.1 / localhost** allowed (security)
- 📦 **Tiny APK** — ~2 MB

## 📋 Requirements

- Android 5.0 (API 21) or higher
- The DNSCrypt module installed and running
  (from [dnscrypt-proxy-webui](https://github.com/gasciljh/dnscrypt-proxy-webui))
- WebUI listening on `127.0.0.1:9090`

## 📥 Download

Get the latest APK from
[Releases](https://github.com/gasciljh/dnscrypt-proxy-app/releases).

## 🔨 Build from source

### Option 1: GitHub Actions (recommended)

1. Fork this repository.
2. Push any change or create a tag.
3. GitHub Actions builds the APK automatically.
4. Download the artifact from the Actions tab.

### Option 2: Local build

Requirements:
- JDK 17+
- Android SDK (API 34)
- Gradle 8.5+

```bash
./gradlew assembleDebug
```

APK output:
`app/build/outputs/apk/debug/app-debug.apk`

## 📲 Install

1. Download the APK.
2. Enable **Install from unknown sources** in Android settings.
3. Tap the APK to install.
4. Launch **DNS Proxy**.

## 🏗️ Architecture

This app is intentionally minimal:

- **Single activity** (`MainActivity.kt`) — ~170 lines
- **WebView** loads `http://127.0.0.1:9090/`
- **No background services**
- **No network permissions** beyond WebView needs
- **No analytics, no telemetry**
- **No external dependencies** beyond AndroidX

## 🔒 Security

- Cleartext HTTP is **allowed only** for `127.0.0.1`,
  `localhost`, and `10.0.2.2` (emulator loopback)
- All other traffic uses HTTPS by default
- No data is collected or sent anywhere
- `allowBackup="true"` — settings survive reinstall

## 📂 Project Structure

```
dnscrypt-proxy-app/
├── .github/workflows/
│   └── build.yml              # Automated APK build
├── app/
│   ├── src/main/
│   │   ├── java/com/gasciljh/dnsproxy/
│   │   │   └── MainActivity.kt
│   │   ├── res/
│   │   │   ├── drawable/      # Vector icons
│   │   │   ├── mipmap-anydpi-v26/  # Adaptive icons
│   │   │   ├── values/        # strings, colors, themes
│   │   │   └── xml/           # network config
│   │   └── AndroidManifest.xml
│   ├── build.gradle.kts
│   └── proguard-rules.pro
├── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
├── .gitignore
└── README.md
```

## 🤝 Related Projects

- [dnscrypt-proxy-webui](https://github.com/gasciljh/dnscrypt-proxy-webui) —
  The main module (Magisk / KernelSU / APatch)

## 📄 License

MIT — see [LICENSE](LICENSE).

## 🙏 Credits

- [DNSCrypt-proxy](https://github.com/DNSCrypt/dnscrypt-proxy) — DNS engine
- [HaGeZi DNS Blocklists](https://github.com/hagezi/dns-blocklists) — blocklists
- Built with AndroidX WebKit