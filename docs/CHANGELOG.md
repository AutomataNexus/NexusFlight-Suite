# Changelog

All notable changes to NexusFlight Suite will be documented in this file.

## [0.1.0] — 2026-02-16

### NexusFlight Firmware v0.1.0

**Initial release.**

- PID controller with feed-forward, I-term relax, anti-gravity, and TPA
- AHRS sensor fusion (complementary filter)
- Filter chain: PT1, PT2, Biquad, Notch, Dynamic Notch (FFT and RPM-based)
- MSP v2 protocol for configuration
- CRSF / ELRS receiver support with bidirectional telemetry
- S.BUS receiver support
- DShot 150/300/600 motor output with bidirectional telemetry (eRPM via GCR)
- BMI270, ICM-42688-P, MPU6000, ICM-20689 gyro/accel drivers
- MAX7456 OSD with configurable element layout
- SmartAudio v1/v2 and Tramp IRC VTX control
- u-blox GPS (UBX binary protocol) with GPS Rescue
- Blackbox logging to onboard dataflash with delta compression
- Arming checks, failsafe, launch control, turtle mode
- Battery voltage/current monitoring
- LED strip control (WS2812)
- CLI for advanced configuration
- 27 supported boards across STM32F4/F7/H7 and AT32F435

### CoreDrive ESC Firmware v0.1.0

**Initial release — Field-Oriented Control for BLDC motor ESCs.**

- **Dual control modes:** Six-Step (trapezoidal) and FOC (sinusoidal) — switchable per ESC
- **FOC engine:** D-Q axis decomposition with independent PI controllers
  - D-axis (direct/flux) Kp/Ki tuning
  - Q-axis (quadrature/torque) Kp/Ki tuning
  - Motor resistance and inductance compensation
  - Back-EMF sensorless observer for rotor position estimation
- **Startup sequence:** Configurable listen → align → ramp pipeline with recovery and anti-stall
- **Protection systems:** Over-current, over-temperature, under-voltage, desync detection, stall timeout
- **Motor configuration:** Direction, timing advance (0-30°), PWM frequency (24/48/96 kHz), pole pairs
- **3D mode:** Bidirectional motor control for acrobatic flight
- **Extended DShot Telemetry (EDT):** Real-time eRPM, temperature, current, voltage per ESC
- **4-way passthrough:** Configure individual ESCs through the flight controller via MSP

### NexusGround v0.1.0

**Initial release.**

- 14 configuration tabs: Setup, Firmware, PID Tuning, Rates, Receiver, Motors, Gyro/Filters, OSD, VTX, GPS, Blackbox, CLI, ESC/CoreDrive
- **ESC/CoreDrive tab:** Per-motor detection, FOC tuning panel (D/Q-axis PID, motor model parameters, observer gain), protection thresholds, startup sequence config
- Built-in firmware flasher with AN3155 bootloader protocol
- Build-from-source workflow (compiles firmware for your board)
- Pre-built .bin flashing via file browser
- Automatic config backup to Aegis-DB before flashing
- Real-time MSP communication over serial
- 27-board database with auto-detection
- Dark and light theme with persistence
- Profile management (save/load/switch configurations)
- Windows (NSIS installer) and Linux (.deb, .rpm, .AppImage) packages
- 150 automated tests (58 frontend + 49 backend + 43 E2E)

### NexusCore v0.1.0

**Initial release.**

- `no_std` compatible core flight algorithms library
- PID controller, AHRS, filter chains, RC command processing
- MSP v2 codec and command handler (including 4-way ESC passthrough protocol)
- DShot frame encoding/decoding with bidirectional GCR telemetry
- Dynamic notch filters driven by motor RPM telemetry
- GPS UBX parser and GPS Rescue
- OSD layout engine and DisplayPort protocol
- VTX SmartAudio and Tramp protocol implementations
- Blackbox frame encoding with delta compression
- Failsafe state machine
- Flight mode management
- 354 unit tests with benchmarks
