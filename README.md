# Slot for RG353PS

Experimental [Slot](https://github.com/BrandonKowalski/slot) frontend bundle for the Anbernic RG353PS (RK3566).

This repository isolates the RG353PS-specific Slot integration from BaseOS and NextUI:
- SDL2 KMSDRM/EGL surface adaptation for the 640×480 panel.
- RG353PS D-pad and Nintendo face-button input mapping.
- BaseOS frontend adapter/launcher and reproducible bundle build.
- CI builds a distributable ZIP and SHA-256 checksum.

## Build

Run on a Linux ARM64 host with Docker installed:

```sh
sh platforms/rg353ps/build-slot.sh
```

The build downloads pinned upstream Slot, mGBA and gpSP revisions, applies the local RG353PS patch, builds a dynamically linked AArch64 executable (needed for SDL2 dynamic loading), and packages the frontend.

Output: `work/rg353ps/frontends/baseos-rg353ps-slot.zip` and its `.sha256` file.

## Install

Extract the ZIP to the BaseOS user-data partition (normally `/mnt/SDCARD`). The package provides `.baseos/frontends/slot/launch.sh` and `System/slot`.

This is an experimental community port. A successful CI build is not a substitute for testing on physical RG353PS hardware.
