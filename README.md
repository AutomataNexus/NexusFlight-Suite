<p align="center">
  <img src="assets/logo.png" alt="NexusFlight Logo" width="280" />
</p>

<h1 align="center">NexusFlight Suite</h1>

<p align="center">
  <strong>The first flight controller ecosystem with integrated Field-Oriented Control ESC firmware — written entirely in Rust</strong>
</p>

<p align="center">
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/releases"><img src="https://img.shields.io/github/v/release/AutomataNexus/NexusFlight-Suite?style=for-the-badge&color=0078D4&label=Latest%20Release&logo=github" alt="Latest Release"></a>
  &nbsp;
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/releases"><img src="https://img.shields.io/github/downloads/AutomataNexus/NexusFlight-Suite/total?style=for-the-badge&color=2ea44f&label=Downloads&logo=download" alt="Downloads"></a>
  &nbsp;
  <a href="https://github.com/AutomataNexus/NexusFlight-Suite/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-blue?style=for-the-badge&logo=gnu" alt="License"></a>
</p>

<p align="center">
  <a href="https://NexusFlight.AutomataNexus.com"><img src="https://img.shields.io/badge/NexusFlight.AutomataNexus.com-FF6B00?style=for-the-badge&logo=firefox&logoColor=white" alt="Website"></a>
  &nbsp;
  <img src="https://img.shields.io/badge/Language-Rust-DEA584?style=for-the-badge&logo=rust&logoColor=white" alt="Rust">
  &nbsp;
  <img src="https://img.shields.io/badge/Platform-STM32%20%7C%20AT32-47848F?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="Platform">
  &nbsp;
  <img src="https://img.shields.io/badge/Tests-917%20Passing-2ea44f?style=for-the-badge&logo=checkmarx&logoColor=white" alt="Tests">
  &nbsp;
  <a href="#request-source-access"><img src="https://img.shields.io/badge/Source-Request%20Access-7C3AED?style=for-the-badge&logo=key&logoColor=white" alt="Source Access"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/NexusFlight-v0.3.2-0078D4?style=flat-square&logo=drone&logoColor=white" alt="NexusFlight v0.3.2">
  &nbsp;
  <img src="https://img.shields.io/badge/CoreDrive_FOC-v0.3.2-E34F26?style=flat-square&logo=hackthebox&logoColor=white" alt="CoreDrive v0.3.2">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusGround-v0.3.2-47848F?style=flat-square&logo=tauri&logoColor=white" alt="NexusGround v0.3.2">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusCore-v0.3.2-DEA584?style=flat-square&logo=rust&logoColor=white" alt="NexusCore v0.3.2">
  &nbsp;
  <img src="https://img.shields.io/badge/FC_Boards-27-2ea44f?style=flat-square" alt="27 FC Boards">
  &nbsp;
  <img src="https://img.shields.io/badge/ESC_Targets-245-2ea44f?style=flat-square" alt="245 ESC Targets">
</p>

<br/>

<p align="center">
  <a href="#-coredrive--field-oriented-control">FOC ESC</a> &nbsp;&bull;&nbsp;
  <a href="#downloads">Downloads</a> &nbsp;&bull;&nbsp;
  <a href="#nexusflight-firmware">Firmware</a> &nbsp;&bull;&nbsp;
  <a href="#nexusground-configurator">Configurator</a> &nbsp;&bull;&nbsp;
  <a href="#nexuscore-library">Core Library</a> &nbsp;&bull;&nbsp;
  <a href="docs/GETTING_STARTED.md">Getting Started</a> &nbsp;&bull;&nbsp;
  <a href="docs/SUPPORTED_HARDWARE.md">Hardware</a> &nbsp;&bull;&nbsp;
  <a href="https://NexusFlight.AutomataNexus.com">Website</a>
</p>

---

## Why NexusFlight?

Every existing flight controller firmware — Betaflight, iNav, ArduPilot — treats the ESC as a black box. You flash the FC firmware, you flash the ESC firmware, and you hope they play nice together. The FC sends throttle commands over DShot and that's where its control ends.

**NexusFlight breaks that wall down.**

