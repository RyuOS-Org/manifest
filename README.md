# Ryu-UI Org 🚀

## Getting Started

To get started with **Ryu-UI Org** sources, you need to get familiar with [Git and Repo](https://source.android.com/setup/build/downloading).

Here are the instructions to build Ryu-UI Org.

### 1. Initialize the local repository

```bash
repo init -u https://github.com/RyuUI-Org/manifest.git -b vic --git-lfs
```

### 2. Sync the sources

```bash
repo sync --no-clone-bundle --current-branch --no-tags -j4
```

---

## Building the System

If you have private keys for signing your build, clone them into:

```bash
vendor/ryu-priv/keys
```
> *Note: This step is optional.*

---

### 3. Set Up the Device Makefile

In your device's makefile (`ryu_$device.mk`), inherit our vendor configuration:

```bash
$(call inherit-product, vendor/ryu/config/common_full_phone.mk)
```

---

## Build Flags

Below are Ryu-UI's common build flags you should be aware of:

```make
RYU_MAINTAINER := RyuDev
RYU_BUILD_TYPE := COMMUNITY
TARGET_BOOT_ANIMATION_RES := 720/1080/1440

# Additional flags
TARGET_FACE_UNLOCK_SUPPORTED := true
TARGET_SUPPORTS_GOOGLE_RECORDER := true
TARGET_SUPPORTS_QUICK_TAP := true
USE_PIXEL_CHARGER := true

# Note:
# - Ryu-UI is based on Pixel, so only GAPPS builds are supported (no vanilla XD).

# For devices with:
# - /sys/class/power_supply/battery/input_suspend
# - /sys/class/qcom-battery/input_suspend
# bypass charging can be enabled.
BYPASS_CHARGE_SUPPORTED := true (false by default)
```

---

### 4. Add Bypass Charging Rule

If your device supports bypass charging, add the following rule to your device tree `sepolicy`:

```bash
# input_suspend_label is the label assigned to /sys/class/power_supply/battery/input_suspend
allow init <input_suspend_label>:file rw_file_perms;
```

---

## Reference Commits

- [**Kernel 1**](https://github.com/romiyusnandar/android_kernel_xiaomi_sm6150/commit/80e2cb89402b45ff615db7536541f56addacfa54)
- [**Kernel 2 (Optional)**](https://github.com/romiyusnandar/android_kernel_xiaomi_sm6150/commit/16c9ecf37cbdaa7bea82c7489dfa441612a87a19)
- [**Device Tree**](https://github.com/romiyusnandar/android_device_xiaomi_sweet/commit/10289250991082c888d909319894489b89f9205a)
- [**Common Tree**](https://github.com/romiyusnandar/android_device_xiaomi_sm6150-common/commit/74dac9b9f086614da48cebc15c32d2009abaf5cb)

---

## Start Building 🚧

After cloning all required device sources:

1. **Initialize the environment:**
   ```bash
   source build/envsetup.sh
   ```

2. **Lunch your device:**
   (Or use `breakfast $device`)

   ```bash
   lunch ryu_$device-bp1a-userdebug
   ```

3. **Start compilation:**
   ```bash
   mka ryu
   ```

---

✨ Happy Building with Ryu-UI Org!

