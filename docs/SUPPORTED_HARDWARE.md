# Supported Hardware

NexusFlight v0.3.2 supports **27 flight controller boards** across 6 MCU families.

## Board Compatibility

### STM32F405 (168 MHz, 1 MB Flash, 192 KB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| SpeedyBee F405 V4 | BMI270 | MAX7456 | W25Q128 | Stable |
| SpeedyBee F405 V3 | BMI270 | MAX7456 | W25Q128 | Stable |
| SpeedyBee F405 Mini | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| SpeedyBee F405 AIO | BMI270 | MAX7456 | W25Q128 | Stable |
| SpeedyBee F405 Wing | BMI270 | MAX7456 | W25Q128 | Stable |
| Happymodel SuperF405 | ICM-42688-P | AT7456E | W25Q128 | Stable |
| Flywoo F405S AIO | BMI270 | MAX7456 | W25Q128 | Stable |
| GEPRC F405 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| Matek F405 Wing V2 | ICM-42688-P | MAX7456 | W25Q128 | Stable |

### STM32F411 (100 MHz, 512 KB Flash, 128 KB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| BetaFPV F411 | BMI270 | AT7456E | None | Stable |
| HDZero AIO5 | BMI270 | None | None | Stable |
| Happymodel CrazyBee F4 DX | BMI270 | AT7456E | None | Stable |

### STM32F722 (216 MHz, 512 KB Flash, 256 KB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| Flywoo F722 Pro V2 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| GEPRC F722 AIO | ICM-42688-P | MAX7456 | W25Q128 | Stable |

### STM32G473 (170 MHz, 512 KB Flash, 128 KB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| CrazyBee G473 | BMI270 | AT7456E | None | Stable |
| BetaFPV G473 | BMI270 | AT7456E | None | Stable |
| GEPRC Taker G473 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| HDZero Gamma 45A | ICM-42688-P | None | W25Q128 | Stable |
| HDZero AIO15 | BMI270 | None | None | Stable |

### STM32H743 (480 MHz, 2 MB Flash, 1 MB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| HDZero Halo | ICM-42688-P | None | W25Q128 | Stable |
| GEPRC Taker H743 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| Sequre H7 V1 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| Sequre H7 V2 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| Matek H743 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| T-Motor Pacer H743 | ICM-42688-P | MAX7456 | W25Q128 | Stable |
| iFlight Blitz H7 Pro | ICM-42688-P | MAX7456 | W25Q128 | Stable |

### AT32F435 (288 MHz, 4 MB Flash, 512 KB RAM)

| Board | Gyro | OSD | Flash | Status |
|-------|------|-----|-------|--------|
| iFlight Blitz F4 F435 | BMI270 | MAX7456 | W25Q128 | Beta |

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Stable** | Fully tested, ready for flight |
| **Beta** | Functional but still undergoing testing — fly with caution |

## Supported Sensors

### Gyroscopes / IMUs
- **Bosch BMI270** — SPI, 3.2 kHz sampling (with config blob upload)
- **TDK ICM-42688-P** — SPI, 8 kHz sampling
- **InvenSense MPU6000** — SPI, 8 kHz sampling (legacy boards)
- **InvenSense ICM-20689** — SPI, 8 kHz sampling (legacy boards)

### OSD Chips
- **MAX7456** — SPI, PAL/NTSC auto-detect
- **AT7456E** — MAX7456-compatible clone
- **MSP DisplayPort** — Digital VTX OSD (DJI/HDZero/Walksnail)

### GPS Modules
- **u-blox M8/M9/M10** — UBX binary protocol over UART, 10 Hz update rate

### VTX Control
- **SmartAudio v1/v2** — Single-wire UART
- **Tramp IRC** — UART half-duplex

### RC Protocols
- **CRSF / ELRS** — UART, bidirectional telemetry, 16 channels
- **S.BUS** — Inverted UART, 16 channels

### Motor Protocols
- **DShot150** — Digital, bidirectional telemetry capable
- **DShot300** — Digital, bidirectional telemetry capable
- **DShot600** — Digital, bidirectional telemetry capable (recommended)

## Supported Aircraft

| Frame | Motors | Recommended MCU | Gyro | Notes |
|-------|--------|----------------|------|-------|
| 65mm whoop | 4 | F411 | BMI270 | 1S brushless |
| 75mm whoop | 4 | F411 | BMI270 | 1-2S brushless |
| 3" toothpick | 4 | F405/G473 | BMI270/ICM-42688-P | Lightweight build |
| 5" freestyle/racing | 4 | F405/F722/G473 | ICM-42688-P | Most popular class |
| 5" HD (digital VTX) | 4 | G473/H743 | ICM-42688-P | Higher MCU for OSD + GPS |
| 7-8" long range | 4 | F405/F745/H743 | ICM-42688-P | GPS rescue recommended |

## Adding a New Board

If your board isn't listed, you can request support:

1. Open an [Issue](https://github.com/AutomataNexus/NexusFlight-Suite/issues/new) with:
   - Board name and manufacturer
   - MCU model
   - Gyro/IMU model
   - Link to the board's pinout diagram or schematic
2. Or [request source access](../README.md#request-source-access) and submit a board definition PR

Board definitions are Rust structs mapping MCU pins to peripherals — typically 30-50 lines of code.

## Minimum Hardware Requirements

| Component | Requirement |
|-----------|-------------|
| MCU | ARM Cortex-M4F or higher, 100+ MHz, 512+ KB Flash |
| Gyro | SPI-connected 6-axis IMU (3-axis gyro + 3-axis accel) |
| Flash | (Optional) SPI dataflash for blackbox logging |
| OSD | (Optional) MAX7456-compatible chip or digital VTX with DisplayPort |
| USB | USB-FS or USB-OTG for configuration and firmware updates |
