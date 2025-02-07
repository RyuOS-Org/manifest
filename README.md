# Ryu-UI Org

## Getting Started

To get started with the Ryu-UI Org sources, you'll need to get
familiar with [Git and Repo](https://source.android.com/setup/build/downloading).

Here is some instruction for building Ryu-UI Org. To initialize your local repository, use command:

```bash
repo init -u https://github.com/RyuUI-Org/manifest.git -b vic --git-lfs
```

Then to sync up:
*Please dont use ```--optimize-fetch --force-sync etc``` to make sure all repo are synced

```bash
repo sync
```

## Building the System
Before that, clone your keys to
```bash

vendor/ryu-priv/keys
```

but this is optional, it's just for signing your build


Then inherit our vendor to your ```ryu_$device.mk```

```bash
$(call inherit-product, vendor/ryu/config/common_full_phone.mk)
```

Here is our flag's

```bash
RYU_MAINTAINER := RyuDev
RYU_BUILD_TYPE := Unofficial
TARGET_BOOT_ANIMATION_RES := 720/1080/1440
# GAPPS? Bro this rom based on pixel, just build for GAPPS, not vanila XD
```

Lunch your device after cloning all device sources if needed.
Initialize the ROM environment with the envsetup.sh script.

```bash
source build/envsetup.sh
```

Do launch, but u can use ```breakfast $device``` also

```bash
lunch ryu_$device-ap4a-userdebug
```

Then start compilation

```bash
mka ryu
```