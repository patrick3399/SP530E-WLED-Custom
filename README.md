# WLED Build For SP530E

## Release 檔案說明

| 檔案 | 用途 |
|------|------|
| `WLED_16.x.x_C3_Custom_FULL.bin` | 首次刷機（含 bootloader + partitions），使用 esptool 燒錄 |
| `WLED_16.x.x_C3_Custom_OTA.bin` | OTA 無線更新，從 WLED 網頁介面上傳 |

---

## 首次刷機（FULL）

### 準備工具
- UART Converter
- Download `WLED_16.x.x_C3_Custom_FULL.bin` at Release page
- Download ESPtool [Here](https://github.com/espressif/esptool/releases)

> The FULL binary already includes bootloader and partition table.  
> No need to download them separately.

### Connect UART Cable to board reverse side

### 備份原廠韌體
```
esptool read_flash 0 0x400000 sp530e-encrypted.bin
```

### 燒錄自訂韌體
#### Please replace `16.x.x` with the actual version number you downloaded (e.g., `16.0.0`)
```
esptool write_flash --encrypt 0x0 WLED_16.x.x_C3_Custom_FULL.bin
```

---

## OTA 無線更新

1. Download `WLED_16.x.x_C3_Custom_OTA.bin` at Release page
2. 連上裝置的 Wi-Fi 或同網段
3. 開啟瀏覽器進入 WLED 網頁介面
4. 前往 **Config** → **Security & Updates** → **Manual OTA Update**
5. 選擇 `*_OTA.bin` 檔案並上傳，等待重啟完成

> **注意：** 首次使用請先用 FULL 版本完整燒錄，之後才能使用 OTA 更新。

---

## I/O Pins

| 功能 | GPIO |
|------|------|
| On Board Button | GPIO 8 |
| On Board Mic | GPIO 3 |
| On Board Blue LED | GPIO 0 (Inverted) |
| On Board Green LED | GPIO 1 (Inverted) |
| LED DAT Output | GPIO 19 |

### Analog Pins

| 頻道 | GPIO |
|------|------|
| R | GPIO 10 |
| G | GPIO 7 |
| B | GPIO 6 |
| WW | GPIO 5 |
| CW | GPIO 4 |
