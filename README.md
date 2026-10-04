# 0xF001-fw

Release channel for the **product firmware** (`app_firmware`, OTA slot `ota_1`) of the ESP32-S3
RS-485 isolated gateway, product id `0xF001`.

Each release carries one file, the ChaCha20-encrypted application image `fw_*_enc.bin`,
built and published by the release workflow of
[esp32s3-rs485-iso-gateway-fw](https://github.com/dtbao-firmware/esp32s3-rs485-iso-gateway-fw).
The tag matches that repository's version (`vX.Y.Z`).

## How a unit installs it

The updater in `ota_0` (released in
[0xF001-bl](https://github.com/dtbao-firmware-release/0xF001-bl)) fetches this file over Wi-Fi,
or reads it from microSD as `update.bin`, then decrypts it and writes it into `ota_1`.
The image is encrypted, so the plain `.bin` from the source repository will not install
through the updater.

## Sibling channel

Both apps share the `cfg_setting` and `cfg_factory` partitions, so a release note states the
oldest updater version it works with when that matters.

The source, build instructions and the full set of artefacts (bootloader, partition table,
`.elf`, plain `.bin`) live in the source repository, not here.
