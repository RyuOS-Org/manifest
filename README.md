<div align="center">

# 🐉 RyuOS-Org

*An Android Custom ROM based on AOSP*

[![GitHub](https://img.shields.io/badge/GitHub-RyuOS--Org-blue?style=for-the-badge&logo=github)](https://github.com/RyuOS-Org)
[![License](https://img.shields.io/badge/License-Apache--2.0-green?style=for-the-badge)](https://www.apache.org/licenses/LICENSE-2.0.txt)
[![Android](https://img.shields.io/badge/Android-16-brightgreen?style=for-the-badge&logo=android)](https://android.com)

</div>

---

## 🚀 Getting Started

Before you begin, make sure you're familiar with:
- 📖 [Git and Repo](https://source.android.com/setup/build/downloading)
- 💻 [System Requirements](https://source.android.com/docs/setup/start/requirements)

### 📥 Initialize Repository

```bash
repo init -u https://github.com/RyuOS-Org/manifest.git -b 16 --git-lfs
```

### 🔄 Sync Sources

> **Note:** `-j8` uses 8 threads. Adjust based on your CPU cores (8 is recommended).

```bash
repo sync -c -j8
```

---

## 🔨 Building the System

### 1️⃣ Initialize Environment

```bash
. build/envsetup.sh
```

### 2️⃣ Configure Build Flags

Clone your device tree and choose your configuration options:

#### 📱 Google Apps (GApps)
```bash
WITH_GAPPS := true
```

#### 📱 Google Apps Go Edition
```bash
WITH_GAPPS := true
WITH_GAPPS_GO := true
```

#### ⚙️ Additional Flags
```bash
TARGET_BOOT_ANIMATION_RES := 1080
RYUOS_MAINTAINER := RyuDev
RYUOS_BUILD_TYPE := OFFICIAL
```

### 3️⃣ Device Configuration

> **Example:** `lunch ryuos_sweet-bp2a-userdebug`

```bash
lunch ryuos_devicecodename-bp2a-buildtype
```

### 4️⃣ Start Compilation

```bash
make ryuos
```

---

## 📋 Build Types

| Build Type | Description |
|------------|-------------|
| `eng` | Engineering build with debugging enabled |
| `userdebug` | User build with debugging capabilities |
| `user` | Production build for end users |

---

## 🤝 Contributing

We welcome contributions! Please feel free to submit issues and pull requests.

---

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](https://www.apache.org/licenses/LICENSE-2.0.txt) file for details.

---

<div align="center">

**Made with ❤️ by the RyuOS Team**

</div>