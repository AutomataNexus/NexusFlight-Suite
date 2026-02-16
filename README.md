<p align="center">
  <img src="assets/logo.png" alt="NexusFlight Logo" width="280" />
</p>

<h1 align="center">NexusFlight Suite</h1>

<p align="center">
  <strong>Next-generation open-source flight controller ecosystem — written in Rust</strong>
</p>

<p align="center">
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/releases"><img src="https://img.shields.io/github/v/release/AutomataNexus/NexusFlight-Suite?style=for-the-badge&color=0078D4&label=Latest%20Release&logo=github" alt="Latest Release"></a>
  &nbsp;
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/releases"><img src="https://img.shields.io/github/downloads/AutomataNexus/NexusFlight-Suite/total?style=for-the-badge&color=2ea44f&label=Downloads&logo=download" alt="Downloads"></a>
  &nbsp;
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-blue?style=for-the-badge&logo=gnu" alt="License"></a>
</p>

<p align="center">
  <a href="https://automatanexus.com"><img src="https://img.shields.io/badge/AutomataNexus.com-FF6B00?style=for-the-badge&logo=firefox&logoColor=white" alt="Website"></a>
  &nbsp;
  <img src="https://img.shields.io/badge/Language-Rust-DEA584?style=for-the-badge&logo=rust&logoColor=white" alt="Rust">
  &nbsp;
  <img src="https://img.shields.io/badge/Platform-STM32%20%7C%20AT32-47848F?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="Platform">
  &nbsp;
  <img src="https://img.shields.io/badge/Tests-150%20Passing-2ea44f?style=for-the-badge&logo=checkmarx&logoColor=white" alt="Tests">
  &nbsp;
  <a href="#request-source-access"><img src="https://img.shields.io/badge/Source-Request%20Access-7C3AED?style=for-the-badge&logo=key&logoColor=white" alt="Source Access"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/NexusFlight-v0.1.0-0078D4?style=flat-square&logo=drone&logoColor=white" alt="NexusFlight v0.1.0">
  &nbsp;
  <img src="https://img.shields.io/badge/CoreDrive_FOC-v0.1.0-E34F26?style=flat-square&logo=hackthebox&logoColor=white" alt="CoreDrive v0.1.0">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusGround-v0.1.0-47848F?style=flat-square&logo=tauri&logoColor=white" alt="NexusGround v0.1.0">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusCore-v0.1.0-DEA584?style=flat-square&logo=rust&logoColor=white" alt="NexusCore v0.1.0">
  &nbsp;
  <img src="https://img.shields.io/badge/Boards-27%20Supported-2ea44f?style=flat-square" alt="27 Boards">
</p>

<br/>

<p align="center">
  <a href="#downloads">Downloads</a> &nbsp;&bull;&nbsp;
  <a href="#nexusflight-firmware">Firmware</a> &nbsp;&bull;&nbsp;
  <a href="#coredrive-esc-firmware">CoreDrive ESC</a> &nbsp;&bull;&nbsp;
  <a href="#nexusground-configurator">Ground Station</a> &nbsp;&bull;&nbsp;
  <a href="#nexuscore-library">Core Library</a> &nbsp;&bull;&nbsp;
  <a href="docs/GETTING_STARTED.md">Getting Started</a> &nbsp;&bull;&nbsp;
  <a href="docs/SUPPORTED_HARDWARE.md">Supported Hardware</a> &nbsp;&bull;&nbsp;
  <a href="https://automatanexus.com">AutomataNexus.com</a>
</p>

---

## What is NexusFlight?

**NexusFlight Suite** is a complete flight controller ecosystem built from the ground up in **Rust** — delivering memory safety, real-time performance, and modern tooling to the FPV and drone community.

The suite consists of four components:

| Component | Description | Status |
|-----------|-------------|--------|
| **NexusFlight** | Embedded flight controller firmware for STM32/AT32 MCUs | v0.1.0 |
| **CoreDrive** | FOC (Field-Oriented Control) ESC firmware for BLDC motors | v0.1.0 |
| **NexusGround** | Desktop configurator app (Windows, Linux) | v0.1.0 |
| **NexusCore** | Core flight algorithms library (`no_std`, embeddable) | v0.1.0 |

---

## Downloads

### NexusGround (Configurator)

The desktop app for configuring your flight controller — PID tuning, rates, receiver setup, OSD, VTX, blackbox, firmware flashing, and more.

