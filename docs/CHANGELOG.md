# Changelog

All notable changes to NexusFlight Suite will be documented in this file.

## [0.2.0 / 0.3.2] — 2026-02-18

### NexusFlight Firmware v0.3.2

**Major feature release — novel flight control algorithms and expanded MCU support.**

**New MCU Targets:**
- STM32G4 (STM32G473/G431) — 170 MHz Cortex-M4F, DMAMUX, page-based flash
- STM32H7 (STM32H743/H723) — 480 MHz Cortex-M7F, AXI SRAM DMA, D-cache management
- All four STM32 families now share identical flight pipeline and feature set

**Novel Control Algorithms (none of these exist in Betaflight):**
- **Adaptive Kalman gyro filter** — Per-axis 1D Kalman with adaptive measurement noise. Adjusts trust between prediction and measurement based on actual noise levels. Replaces PT1+biquad lowpass chain when enabled. ~50% less phase lag at equivalent noise rejection.
- **ADRC rate controller** — Active Disturbance Rejection Control with Extended State Observer. Estimates and cancels total disturbance (wind, prop wash, weight changes, motor nonlinearity) in real-time. Single bandwidth parameter vs. four PID gains. Roll/pitch ADRC + PID yaw hybrid mode supported.
- **Cross-axis decoupling feedforward** — Pre-compensates gyroscopic precession torques during yaw maneuvers. Yaw acceleration produces roll/pitch corrections.
- **Model-based gain scheduling** — Scales all PID terms using thrust model curves (linear/sqrt/model-based) and battery voltage compensation. Handles the full flight envelope instead of simple TPA.

**Navigation:**
- **9-state Extended Kalman Filter** — GPS-IMU fusion for position (NED), velocity (NED), wind (NE), vertical acceleration bias
- **Position Hold** — Cascaded PID controller (position → velocity → lean angle) with heading rotation
- **Waypoint Mission** — Autonomous multi-point navigation state machine (Idle → InTransit → Holding → RTH → Landing → Complete)
- **GPS Rescue rewrite** — Wind-aware and battery-aware return-to-home via EKF or raw GPS fallback
- **Two new flight modes**: PosHold, WaypointMission (total: 7 modes)

**Blackbox v3:**
- Expanded frame from 36 to 96 bytes
- Dual gyro recording (raw + filtered)
- Separated PID terms (P/I/D/FF per axis)
- Setpoint, sensor data (vbat, current, RSSI, CPU, loop time)
- 4 debug channels (auto-populated: Kalman gain, innovation, ESO disturbance, ESO error)

**Debug Telemetry:**
- New MSP commands: MSP_RAW_IMU (102), MSP_ATTITUDE (108), MSP_DEBUG (254), MSP_SENSOR_STATUS (0x1F20), MSP_DEBUG_STREAM (0x1F21)
- `FcStatus` shared between main loop and USB task via `Mutex<RefCell<FcStatus>>`
- Live CPU load, loop time, battery voltage, RSSI in telemetry stream

**Other:**
- PID controller returns separated `PidTerms { p, i, d, ff, total }` and `PidBankOutput`
- `RateController` enum: PID, ADRC, or hybrid (ADRC roll/pitch + PID yaw)
- CONFIG_VERSION bumped to 4 (auto-migration from v2/v3)
- HDZero VTX support wired in G4/H7 targets
- Flash region definitions for all 6 MCU variants
- 458 nexus-core tests (up from 354)
- 84 nexus-drivers tests (up from 81)

### NexusGround v0.3.2

**Major configurator update — auto-tune, debug telemetry, toast notifications.**

**New Tabs:**
- **Auto-Tune** — Frequency-domain system identification from blackbox logs. Welch's method (512-point FFT, 50% overlap, Hann window) estimates closed-loop transfer function. Extracts plant model, designs optimal PID gains for target bandwidth/phase margin. Bode plot + step response visualization.
- **Debug** — Live 20Hz debug telemetry stream. Four SVG mini-charts (gyro, PID output, motors, loop time/CPU). Status bar with battery/RSSI/debug channels. Scrolling log console with timestamped entries. Export to .log file.
- **Firmware Flasher** — AN3155 UART bootloader protocol with chip auto-detection, step-based workflow (select → backup → bootloader → flash), automatic config backup

**Toast Notification System:**
- Global `ToastProvider` with `useToast()` hook
- All 8 interactive tabs wired: PID, Rates, Motors, Gyro, Setup, ESC, AutoTune, FirmwareFlasher
- Success/error/warning levels with auto-dismiss

**Other:**
- 15 total tabs (up from 14)
- Version bump to 0.3.2 (from 0.3.1)
- New TypeScript types: DebugStream, RawImu, Attitude
- New hook methods: getDebugStream, getRawImu, getAttitude
- `rustfft` dependency added for auto-tune FFT

### NexusCore v0.3.2

- 4 new modules: kalman, adrc, cross_coupling, gain_schedule
- Navigation module: ekf, geo, pos_hold, waypoint
- PidTerms struct for separated PID component access
- RateController enum for PID/ADRC/hybrid switching
- Blackbox v3 frame (96 bytes) with expanded telemetry
- CONFIG_VERSION 4 with auto-migration
- 458 unit tests (up from 354)

---

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
- **Startup sequence:** Configurable listen, align, ramp pipeline with recovery and anti-stall
- **Protection systems:** Over-current, over-temperature, under-voltage, desync detection, stall timeout
- **Motor configuration:** Direction, timing advance (0-30 deg), PWM frequency (24/48/96 kHz), pole pairs
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