NexusFlight Suite is the first and only flight controller ecosystem that ships **integrated FOC (Field-Oriented Control) ESC firmware** alongside the FC firmware — both written in Rust, both configured from the same app, both designed to work as one system. The flight controller doesn't just send throttle percentages; it understands the motor model, tunes the FOC loop, and reads real-time telemetry from every phase of motor commutation.

No other flight controller software does this.

---

## What Sets NexusFlight Apart

NexusFlight goes beyond matching Betaflight feature-for-feature. These are capabilities that no other open-source flight controller firmware offers:

| Feature | Betaflight | NexusFlight |
|---------|-----------|-------------|
| **Gyro filtering** | Fixed-coefficient biquad chain | **Adaptive Kalman filter** — adjusts trust between prediction and measurement based on actual noise levels. ~50% less phase lag at equivalent noise rejection. |
| **Rate controller** | PID only | **ADRC (Active Disturbance Rejection Control)** — Extended State Observer estimates and cancels total disturbance (wind, prop wash, weight changes) in real-time. One tuning parameter instead of four. Same technology as DJI flight controllers. |
| **Gain scheduling** | TPA (linear D-term attenuation) | **Model-based gain scheduling** — scales all PID terms using thrust model curves and battery voltage compensation. Handles the full flight envelope. |
| **Cross-axis coupling** | None | **Gyroscopic decoupling feedforward** — pre-compensates precession torques during yaw maneuvers. |
| **Auto-tune** | Relay-based (Ziegler-Nichols oscillation) | **Frequency-domain system identification** — estimates plant transfer function from normal flight data via Welch's method. No deliberate oscillation needed. |
| **Navigation** | None (that's iNav) | **9-state EKF** — GPS-IMU fusion with wind estimation, position hold, waypoint missions, wind-aware RTH. |
| **ESC integration** | DShot throttle commands | **Integrated FOC ESC firmware** — sinusoidal commutation, shared motor model, unified configuration. |
| **Debug telemetry** | Limited | **Live 20Hz debug stream** — gyro, PID terms, motors, attitude, CPU, battery, 4 debug channels with real-time SVG charts in the configurator. |

---

## CoreDrive — Field-Oriented Control

<p align="center">
  <img src="https://img.shields.io/badge/INDUSTRY_FIRST-Integrated%20FOC%20ESC%20in%20a%20Flight%20Controller%20Suite-E34F26?style=for-the-badge" alt="Industry First">
</p>

**CoreDrive** is a from-scratch BLDC motor ESC firmware with a full **Field-Oriented Control** engine. While traditional ESC firmware (BLHeli_32, BLHeli_S, AM32) uses trapezoidal six-step commutation, CoreDrive implements true **sinusoidal FOC** — the same control strategy used in industrial servo drives and high-performance robotics.

### What FOC Means for FPV

| | Traditional Six-Step | CoreDrive FOC |
|---|---|---|
| **Commutation** | 6 discrete steps per electrical revolution | Continuous sinusoidal — infinite resolution |
| **Torque ripple** | High — causes vibration and noise | Near-zero — smoother motor, cleaner gyro signal |
| **Efficiency** | ~85% typical | ~92-95% — less heat, longer flight times |
| **Low-throttle control** | Coarse, jittery | Precise and linear — better authority on micro quads |
| **Noise** | Audible commutation whine | Near-silent operation |
| **Startup** | Can stutter or desync | Controlled align, ramp with stall recovery |

### How It Works

CoreDrive decomposes motor current into two orthogonal axes using the **Park and Clarke transforms**:

- **D-axis (Direct)** — Controls magnetic flux. Held at zero for maximum torque-per-amp efficiency.
- **Q-axis (Quadrature)** — Controls torque. This is where your throttle command goes.

Each axis has its own **PI controller** with independently tunable Kp/Ki gains. A **sensorless back-EMF observer** estimates rotor position in real time — no hall sensors or encoders needed, just the three motor wires you already have.

### FOC Features

- **D-Q axis PI controllers** — Independent Kp/Ki gains for flux (D) and torque (Q) control
- **Motor model parameters** — Configure winding resistance, inductance, and observer gain for your specific motor
- **Sensorless rotor estimation** — Back-EMF observer tracks rotor position without hall sensors or encoders
- **Switchable control modes** — Toggle between FOC and Six-Step per ESC from NexusGround, fly on either
- **Configurable startup sequence** — Listen duration, alignment hold, eRPM ramp rate, stall recovery with cooldown
- **Full protection suite** — Over-current (mA), over-temperature, under-voltage (mV), commutation desync, stall timeout
- **3D / bidirectional mode** — Smooth FOC control in both motor directions for inverted flight
- **PWM flexibility** — 24, 48, or 96 kHz switching frequency with 0-30° timing advance
- **Extended DShot Telemetry** — eRPM, ESC temperature, current draw, and voltage per motor in real time
- **4-way passthrough** — Configure each ESC individually through the FC, no direct ESC connection needed
- **Integrated tuning** — Tune FOC parameters from NexusGround's ESC/CoreDrive tab with live motor detection

### FOC + NexusFlight = Tighter Loop

Because the FC and ESC firmware are designed together:

- The FC reads motor eRPM via bidirectional DShot and feeds it directly into **RPM-based dynamic notch filters** — eliminating motor vibration harmonics from the gyro signal before they reach the PID loop
- Motor model parameters (resistance, inductance, pole pairs) are shared between the FOC observer and the FC's telemetry system
- Configuration backup captures both FC and ESC settings to Aegis-DB in one operation
- One configurator app (NexusGround) tunes both the flight PID loop and the motor FOC loop

---

## Downloads

### NexusGround (Configurator)

The desktop app for configuring your flight controller and ESCs — PID tuning, FOC tuning, rates, receiver setup, OSD, VTX, blackbox, firmware flashing, auto-tune, live debug telemetry, and more.

| Platform | Download | Size |
|----------|----------|------|
| **Windows 10/11** (x64) | [NexusGround_0.3.2_x64-setup.exe](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.3.2/NexusGround_0.3.2_x64-setup.exe) | ~19 MB |
| **Linux** (.deb — Ubuntu/Debian) | [NexusGround_0.3.2_amd64.deb](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.3.2/NexusGround_0.3.2_amd64.deb) | ~20 MB |
| **Linux** (.rpm — Fedora/RHEL) | [NexusGround-0.3.2-1.x86_64.rpm](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.3.2/NexusGround-0.3.2-1.x86_64.rpm) | ~20 MB |
| **Linux** (.AppImage — Universal) | [NexusGround_0.3.2_amd64.AppImage](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.3.2/NexusGround_0.3.2_amd64.AppImage) | ~88 MB |

> **Note:** macOS builds are coming soon. For now, macOS users can build from source — see [Building from Source](docs/BUILDING.md).

### NexusFlight Firmware (v0.3.2)

Pre-built firmware binaries for supported flight controllers. Flash directly via NexusGround's built-in firmware flasher.

| Board Family | MCU | Download |
|-------------|-----|----------|
| STM32F405 boards | STM32F405RGT6 (168 MHz Cortex-M4F) | [nexusflight_stm32f405.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.3.2/nexusflight_stm32f405.bin) |
| STM32F411 boards | STM32F411CEU6 (100 MHz Cortex-M4F) | [nexusflight_stm32f411.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.3.2/nexusflight_stm32f411.bin) |
| STM32F7 boards | STM32F745/F722 (216 MHz Cortex-M7F) | [nexusflight_stm32f7.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.3.2/nexusflight_stm32f7.bin) |
| STM32G4 boards | STM32G473/G431 (170 MHz Cortex-M4F) | [nexusflight_stm32g4.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.3.2/nexusflight_stm32g4.bin) |
| STM32H7 boards | STM32H743/H723 (480 MHz Cortex-M7F) | [nexusflight_stm32h7.bin](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusflight-v0.3.2/nexusflight_stm32h7.bin) |

> **Full board list:** See [Supported Hardware](docs/SUPPORTED_HARDWARE.md) for all 27 supported boards across 6 MCU families.

### NexusCore (Library)

The core flight algorithms as a standalone Rust crate — `no_std` compatible, usable in your own projects.

```toml
# Cargo.toml — available upon source access request
[dependencies]
nexus-core = { git = "https://github.com/AutomataNexus/NexusFlight.git", branch = "main" }
```

| Asset | Download |
|-------|----------|
| Source documentation | [API Reference](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexuscore-v0.3.2/nexus-core-docs.tar.gz) |

---

## The Suite

### NexusFlight Firmware

**Core Flight Stack:**
- **Pure Rust** — No C dependencies, memory-safe by default
- **Embassy async runtime** — Cooperative multitasking with zero-cost state machines on a single stack
- **7 flight modes** — Acro, Angle, Horizon, Position Hold, Waypoint Mission, Turtle (flip-over-after-crash), Launch Control
- **Protocol support** — MSP v2, CRSF/ELRS, S.BUS, DShot (150/300/600), SmartAudio, Tramp IRC, UBX GPS
- **Bidirectional DShot** — Real-time eRPM telemetry via GCR decoding, RPM-driven dynamic notch filters
- **OSD** — MAX7456 analog + MSP DisplayPort digital (DJI/HDZero/Walksnail)
- **Blackbox** — 96-byte v3 frames with dual gyro (raw+filtered), separated PID terms, debug channels, delta compression
- **Safety** — Staged failsafe (hold, ramp, disarm), arming pre-checks, watchdog, stack guard, hard fault handler

**Advanced Control (beyond Betaflight):**
- **Adaptive Kalman gyro filter** — Per-axis 1D Kalman with adaptive measurement noise R. Replaces PT1+biquad lowpass chain. Less phase lag, better noise rejection.
- **ADRC rate controller** — Extended State Observer estimates total disturbance and cancels it. Roll/pitch ADRC with PID yaw hybrid mode. Single bandwidth parameter tunes all observer gains.
- **Cross-axis decoupling feedforward** — Pre-compensates gyroscopic precession during yaw maneuvers.
- **Model-based gain scheduling** — Thrust-curve-aware PID scaling (linear/sqrt/model-based) + battery voltage compensation. Replaces simple TPA.
- **Anti-gravity** — Throttle change rate detection with temporary I-term boost for punch response.
- **RC smoothing** — Auto-tuned PT1 filter that detects RC frame rate and sets cutoff at 2x.

**Navigation:**
- **9-state Extended Kalman Filter** — GPS-IMU sensor fusion: position (NED), velocity (NED), wind (NE), vertical accel bias
- **Position Hold** — Cascaded PID (position, velocity, lean angle) with heading rotation
- **Waypoint Mission** — Autonomous multi-point navigation state machine (transit, hold, RTH, landing)
- **GPS Rescue** — Wind-aware and battery-aware return-to-home via EKF or raw GPS fallback

**Sensor Fusion & Filtering:**
- **Mahony AHRS** — Complementary filter with gyro + accelerometer fusion for attitude estimation
- **256-point FFT** — Fixed-point radix-2 with peak detection for dynamic notch frequency identification
- **Dynamic notch** — FFT-based and RPM-based, auto-tracking motor noise harmonics
- **Configurable filter chain** — PT1, biquad lowpass, biquad notch, per-axis configuration

### NexusGround Configurator

- **15 configuration tabs** — Setup, Firmware Flasher, PID, Rates, Receiver, Motors, Gyro/Filters, OSD, VTX, GPS, Blackbox, CLI, ESC/CoreDrive, Auto-Tune, Debug
- **Frequency-domain auto-tune** — Load blackbox logs, system identification via Welch's method, Bode plot visualization, automatic PID gain design for target bandwidth/phase margin
- **Live debug telemetry** — 20Hz real-time streaming of gyro, PID output, motors, attitude, CPU load, battery, RSSI, and 4 debug channels with SVG time-series charts and scrolling log console
- **ESC/CoreDrive FOC tab** — Per-motor detection, D/Q-axis PID tuning, motor model parameters, protection thresholds, startup sequence editor
- **Built-in firmware flasher** — AN3155 UART bootloader protocol with chip auto-detection, automatic config backup before flash
- **Config profiles** — Save/load/compare full FC + ESC configurations via Aegis-DB
- **Toast notification system** — Real-time feedback on saves, errors, and warnings across all tabs
- **Cross-platform** — Windows (NSIS installer) and Linux (.deb, .rpm, .AppImage)
- **Light and dark themes** — Cream/teal/copper light theme (default) with dark toggle, persisted to DB
- **Built with Tauri 2** — React 19 + TypeScript + Vite frontend, Rust backend, native performance

### NexusCore Library

- **`no_std` compatible** — Runs on bare metal, WASM, or desktop
- **551 unit tests** — Comprehensive coverage across 36 modules
- **Modular** — Use only the algorithms you need (PID, ADRC, Kalman, AHRS, EKF, filters, RC, MSP, mixer, etc.)
- **Benchmarked** — Sub-10ns PID loop, ~1.8us FFT, ~54ns CRSF parse (Criterion benchmarks)
- **`serde` feature flag** — Optional serialization support for Tauri/WASM reuse
- **`#[repr(C)]` config** — Deterministic memory layout with CRC32 integrity for direct flash serialization

---

## Supported Hardware

NexusFlight supports **27 flight controller boards** across 6 MCU families:

| MCU Family | Clock | Boards | Status |
|------------|-------|--------|--------|
| **STM32F405** | 168 MHz | SpeedyBee F405 V3/V4/Mini/AIO/Wing, Happymodel SuperF405, Flywoo F405S AIO, GEPRC F405, Matek F405 Wing V2 | Stable |
| **STM32F411** | 100 MHz | BetaFPV F411, HDZero AIO5, Happymodel CrazyBee F4 DX | Stable |
| **STM32F722** | 216 MHz | Flywoo F722 Pro V2, GEPRC F722 AIO | Stable |
| **STM32G473** | 170 MHz | CrazyBee G473, BetaFPV G473, GEPRC Taker G473, HDZero Gamma 45A, HDZero AIO15 | Stable |
| **STM32H743** | 480 MHz | HDZero Halo, GEPRC Taker H743, Sequre H7 V1/V2, Matek H743, T-Motor Pacer H743, iFlight Blitz H7 Pro | Stable |
| **AT32F435** | 288 MHz | iFlight Blitz F4 F435 | Beta |

> See [docs/SUPPORTED_HARDWARE.md](docs/SUPPORTED_HARDWARE.md) for the full board list with pinouts and features.

### Supported Aircraft

| Frame | Motors | Recommended MCU | Gyro |
|-------|--------|----------------|------|
| 65mm whoop | 4 | F411 | BMI270 |
| 75mm whoop | 4 | F411 | BMI270 |
| 5" freestyle/racing | 4 | F405/F722/G473 | ICM-42688-P |
| 5" HD (digital VTX) | 4 | G473/H743 | ICM-42688-P |
| 7-8" long range | 4 | F405/F745/H743 | ICM-42688-P |

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

### 4. Configure Everything — FC and ESC — in One Place

Use the configurator tabs to tune PIDs, set rates, configure your receiver, OSD, VTX, and GPS modes. Open the **ESC/CoreDrive** tab to tune FOC parameters, set protection thresholds, and configure motor startup. Use the **Auto-Tune** tab to analyze blackbox logs and compute optimal PID gains. Monitor everything in real-time with the **Debug** tab.

> See [docs/GETTING_STARTED.md](docs/GETTING_STARTED.md) for a detailed walkthrough.

---

## Architecture

```
NexusFlight Suite
│
├── NexusFlight (FC Firmware) ............... v0.3.2
│   ├── nexus-core ........... Flight algorithms: PID, ADRC, Kalman, AHRS, EKF,
│   │                          filters, FFT, mixer, MSP, GPS, OSD, VTX, blackbox,
│   │                          navigation, waypoints, 36 modules, 458 tests
│   ├── nexus-hal ............ Hardware abstraction traits (gyro, motor, RC, serial,
│   │                          storage, ADC, watchdog, beeper, LED strip, servo)
│   ├── nexus-drivers ........ Device drivers: BMI270, ICM-42688-P, MAX7456, CRSF,
│   │                          SBUS, DShot, u-blox GPS, SPI flash, VTX, 84 tests
│   ├── nexus-board .......... Board definitions and pin mappings (27 boards)
│   └── targets/ ............. MCU-specific entry points
│       ├── stm32f4 .......... STM32F405 / F411 (Cortex-M4F)
│       ├── stm32f7 .......... STM32F745 / F722 (Cortex-M7F)
│       ├── stm32g4 .......... STM32G473 / G431 (Cortex-M4F, DMAMUX)
│       ├── stm32h7 .......... STM32H743 / H723 (Cortex-M7F, 480 MHz)
│       └── sitl ............. Software-In-The-Loop (host testing, 7 tests)
│
├── CoreDrive (FOC ESC Firmware) ............ v0.3.1, 366 tests
│   ├── coredrive-core ....... FOC engine (Clarke/Park/SVPWM), D-Q PI controllers,
│   │                          six-step commutation, sensorless SMO observer,
│   │                          startup FSM, protection, telemetry, autotune,
│   │                          Q15 fixed-point math, config serialization — 206 tests
│   ├── coredrive-dshot ...... DShot 150/300/600 + bidirectional EDT telemetry — 37 tests
│   ├── coredrive-hal ........ Hardware abstraction traits (ADC, PWM, GPIO, flash, serial)
│   ├── coredrive-board ...... 245 ESC board configs across 7 MCU families — 39 tests
│   ├── coredrive-passthrough  4-way passthrough protocol (CRC-16/XMODEM) — 23 tests
│   ├── coredrive-bootloader . AM32-compatible bootloader protocol — 20 tests
│   ├── coredrive-flasher .... PC-side firmware flasher (std, serialport) — 29 tests
│   └── targets/ ............. 4 MCU targets + 4 bootloaders
│       ├── stm32g0 .......... STM32G071 (Cortex-M0+, 64 MHz, FOC + six-step)
│       ├── at32f4 ........... AT32F421 (Cortex-M4, 120 MHz, FOC)
│       ├── stm32f0 .......... STM32F051 (Cortex-M0, 48 MHz, six-step)
│       └── gd32e2 ........... GD32E230 (Cortex-M23, 72 MHz, six-step)
│
├── NexusGround (Configurator) .............. v0.3.2
│   ├── src/ ................. React 19 + TypeScript + Vite (15 tabs)
│   ├── src-tauri/ ........... Rust backend: MSP bridge, serial, flasher, ESC passthrough,
│   │                          auto-tune (FFT system ID), board DB, Aegis-DB client
│   └── 917 tests ............ 551 NexusFlight/NexusCore + 366 CoreDrive across all crates
│
└── Aegis-DB ................. Configuration database (FC + ESC backup/restore/profiles)
```

### Performance

Hot-path benchmarks (Criterion, Cortex-M7 equivalent):

| Operation | Time |
|-----------|------|
| Full 3-axis PID loop + mixer + filters | ~9 ns |
| Single-axis PID (P+I+D+FF) | ~3 ns |
| 256-point FFT | ~1.8 us |
| Gyro filter chain (LP + notch + D-LP) | ~3.5 ns |
| CRSF RC frame parse | ~54 ns |
| DShot frame encode (per motor) | ~1.1 ns |
| MSP frame parse | ~73 ns |

---

## Request Source Access

The NexusFlight source code is maintained in private repositories. We welcome contributors, hardware partners, and community members who want to get involved.

**To request access:**

1. Visit [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com) and reach out via the contact form
2. Email us at **devops@automatanexus.com** with:
   - Your GitHub username
   - What you'd like to contribute (firmware, FOC/ESC, drivers, ground station, docs, testing)
   - Your experience with flight controllers, motor control, or embedded Rust
3. Open an [Issue](https://github.com/AutomataNexus/NexusFlight-Suite/issues/new?template=source-access.md) in this repo using the "Source Access Request" template

We typically respond within 48 hours.

---

## Community

- **Website:** [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com)
- **Email:** devops@automatanexus.com
- **Issues & Requests:** [GitHub Issues](https://github.com/AutomataNexus/NexusFlight-Suite/issues)

---

## License

NexusFlight Suite is licensed under the **GNU General Public License v3.0**. See [LICENSE](LICENSE) for details.

Commercial licensing is available — contact us at [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com).

---

<p align="center">
  <strong>Built with Rust. Built for flight. The only FC suite with integrated FOC.</strong><br/><br/>
  <a href="https://NexusFlight.AutomataNexus.com">NexusFlight.AutomataNexus.com</a>
</p>