| Platform | Download | Size |
|----------|----------|------|
| **Windows 10/11** (x64) | [NexusGround_0.1.0_x64-setup.exe](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.1.0/NexusGround_0.1.0_x64-setup.exe) | ~19 MB |
| **Linux** (.deb — Ubuntu/Debian) | [NexusGround_0.1.0_amd64.deb](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.1.0/NexusGround_0.1.0_amd64.deb) | ~20 MB |
| **Linux** (.rpm — Fedora/RHEL) | [NexusGround-0.1.0-1.x86_64.rpm](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.1.0/NexusGround-0.1.0-1.x86_64.rpm) | ~20 MB |
| **Linux** (.AppImage — Universal) | [NexusGround_0.1.0_amd64.AppImage](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.1.0/NexusGround_0.1.0_amd64.AppImage) | ~88 MB |

> **Note:** macOS builds are coming soon. For now, macOS users can build from source — see [Building from Source](docs/BUILDING.md).

### NexusFlight (Firmware)

Pre-built firmware binaries for supported flight controllers. Flash directly via NexusGround's built-in firmware flasher.

| Board Family | MCU | Download |
|-------------|-----|----------|
| STM32F405 boards | STM32F405RGT6 | [nexusflight-stm32f405.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.1.0/nexusflight-stm32f405.bin) |
| STM32F411 boards | STM32F411CEU6 | [nexusflight-stm32f411.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.1.0/nexusflight-stm32f411.bin) |
| STM32F722 boards | STM32F722RET6 | [nexusflight-stm32f722.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.1.0/nexusflight-stm32f722.bin) |

> **Full board list:** See [Supported Hardware](docs/SUPPORTED_HARDWARE.md) for all 27 supported boards.

### NexusCore (Library)

The core flight algorithms as a standalone Rust crate — `no_std` compatible, usable in your own projects.

```toml
# Cargo.toml — available upon source access request
[dependencies]
nexus-core = { git = "https://github.com/AutomataNexus/NexusFlight.git", branch = "main" }
```

| Asset | Download |
|-------|----------|
| Source documentation | [API Reference](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexuscore-v0.1.0/nexus-core-docs.tar.gz) |

---

## Features

### NexusFlight Firmware

- **Pure Rust** — No C dependencies, memory-safe by default
- **Embassy async runtime** — Cooperative multitasking with zero-cost abstractions
- **Advanced PID controller** — Feed-forward, I-term relax, anti-gravity, TPA
- **Sensor fusion** — Complementary AHRS with configurable filter chains (PT1, PT2, Biquad, Notch, Dynamic Notch with FFT)
- **Protocol support** — MSP v2, CRSF/ELRS, S.BUS, DShot (150/300/600), SmartAudio, Tramp IRC
- **Bidirectional DShot** — Real-time eRPM telemetry via GCR decoding, RPM-driven dynamic notch filters
- **OSD** — MAX7456 DisplayPort with configurable element layout
- **GPS** — u-blox UBX binary protocol with GPS Rescue failsafe
- **Blackbox** — Onboard dataflash logging with delta compression
- **Safety** — Arming checks, failsafe, launch control, turtle mode (flip-over-after-crash)

### CoreDrive ESC Firmware

- **Field-Oriented Control (FOC)** — Sinusoidal commutation with D-Q axis decomposition for smoother, more efficient motor control
- **Dual control modes** — Switch between Six-Step (trapezoidal) and FOC per ESC
- **FOC tuning** — Independent D-axis (flux) and Q-axis (torque) PI controllers with configurable Kp/Ki gains
- **Sensorless rotor estimation** — Back-EMF observer with configurable gain, motor resistance, and inductance compensation
- **Configurable startup** — Listen → align → ramp pipeline with anti-stall recovery, configurable eRPM ramp rates
- **Protection suite** — Over-current, over-temperature, under-voltage, desync detection, stall timeout
- **3D mode** — Bidirectional motor control for inverted/acrobatic flight
- **Extended DShot Telemetry (EDT)** — Real-time eRPM, temperature, current, and voltage per ESC
- **4-way passthrough** — Configure individual ESCs through the flight controller via MSP
- **Flexible PWM** — 24, 48, or 96 kHz switching frequency, 0-30° timing advance

### NexusGround Configurator

- **14 configuration tabs** — Setup, Firmware, PID, Rates, Receiver, Motors, Gyro/Filters, OSD, VTX, GPS, Blackbox, CLI, ESC/CoreDrive
- **ESC/CoreDrive tab** — Per-motor detection, FOC tuning panel (D/Q-axis PID gains, motor model parameters, observer gain), protection thresholds, startup sequence editor
- **Built-in firmware flasher** — Build from source or flash pre-built .bin via AN3155 bootloader protocol
- **Config backup** — Automatic configuration backup to Aegis-DB before flashing
- **Cross-platform** — Windows and Linux (macOS coming soon)
- **Modern UI** — Dark/light theme, real-time data display
- **Built with Tauri 2** — Native performance, small footprint

