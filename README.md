# WLED Build For SP530E

## Release Files

| File | Purpose |
|------|---------|
| `WLED_16.x.x_C3_Custom_FULL.bin` | Initial flash (includes bootloader + partition table), flash via esptool |
| `WLED_16.x.x_C3_Custom_OTA.bin` | OTA wireless update, upload via WLED web interface |

---

## Initial Flash (FULL)

Prepare a UART Converter  
Download `WLED_16.x.x_C3_Custom_FULL.bin` at the Release page  
Download ESPtool [Here](https://github.com/espressif/esptool/releases)

> The FULL binary already includes bootloader and partition table.  
> No need to download them separately.

### Connect UART Cable to board reverse side

### Backup original firmware
```
esptool read_flash 0 0x400000 sp530e-encrypted.bin
```

### Flash custom firmware
#### Replace `16.x.x` with the actual version number you downloaded (e.g., `16.0.0`)
```
esptool write_flash --encrypt 0x0 WLED_16.x.x_C3_Custom_FULL.bin
```

---

## OTA Wireless Update

1. Download `WLED_16.x.x_C3_Custom_OTA.bin` at the Release page
2. Connect to the same network as your device
3. Open the WLED web interface in a browser
4. Go to **Config** → **Security & Updates** → **Manual OTA Update**
5. Select the `*_OTA.bin` file, upload, and wait for the device to reboot

> **Note:** The FULL binary must be flashed at least once before OTA updates can be used.

---

## I/O Pins

| Function | GPIO |
|----------|------|
| On Board Button | GPIO 8 |
| On Board Mic | GPIO 3 |
| On Board Blue LED | GPIO 0 (Inverted) |
| On Board Green LED | GPIO 1 (Inverted) |
| LED DAT Output | GPIO 19 |

### Analog Pins

| Channel | GPIO |
|---------|------|
| R | GPIO 10 |
| G | GPIO 7 |
| B | GPIO 6 |
| WW | GPIO 5 |
| CW | GPIO 4 |
