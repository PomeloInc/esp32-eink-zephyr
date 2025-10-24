# ESP32 E-Ink Zephyr

This repository contains notes and a minimal guide for building Zephyr for the Waveshare ESP32-S3 PhotoPainter display.

Note: the original README had duplicated and partially-overwritten sections; this file is a consolidated, cleaned version.

## Quick start

1. Install the Zephyr dependencies: https://docs.zephyrproject.org/latest/develop/getting_started/index.html#install-dependencies
2. Setup the Zephyr project and toolchains in a project folder of your choosing.

Run the following in a shell inside your project folder:

```bash
# Create and activate Python virtual environment.
python3 -m venv .venv
source .venv/bin/activate

# Upgrade pip and install west.
pip install --upgrade pip
pip install west

# Initialize and fetch Zephyr.
west init .
west update
west zephyr-export
west packages pip --install

# Get relevant toolchains and SDK for ESP32.
cd zephyr
west sdk install
west blobs fetch hal_espressif
cd ..

# Verify build environment with hello world.
west build -b esp32s3_devkitc/esp32s3/procpu samples/hello_world --pristine
```

3. Connect the Photopainter via USB. To flash and monitor it use:

```bash
west flash && west espressif monitor
```

## Required hardware

- Waveshare ESP32-S3 PhotoPainter: https://www.waveshare.com/wiki/ESP32-S3-PhotoPainter
- Raspberry Pi 5 (for tooling or developer host)

## OTA updates

This project will feature OTA updates using Mender. See the microcontroller preview docs for ESP32 + Zephyr:

- https://docs.mender.io/get-started/microcontroller-preview/prepare-an-esp32-s3-with-zephyr

## References

- Zephyr Project — Getting Started: https://docs.zephyrproject.org/latest/develop/getting_started/index.html
- West (Zephyr meta-tool): https://docs.zephyrproject.org/latest/guides/west/index.html
- Mender (OTA): https://docs.mender.io/
- Waveshare ESP32-S3 PhotoPainter: https://www.waveshare.com/wiki/ESP32-S3-PhotoPainter
- ESP32-S3 Reference Manual: https://documentation.espressif.com/esp32-s3_technical_reference_manual_en.html
- Guide: https://www.hackster.io/gkiryaziev/zephyr-on-esp32-s3-your-first-hello-world-74aec3
- Features: https://www.waveshare.com/esp32-s3-photopainter.htm

