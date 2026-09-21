# tdlib-packed

Automated packager and distributor for prebuilt [Telegram X TDLib](https://github.com/TGX-Android/tdlib) binaries and Java bindings for Android.

This repository tracks upstream releases from `TGX-Android/tdlib`, pairs the compiled libraries with the matching Android NDK `libc++_shared.so`, and packages them into clean, drop-in zip archives (`tdlib-v<version>.zip`).

---

## 📦 What's Inside

Each release includes `tdlib-v<version>.zip` with the following structure:

```
tdlib-v<version>.zip
├── libs/
│   ├── arm64-v8a/
│   │   ├── libc++_shared.so
│   │   ├── libcryptox.so
│   │   ├── libsslx.so
│   │   └── libtdjni.so
│   ├── armeabi-v7a/
│   │   ├── libc++_shared.so
│   │   ├── libcryptox.so
│   │   ├── libsslx.so
│   │   └── libtdjni.so
│   ├── x86_64/
│   │   ├── libc++_shared.so
│   │   ├── libcryptox.so
│   │   ├── libsslx.so
│   │   └── libtdjni.so
│   └── x86/
│       ├── libc++_shared.so
│       ├── libcryptox.so
│       ├── libsslx.so
│       └── libtdjni.so
└── java/
    └── org/drinkless/tdlib/
        ├── Client.java
        └── TdApi.java
```

---

## 🚀 Usage in Android Projects

1. Download `tdlib-v<version>.zip` from the latest [Release](https://github.com/CodexofLost/tdlib-packed/releases).
2. Extract the archive.
3. Copy `libs/*` into your project's `app/src/main/jniLibs/`.
4. Copy `java/*` into your project's `app/src/main/java/`.

---

## ⚙️ Automation

* **Schedule:** Automatically checks every 24 hours if `TGX-Android/tdlib` has received new updates. If an update is detected, it packages and publishes a new release.
* **Manual:** Can be triggered on demand via GitHub Actions (`workflow_dispatch`), with an optional `force` re-packaging toggle.
* **Validation:** All 16 native `.so` files and Java binding files are verified before release creation.

---

## 📄 License

* TDLib is licensed under the Boost Software License 1.0.
* See [TGX-Android/tdlib](https://github.com/TGX-Android/tdlib) and [tdlib/td](https://github.com/tdlib/td) for upstream licenses.