### NexusCore Library

- **`no_std` compatible** — Runs on bare metal, WASM, or desktop
- **490+ unit tests** — Comprehensive test coverage
- **Modular** — Use only the algorithms you need (PID, AHRS, filters, RC, MSP, etc.)
- **Benchmarked** — Performance-critical paths benchmarked with Criterion

---

## Supported Hardware

NexusFlight supports **27 flight controller boards** across multiple MCU families:

| MCU Family | Boards | Status |
|------------|--------|--------|
| **STM32F405** | Matek F405-SE, SpeedyBee F405 V3/V4, iFlight SucceX-E F4, and more | Stable |
| **STM32F411** | SpeedyBee F405 Mini, BetaFPV F4 1S 12A AIO, and more | Stable |
| **STM32F722** | Matek F722-SE, SpeedyBee F7 V3, JHEMCU GF30F722-AIO, and more | Stable |
| **STM32F745** | Matek F765-WSE | Beta |
| **STM32H743** | SpeedyBee F405 V4, Matek H743-SLIM | Beta |
| **AT32F435** | iFlight Blitz F4 F435 | Beta |

> See [docs/SUPPORTED_HARDWARE.md](docs/SUPPORTED_HARDWARE.md) for the full board list with pinouts and features.

---

## Quick Start

### 1. Install NexusGround

Download the installer for your platform from the [Releases](https://github.com/AutomataNexus/NexusFlight-Suite/releases) page, or use the direct links above.

### 2. Connect Your Flight Controller

Plug in your FC via USB. NexusGround will auto-detect the board, MCU, and current firmware version.

### 3. Flash NexusFlight Firmware

Use the **Firmware** tab in NexusGround:
1. Select your board (auto-detected or manual)
2. Click **Build from Source** or browse a pre-built `.bin`
3. Click **Backup Config & Prepare Flash**
4. Enter bootloader mode (hold BOOT + plug USB)
5. Click **Detect & Flash**

### 4. Configure

Use the configurator tabs to tune PIDs, set rates, configure your receiver, OSD, VTX, and more.

> See [docs/GETTING_STARTED.md](docs/GETTING_STARTED.md) for a detailed walkthrough.

---

## Architecture

```
NexusFlight Suite
├── NexusFlight (FC Firmware)
│   ├── nexus-core ........... Flight algorithms (PID, AHRS, filters, MSP, GPS, OSD, VTX)
│   ├── nexus-hal ............ Hardware abstraction (SPI, I2C, UART, DMA, ADC, timers)
│   ├── nexus-drivers ........ Device drivers (BMI270, ICM-42688, MAX7456, CRSF, DShot)
│   ├── nexus-board .......... Board definitions and pin mappings
│   └── targets/ ............. MCU-specific entry points (STM32F4, STM32F7, SITL)
│
├── CoreDrive (ESC Firmware)
│   ├── coredrive-core ....... FOC engine, six-step, motor model, protection
│   └── coredrive-passthrough  4-way interface protocol for ESC configuration
│
├── NexusGround (Configurator)
│   ├── src/ ................. React + TypeScript frontend (14 tabs incl. FOC tuning)
│   ├── src-tauri/ ........... Rust backend (MSP bridge, serial, flasher, ESC passthrough)
│   └── e2e/ ................. End-to-end test suite
│
└── Aegis-DB ................. Configuration database (backup/restore/profiles)
```

---

## Request Source Access

The NexusFlight source code is maintained in private repositories. We welcome contributors, hardware partners, and community members who want to get involved.

**To request access:**

1. Visit [AutomataNexus.com](https://automatanexus.com) and reach out via the contact form
2. Email us at **devops@automatanexus.com** with:
   - Your GitHub username
   - What you'd like to contribute (firmware, drivers, ground station, docs, testing)
   - Your experience with flight controllers or embedded Rust
3. Open an [Issue](https://github.com/AutomataNexus/NexusFlight-Suite/issues/new?template=source-access.md) in this repo using the "Source Access Request" template

We typically respond within 48 hours.

---

## Community

- **Website:** [AutomataNexus.com](https://automatanexus.com)
- **Email:** devops@automatanexus.com
- **Issues & Requests:** [GitHub Issues](https://github.com/AutomataNexus/NexusFlight-Suite/issues)

---

## License

NexusFlight Suite is licensed under the **GNU General Public License v3.0**. See [LICENSE](LICENSE) for details.

The NexusCore library may be used under GPLv3 in your own projects. Commercial licensing is available — contact us at [AutomataNexus.com](https://automatanexus.com).

---

<p align="center">
  <strong>Built with Rust. Built for flight.</strong><br/>
  <a href="https://automatanexus.com">AutomataNexus.com</a>
</p>
