# Supported Hardware

NexusFlight v0.1.0 supports **27 flight controller boards** across 6 MCU families.

## Board Compatibility

### STM32F405 (168 MHz, 1 MB Flash, 192 KB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| Matek F405-SE | STM32F405RGT6 | MPU6000 | MAX7456 | Stable |
| Matek F405-CTR | STM32F405RGT6 | MPU6000 | MAX7456 | Stable |
| SpeedyBee F405 V3 | STM32F405RGT6 | BMI270 | MAX7456 | Stable |
| SpeedyBee F405 V4 | STM32F405RGT6 | BMI270 | MAX7456 | Stable |
| SpeedyBee F405 Wing | STM32F405RGT6 | BMI270 | MAX7456 | Stable |
| Foxeer F405 V2 | STM32F405RGT6 | MPU6000 | MAX7456 | Stable |
| iFlight SucceX-E F4 | STM32F405RGT6 | MPU6000 | MAX7456 | Stable |
| BetaFPV F405 AIO | STM32F405RGT6 | BMI270 | AT7456E | Stable |
| JHEMCU GF25F405-AIO | STM32F405RGT6 | ICM-42688-P | MAX7456 | Stable |
| HGLRC Zeus F405 | STM32F405RGT6 | BMI270 | MAX7456 | Stable |
| Diatone Mamba F405 MK2 | STM32F405RGT6 | MPU6000 | MAX7456 | Stable |
| Flywoo GN F405 | STM32F405RGT6 | BMI270 | MAX7456 | Stable |

### STM32F411 (100 MHz, 512 KB Flash, 128 KB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| SpeedyBee F405 Mini | STM32F411CEU6 | BMI270 | MAX7456 | Stable |
| BetaFPV F4 1S 12A AIO | STM32F411CEU6 | BMI270 | AT7456E | Stable |
| Happymodel CrazyBee F4 | STM32F411CEU6 | BMI270 | AT7456E | Stable |
| Matek F411-WMN | STM32F411CEU6 | MPU6000 | MAX7456 | Stable |

### STM32F722 (216 MHz, 512 KB Flash, 256 KB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| Matek F722-SE | STM32F722RET6 | MPU6000 | MAX7456 | Stable |
| SpeedyBee F7 V3 | STM32F722RET6 | BMI270 | MAX7456 | Stable |
| JHEMCU GF30F722-AIO | STM32F722RET6 | ICM-42688-P | MAX7456 | Stable |
| Foxeer F722 V4 | STM32F722RET6 | BMI270 | MAX7456 | Stable |
| iFlight SucceX-D F7 | STM32F722RET6 | ICM-20689 | MAX7456 | Stable |
| Diatone Mamba F722 | STM32F722RET6 | MPU6000 | MAX7456 | Stable |

### STM32F745 (216 MHz, 1 MB Flash, 320 KB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| Matek F765-WSE | STM32F745VGT6 | ICM-42688-P | MAX7456 | Beta |

### STM32H743 (480 MHz, 2 MB Flash, 1 MB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| SpeedyBee F405 V4 (H7) | STM32H743VIT6 | BMI270 | MAX7456 | Beta |
| Matek H743-SLIM | STM32H743VIT6 | ICM-42688-P | MAX7456 | Beta |

### AT32F435 (288 MHz, 4 MB Flash, 512 KB RAM)

| Board | MCU | Gyro | OSD | Status |
|-------|-----|------|-----|--------|
| iFlight Blitz F4 F435 | AT32F435CGU7 | BMI270 | MAX7456 | Beta |

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Stable** | Fully tested, ready for flight |
| **Beta** | Functional but still undergoing testing — fly with caution |
| **Alpha** | Basic support, not yet recommended for flight |

## Supported Sensors

### Gyroscopes / IMUs
- **InvenSense MPU6000** — SPI, 8 kHz sampling
- **Bosch BMI270** — SPI, 6.4 kHz sampling (with config blob upload)
- **TDK ICM-42688-P** — SPI, 32 kHz sampling
- **InvenSense ICM-20689** — SPI, 8 kHz sampling

### OSD Chips
- **MAX7456** — SPI, PAL/NTSC auto-detect
- **AT7456E** — MAX7456-compatible clone

### GPS Modules
- **u-blox M8/M9/M10** — UBX binary protocol over UART

### VTX Control
- **SmartAudio v1/v2** — Single-wire UART
- **Tramp IRC** — UART half-duplex

### RC Protocols
- **CRSF / ELRS** — UART, bidirectional telemetry
- **S.BUS** — Inverted UART

### Motor Protocols
- **DShot150** — Digital, bidirectional telemetry capable
- **DShot300** — Digital, bidirectional telemetry capable
- **DShot600** — Digital, bidirectional telemetry capable

## Adding a New Board

If your board isn't listed, you can request support:

1. Open an [Issue](https://github.com/AutomataNexus/NexusFlight-Suite/issues/new) with:
   - Board name and manufacturer
   - MCU model
   - Gyro/IMU model
   - Link to the board's pinout diagram or schematic
2. Or [request source access](#request-source-access) and submit a board definition PR

Board definitions are Rust structs mapping MCU pins to peripherals — typically 30-50 lines of code.

## Minimum Hardware Requirements

| Component | Requirement |
|-----------|-------------|
| MCU | ARM Cortex-M4F or higher, 100+ MHz, 512+ KB Flash |
| Gyro | SPI-connected 6-axis IMU (3-axis gyro + 3-axis accel) |
| Flash | (Optional) SPI dataflash for blackbox logging |
| OSD | (Optional) MAX7456-compatible chip |
| USB | USB-FS or USB-OTG for configuration and firmware updates |
