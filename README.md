<p align="center">
  <img src="assets/brand/NexusFlightLogo.png" alt="NexusFlight Logo" width="720" />
</p>

<h1 align="center">NexusFlight Suite</h1>

<p align="center">
  <strong>A flight controller ecosystem built together with its own ESC firmware: NexusFlight FC firmware and CoreDrive ESC firmware, configured from one app, with in-flight AI tuning by Vireo, an Oxiryn-trained model</strong>
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
  <img src="https://img.shields.io/badge/Platform-STM32%20%7C%20AT32%20%7C%20EFM8-47848F?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="Platform">
  &nbsp;
  <img src="https://img.shields.io/badge/ML-Oxiryn-1F6FEB?style=for-the-badge" alt="Oxiryn">
  &nbsp;
  <img src="https://img.shields.io/badge/Status-In%20Testing-F5A623?style=for-the-badge" alt="Status: In Testing">
  &nbsp;
  <a href="#request-source-access"><img src="https://img.shields.io/badge/Source-Request%20Access-7C3AED?style=for-the-badge&logo=key&logoColor=white" alt="Source Access"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/NexusFlight-v0.3.3-0078D4?style=flat-square&logo=drone&logoColor=white" alt="NexusFlight v0.3.3">
  &nbsp;
  <img src="https://img.shields.io/badge/CoreDrive_FOC-v0.3.2-E34F26?style=flat-square&logo=hackthebox&logoColor=white" alt="CoreDrive v0.3.2">
  &nbsp;
  <img src="https://img.shields.io/badge/CoreDrive--8051-in%20development-E34F26?style=flat-square" alt="CoreDrive-8051 in development">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusGround-v0.4.3-47848F?style=flat-square&logo=tauri&logoColor=white" alt="NexusGround v0.4.3">
  &nbsp;
  <img src="https://img.shields.io/badge/NexusTune_AI-in%20review-8E44AD?style=flat-square" alt="NexusTune in review">
  &nbsp;
  <img src="https://img.shields.io/badge/Oxiryn-onboard-1F6FEB?style=flat-square" alt="Oxiryn onboard">
  &nbsp;
  <img src="https://img.shields.io/badge/Vireo_model-in%20training-1F6FEB?style=flat-square" alt="Vireo model in training">
  &nbsp;
  <img src="https://img.shields.io/badge/FC_Boards-29-2ea44f?style=flat-square" alt="29 FC Boards">
  &nbsp;
  <img src="https://img.shields.io/badge/ESC_Targets-245-2ea44f?style=flat-square" alt="245 ESC Targets">
  &nbsp;
  <img src="https://img.shields.io/badge/Host_Tests-900%2B-2ea44f?style=flat-square" alt="900+ host tests">
</p>

<br/>

<p align="center">
  <a href="#-currently-developing-betafpv-air65-ii">Currently Developing</a> &nbsp;&bull;&nbsp;
  <a href="#project-status">Status</a> &nbsp;&bull;&nbsp;
  <a href="#nexustune--in-flight-ai-tuning">NexusTune AI</a> &nbsp;&bull;&nbsp;
  <a href="#oxiryn--the-ml-framework-behind-nexustune">Oxiryn</a> &nbsp;&bull;&nbsp;
  <a href="#coredrive--field-oriented-control">FOC ESC</a> &nbsp;&bull;&nbsp;
  <a href="#downloads">Downloads</a> &nbsp;&bull;&nbsp;
  <a href="#nexusflight-firmware">Firmware</a> &nbsp;&bull;&nbsp;
  <a href="#nexusground-configurator">Configurator</a> &nbsp;&bull;&nbsp;
  <a href="#nexuscore-library">Core Library</a> &nbsp;&bull;&nbsp;
  <a href="docs/GETTING_STARTED.md">Getting Started</a> &nbsp;&bull;&nbsp;
  <a href="docs/SUPPORTED_HARDWARE.md">Hardware</a> &nbsp;&bull;&nbsp;
  <a href="https://NexusFlight.AutomataNexus.com">Website</a>
</p>

---

## 📌 Currently Developing: BETAFPV Air65 II

<p align="center">
  <img src="https://img.shields.io/badge/PINNED-Currently%20Developing-D73A49?style=for-the-badge" alt="Currently Developing">
  &nbsp;
  <img src="https://img.shields.io/badge/FC-STM32G473%2FG474-0078D4?style=for-the-badge" alt="FC STM32G473/G474">
  &nbsp;
  <img src="https://img.shields.io/badge/ESC-EFM8BB51-E34F26?style=for-the-badge" alt="ESC EFM8BB51">
</p>

> **This is the board the whole suite is being brought up on right now.** NexusFlight runs the flight controller, CoreDrive-8051 runs the four ESCs, NexusGround configures both, and NexusTune tunes it in the air. **None of it has flown yet.** The FC firmware for this board is in development and has only run in our boot simulator; CoreDrive-8051 has only run in our ESC simulator and has never been flashed to a real ESC. Do not flash either to your own Air65 II yet.

The Air65 II is a 65 mm 1S whoop. Its flight controller and ESCs sit on one AIO board, the **BETAFPV Matrix 1S 5IN1 II** (12A), which also carries the receiver, VTX and OSD. That makes it a complete test of NexusFlight's "FC and ESC as one system" idea on a single board.

### The flight controller: Matrix 1S 5IN1 II (`betafpv_g473_v2`)

| | |
|---|---|
| **Betaflight target** | `BETAFPVG473_V2` |
| **MCU** | STM32G473CEU6 per BETAFPV's target (our board reads back as an STM32G474), Cortex-M4F at 170 MHz, 8 MHz crystal |
| **Gyro** | Bosch **BMI270** on our board. BETAFPV ships this board with any of BMI270, ICM-42688-P, ICM-42622-P or LSM6DSK320X depending on batch, so NexusFlight detects the chip at boot and one image covers all four |
| **OSD** | AT7456E (MAX7456-compatible) analog OSD on SPI2 |
| **Receiver** | Onboard serial ExpressLRS 2.4 GHz (CRSF on USART3) |
| **VTX** | Onboard analog 5.8 GHz VTX, 25 / 100 / 200 / 400 mW, SmartAudio on USART2 |
| **Motors** | 4 outputs, all on TIM3 (PB0, PB1, PC6, PA4), DShot300 with bidirectional DShot |
| **NexusFlight target** | `betafpv_g473_v2`, a new target. Not the same as the first-revision `betafpv_g473` image, which uses different pins |

**What's done for it (host, simulator and boot-simulator tested only, nothing flashed):**

- Board pin map taken from Betaflight's target and checked against our own stock board's flash backup: pins, timers, UARTs and SPI buses match.
- Gyro auto-detection across all four chips, including a new LSM6DSK320X driver.
- Boot guard, early watchdog, HardFault reset and USB reboot-to-bootloader, so a bad image can't lock the board out of USB.
- Bidirectional DShot (eRPM per motor), SmartAudio VTX control using the board's own power table, and the AT7456E analog OSD.
- Flight-setup parity with the stock Betaflight config: Betaflight motor order, board alignment (the stock board is mounted at -135° yaw), props-out, Actual rates, Betaflight throttle curve, arming on any AUX range, and a built-in Air65 II default profile.
- The image starts cleanly in `tools/boot-sim`, our emulated STM32G473.

**Still to do before first flight:** angle and horizon modes, beeper, turtle mode, VTX pit-mode switch, RPM filter and dynamic notch wired into the loop, TPA and D-max. Then a props-off bench check of every motor and stick direction, and only then a first hover.

### The ESCs: CoreDrive-8051 on the onboard 12A ESCs

| | |
|---|---|
| **ESC** | 4 × 1S 12A, on the same Matrix 5IN1 II board |
| **ESC MCU** | Silicon Labs **EFM8BB51** (8051 core), one per motor |
| **Stock firmware** | Bluejay 0.19.2, layout tag `#A_X_05#`, 96 kHz PWM |
| **CoreDrive build** | **CoreDrive-8051**, layout **A_X_05**, matching the board |

- CoreDrive-8051 is CoreDrive for 8-bit ESCs: C (SDCC) with an 8051 assembly commutation core, built on the Bluejay six-step design and FC-compatible with it (DShot300/600, bidirectional DShot with extended telemetry, same settings layout).
- In our whole-board ESC simulator (`efm8sim`) it passes all 19 test scenarios on each of the five common layouts A to E, including standstill starts straight into 30% and 100% throttle.
- All four stock ESCs on our Air65 II have been backed up read-only through the flight controller, so the stock Bluejay image can be restored exactly.
- **Status: sim-tested only. Never flashed to a real ESC.**

**Next steps on this board:** first NexusFlight flash on one board (props off, VTX antenna on, stock firmware backed up), then a CoreDrive-8051 bench test on a single ESC, then first flights. The second Air65 II stays on stock firmware until the first one is proven.

---

## Project Status

> **NexusFlight is in testing. Beta releases are coming soon.**
>
> Every NexusFlight and CoreDrive target compiles and passes its host test suite, and start-up is checked in an emulator before an image is published. **No NexusFlight or CoreDrive build has flown yet.** Hardware bring-up is happening now, board by board, props off. Until a board is listed as hardware-verified, treat its firmware as experimental: keep a backup of the stock firmware, and do not fly it.

| Piece | Version | State |
|-------|---------|-------|
| NexusFlight FC firmware | v0.3.3 | 29 board targets build. Hardware bring-up in progress on the T-Motor F411 AIO and the BETAFPV Air65 II. |
| BETAFPV Air65 II (`betafpv_g473_v2`) | **currently developing** | New board target with gyro auto-detect, boot guard, bidirectional DShot, SmartAudio, OSD and Betaflight-compatible motor order and board alignment. Passes the boot simulator. Not yet flashed or flown. See [Currently Developing](#-currently-developing-betafpv-air65-ii). |
| CoreDrive FOC ESC firmware (32-bit) | v0.3.2 | 245 ESC board configs, 4 MCU families. Host-tested, not yet run on a real ESC. |
| CoreDrive-8051 (8-bit EFM8BB51) | **currently developing** | Target: the Air65 II's 12A ESCs (layout A_X_05). 19 of 19 simulator scenarios pass on layouts A to E. Stock ESCs backed up. Never flashed. |
| NexusGround configurator | v0.4.3 | Windows and Linux installers available. DFU flashing works on Windows. |
| NexusTune in-flight AI tuning | in review | Feature extractor, int8 GRU kernel, safety supervisor and pilot switch are in the flight controller code (SITL tested). First version of its model, **Vireo**, trained with Oxiryn; not yet passing all accuracy gates. Not in any release, never flown. |
| Oxiryn (ML framework) | onboard | Trains Vireo, the NexusTune model, and exports the int8 weights the FC runs. Runs on the training machine, not on the aircraft. |

### What's new since v0.3.2

- **29 board-specific firmware targets** (was 27), each built with its own pin map and compile-time pin conflict checks, all bundled in NexusGround so no build tools are needed.
- **STM32F411 clock fix** (v0.3.3): F411 boards now run at 96 MHz SYSCLK with a 48 MHz USB clock instead of the F405's 168 MHz configuration.
- **Working USB DFU flashing on Windows** in NexusGround v0.4.3.
- **BETAFPV Air65 II support** (currently developing): the Matrix 1S 5IN1 II board (`betafpv_g473_v2`) with gyro auto-detection for the ICM-42688-P, ICM-42622-P, BMI270 and LSM6DSK320X, bidirectional DShot, SmartAudio, AT7456E OSD, and Betaflight-compatible motor order, board alignment, props-out and Actual rates.
- **Boot guard and USB reboot-to-bootloader** (in review): firmware that fails to start can no longer lock a board out of USB. See [Safety](#flashing-safety).
- **CoreDrive-8051** (currently developing): CoreDrive for the 8-bit EFM8BB51 ESCs found on whoop AIO boards like the Air65 II.
- **Oxiryn onboard**: Oxiryn, the AutomataNexus machine learning framework written in Rust, is now part of the suite as the training side of NexusTune. See [Oxiryn](#oxiryn--the-ml-framework-behind-nexustune).
- **NexusTune** (in review): in-flight AI PID tuning. The on-FC inference kernel, supervisor and pilot switch are written and SITL-tested, and the first version of **Vireo**, the Oxiryn-trained model NexusTune runs, exists. See below.

---

## Why NexusFlight?

Every existing flight controller firmware (Betaflight, iNav, ArduPilot) treats the ESC as a black box. You flash the FC firmware, you flash the ESC firmware, and you hope they play nice together. The FC sends throttle commands over DShot and that's where its control ends.

**NexusFlight breaks that wall down.**

NexusFlight Suite ships **its own ESC firmware, CoreDrive**, alongside the FC firmware. The two are designed together and configured from the same app. On 32-bit ESCs, CoreDrive runs **integrated FOC (Field-Oriented Control)**: the flight controller doesn't just send throttle percentages, it shares the motor model, tunes the FOC loop, and reads real-time telemetry from every motor. On 8-bit whoop ESCs, CoreDrive-8051 brings the same "one system" approach to boards the 32-bit firmware can't run on.

To the best of our knowledge, no other flight controller software in the FPV drone ecosystem does this.

---

## What Sets NexusFlight Apart

NexusFlight goes beyond matching Betaflight feature-for-feature. These are capabilities that no other open-source flight controller firmware offers:

| Feature | Betaflight | NexusFlight |
|---------|-----------|-------------|
| **Gyro filtering** | Fixed-coefficient biquad chain | **Adaptive Kalman filter**: adjusts trust between prediction and measurement based on actual noise levels. Designed for less phase lag at equivalent noise rejection. |
| **Rate controller** | PID only | **ADRC (Active Disturbance Rejection Control)**: an Extended State Observer estimates and cancels total disturbance (wind, prop wash, weight changes) in real time. One tuning parameter instead of four. |
| **Gain scheduling** | TPA (linear D-term attenuation) | **Model-based gain scheduling**: scales all PID terms using thrust model curves and battery voltage compensation across the full flight envelope. |
| **Cross-axis coupling** | None | **Gyroscopic decoupling feedforward**: pre-compensates precession torques during yaw maneuvers. |
| **Auto-tune** | Manual tuning from blackbox logs | **Frequency-domain system identification**: estimates the plant transfer function from normal flight data via Welch's method. No deliberate oscillation needed. |
| **In-flight tuning** | None | **NexusTune** *(in review)*: **Vireo**, a small Oxiryn-trained neural network on the FC, that adjusts PID gains while you fly, inside hard limits, under a safety supervisor. |
| **Navigation** | None (that's iNav) | **9-state EKF**: GPS-IMU fusion with wind estimation, position hold, waypoint missions, wind-aware RTH. |
| **ESC integration** | DShot throttle commands | **Integrated ESC firmware**: FOC on 32-bit ESCs, CoreDrive-8051 on 8-bit ESCs, shared motor model, unified configuration. |
| **Brick protection** | Reboot to bootloader only from firmware that is running | **Boot guard** *(in review)*: after three failed starts in a row the FC drops into its USB bootloader on its own, so a bad image can't lock out a board with no BOOT button. |
| **Debug telemetry** | Limited | **Live 20 Hz debug stream**: gyro, PID terms, motors, attitude, CPU, battery, 4 debug channels with real-time charts in the configurator. |

---

## NexusTune — In-Flight AI Tuning

<p align="center">
  <img src="https://img.shields.io/badge/STATUS-In%20Review-8E44AD?style=for-the-badge" alt="In Review">
  &nbsp;
  <img src="https://img.shields.io/badge/Model-Vireo-1F6FEB?style=for-the-badge" alt="Model: Vireo">
  &nbsp;
  <img src="https://img.shields.io/badge/Trained_with-Oxiryn-1F6FEB?style=for-the-badge" alt="Trained with Oxiryn">
</p>

NexusGround's auto-tune already designs PID gains from blackbox logs on the ground. **NexusTune moves tuning into the air.** NexusTune is in-flight tuning powered by **Vireo**, a 23k-parameter on-board model: NexusTune is the whole system (onboard system identification, Vireo and the safety supervisor), and Vireo is the small recurrent neural network at its heart. Vireo runs on the flight controller, watches how the quad actually responds to your sticks, and nudges the gains toward a better tune while you fly.

**How it works:**

- **The model: Vireo.** A compact GRU network of about **23,500 parameters** (dense 75→64, GRU 64→48, dense 48→32, dense 32→20), quantized to **int8** with per-row scales. The whole weight blob is **26,400 bytes**, one inference is about **23,000 multiply-accumulates**, and the tuner needs about **5.3 KB of RAM**, so it fits an F4 or G4 flight controller. It runs at **100 Hz**, separately from the main flight loop.
- **Trained with Oxiryn.** Vireo is trained in [Oxiryn](#oxiryn--the-ml-framework-behind-nexustune) on simulated flights from NexusFlight's software-in-the-loop quad model, with varied frames, motors, noise, resonances and deliberately mistuned starting gains. Oxiryn exports Vireo's weights as an `NXTM` blob (model files are named `vireo-vN.nxtm`); the FC runs them with its own fixed-memory inference kernel in `nexus-core`.
- **What it sees.** 75 features per 10 ms step (schema `nxtune-feat-v2`): tracking error, overshoot, noise and oscillation measures per axis from the gyro, setpoint, PID terms, motor outputs and battery, plus the live gains, filter cutoffs and loop rate it is working on.
- **What it changes.** For each of roll, pitch and yaw: P, I, D, feedforward and the D-term filter cutoff, plus the gyro lowpass cutoff. Every output is a **multiplier on the pilot's own tune**, never an absolute gain. P and D are bounded to **0.5× to 1.5×** of the pilot's values, I to 0.5× to 2×, feedforward to 0.25× to 1.5×, and filter cutoffs to 0.7× to 1.4×.
- **A supervisor has the final say.** Vireo also outputs an oscillation-risk estimate per axis and a confidence score. A deterministic, rule-based supervisor clamps every gain to its band, limits how fast it can change, ignores Vireo when its confidence is below 0.6, aborts on oscillation, noise or loss of authority, and **reverts to the pilot's tune** when risk climbs past 0.7. An onboard recursive-least-squares system identifier runs alongside Vireo under the same supervisor.
- **The pilot stays in charge.** A three-position switch: **low** reverts to your tune, **mid** holds the current gains, **high** lets NexusTune adjust. The switch channel is configurable (AUX5 in the Air65 II default profile).

**Status:** the feature extractor, int8 kernel and `NXTM` loader, supervisor, tuner and pilot switch are in the flight controller code and pass host and SITL tests (in review, not yet merged). `nxtune-check` runs any trained model through the exact firmware kernel and gates it on accuracy, risk detection and parity with Oxiryn's own outputs. The first Oxiryn-trained int8 Vireo model clears the risk-detection gate on all three axes but **does not yet clear the P/D accuracy gate**, so training continues. **NexusTune is not in any release and has not flown.** It will ship as an opt-in feature once it has been proven on the bench and in flight.

---

## Oxiryn — The ML Framework Behind NexusTune

<p align="center">
  <img src="https://img.shields.io/badge/Oxiryn-Onboard-1F6FEB?style=for-the-badge" alt="Oxiryn onboard">
  &nbsp;
  <img src="https://img.shields.io/badge/Written_in-Rust-DEA584?style=for-the-badge&logo=rust&logoColor=white" alt="Written in Rust">
</p>

**Oxiryn** is the AutomataNexus machine learning framework, written in Rust. It is now part of NexusFlight Suite as the training and export side of NexusTune: Oxiryn builds **Vireo**, trains it, and produces the weights that fly.

| Step | Where it runs | What happens |
|------|---------------|--------------|
| **1. Generate data** | Desktop (`nxtune-datagen`) | NexusFlight's SITL quad model flies thousands of simulated quads and writes `.nxtd` training files with features and target labels. |
| **2. Train** | Desktop / GPU box, **Oxiryn** | Oxiryn trains Vireo, then fine-tunes it with int8 quantization-aware training so the weights behave the same once quantized. |
| **3. Export** | **Oxiryn** | Oxiryn writes Vireo as an `NXTM` blob: int8 weights with per-row scales, a schema CRC so a model can't be loaded against the wrong features, and a checksum. |
| **4. Verify** | Desktop (`nxtune-check`) | The exported Vireo model is run through the exact firmware kernel. Its outputs must match Oxiryn's reference outputs (parity gate 0.02) and pass the accuracy and risk gates. The exporter matches the kernel's reference outputs to within 1e-7. |
| **5. Fly** | Flight controller, `nexus-core` | The FC's fixed-memory int8 kernel runs Vireo's Oxiryn-trained weights at 100 Hz under the supervisor. |

**What runs on the aircraft:** Vireo, the Oxiryn-trained model, not the Oxiryn library itself. Oxiryn's training stack needs a heap and the standard library, which a flight controller loop should not depend on, so the FC uses its own small kernel with no heap, no allocation and a fixed memory footprint. The `NXTM` format and the kernel are kept bit-compatible with Oxiryn's export, and `nxtune-check` proves it for every Vireo build before it can be loaded.

---

## CoreDrive — Field-Oriented Control

<p align="center">
  <img src="https://img.shields.io/badge/Integrated%20FOC%20ESC%20in%20a%20Flight%20Controller%20Suite-E34F26?style=for-the-badge" alt="Integrated FOC ESC">
</p>

**CoreDrive** is a from-scratch BLDC motor ESC firmware with a full **Field-Oriented Control** engine. While traditional ESC firmware (BLHeli_32, BLHeli_S, AM32) uses trapezoidal six-step commutation, CoreDrive implements **sinusoidal FOC**, the same control strategy used in industrial servo drives and high-performance robotics.

### What FOC Means for FPV

| | Traditional Six-Step | CoreDrive FOC |
|---|---|---|
| **Commutation** | 6 discrete steps per electrical revolution | Continuous sinusoidal |
| **Torque ripple** | High: causes vibration and noise | Much lower: smoother motor, cleaner gyro signal |
| **Efficiency** | ~85% typical | Up to ~90-93% depending on operating point, most pronounced at partial throttle and low speed |
| **Low-throttle control** | Coarse, jittery | Precise and linear: better authority on micro quads |
| **Noise** | Audible commutation whine | Much quieter operation |
| **Startup** | Can stutter or desync | Controlled align and ramp with stall recovery |

### How It Works

CoreDrive decomposes motor current into two orthogonal axes using the **Park and Clarke transforms**:

- **D-axis (Direct)** controls magnetic flux. Held at zero for maximum torque-per-amp efficiency.
- **Q-axis (Quadrature)** controls torque. This is where your throttle command goes.

Each axis has its own **PI controller** with independently tunable Kp/Ki gains. A **sensorless back-EMF observer** estimates rotor position in real time: no hall sensors or encoders needed, just the three motor wires you already have.

### FOC Features

- **D-Q axis PI controllers**: independent Kp/Ki gains for flux (D) and torque (Q) control
- **Motor model parameters**: winding resistance, inductance, and observer gain for your specific motor
- **Sensorless rotor estimation**: back-EMF observer tracks rotor position without hall sensors or encoders
- **Switchable control modes**: toggle between FOC and six-step per ESC from NexusGround
- **Configurable startup sequence**: listen duration, alignment hold, eRPM ramp rate, stall recovery with cooldown
- **Full protection suite**: over-current (mA), over-temperature, under-voltage (mV), commutation desync, stall timeout
- **3D / bidirectional mode**: FOC control in both motor directions for inverted flight
- **PWM flexibility**: 24, 48, or 96 kHz switching frequency with 0-30° timing advance
- **Extended DShot Telemetry**: eRPM, ESC temperature, current draw, and voltage per motor in real time
- **4-way passthrough**: configure each ESC individually through the FC, no direct ESC connection needed
- **Integrated tuning**: tune FOC parameters from NexusGround's ESC/CoreDrive tab with live motor detection

### CoreDrive-8051 — for 8-bit whoop ESCs

<p align="center">
  <img src="https://img.shields.io/badge/STATUS-Currently%20Developing-E34F26?style=for-the-badge" alt="Currently Developing">
</p>

Most 1S whoop AIO boards, including the **BETAFPV Air65 II's Matrix 1S 5IN1 II**, drive their motors from separate 8-bit **Silicon Labs EFM8BB51** chips (8051 core) that the Rust CoreDrive targets can't run on. **CoreDrive-8051** is CoreDrive for those chips.

- Written in **C (SDCC) with an 8051 assembly commutation core**, built on the proven Bluejay six-step design and its timing constants, and FC-compatible with it: DShot300/600, bidirectional DShot with extended telemetry, the same settings layout and layout tags.
- First target: the Air65 II's 12A ESCs, layout **A_X_05**, with BETAFPV's stock startup power, beep and temperature settings as defaults.
- Developed against a **whole-board simulator** (`efm8sim`) that models the MCU, gate driver, motor and DShot input. **All 19 test scenarios pass on each of the five common layouts (A to E)**, including standstill starts straight into 30% and 100% throttle on every motor KV tested. The stock Bluejay image also runs in the simulator, so the two can be compared directly.
- The simulator found two edge-case fixes over the upstream design: overflow-safe PWM register write order, and correct dead time at 100% duty (the stock image shows the shoot-through that CoreDrive-8051 fixes).
- Comes with a **read-only ESC backup tool** that saves all four stock ESCs through the flight controller before anything is changed. Our Air65 II's four ESCs are backed up.
- **Status: sim-tested only, never flashed to hardware.** The first bench test is one ESC on the Air65 II, props off.

### FOC + NexusFlight = Tighter Loop

Because the FC and ESC firmware are designed together:

- The FC reads motor eRPM via bidirectional DShot and feeds it into **RPM-based dynamic notch filters**, removing motor vibration harmonics from the gyro signal before they reach the PID loop
- Motor model parameters (resistance, inductance, pole pairs) are shared between the FOC observer and the FC's telemetry system
- Configuration backup captures both FC and ESC settings to Aegis-DB in one operation
- One configurator app (NexusGround) tunes both the flight PID loop and the motor FOC loop

---

## Downloads

> **Before you flash:** these are pre-beta builds. Nothing has flown yet. Back up your stock firmware first, flash with props off, and keep a way into the bootloader (the BOOT button or pads). See [Flashing Safety](#flashing-safety).

### NexusGround (Configurator) v0.4.3

The desktop app for configuring your flight controller and ESCs: PID tuning, FOC tuning, rates, receiver setup, OSD, VTX, blackbox, firmware flashing, auto-tune, live debug telemetry, and more. **Ships with all 29 board firmware images built in.**

| Platform | Download | Size |
|----------|----------|------|
| **Windows 10/11** (x64) | [NexusGround_0.4.3_x64-setup.exe](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.4.3/NexusGround_0.4.3_x64-setup.exe) | ~20 MB |
| **Linux** (.deb, Ubuntu/Debian) | [NexusGround_0.4.3_amd64.deb](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.4.3/NexusGround_0.4.3_amd64.deb) | ~23 MB |
| **Linux** (.rpm, Fedora/RHEL) | [NexusGround-0.4.3-1.x86_64.rpm](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.4.3/NexusGround-0.4.3-1.x86_64.rpm) | ~23 MB |
| **Linux** (.AppImage, universal) | [NexusGround_0.4.3_amd64.AppImage](https://github.com/AutomataNexus/NexusFlight-Suite/releases/download/nexusground-v0.4.3/NexusGround_0.4.3_amd64.AppImage) | ~93 MB |

> **Note:** macOS builds are coming soon. For now, macOS users can build from source. See [Building from Source](docs/BUILDING.md).

### NexusFlight Firmware v0.3.3

One firmware image per board, built with that board's pin map. Flash through NexusGround's built-in flasher (it already includes them), or download individually from the [v0.3.3 release](https://github.com/AutomataNexus/NexusFlight-Suite/releases/tag/nexusflight-v0.3.3).

| MCU Family | Boards in v0.3.3 |
|-------------|-----|
| **STM32F405** (10) | SpeedyBee F405 V4, V3, Mini, AIO and Wing; Happymodel SuperF405 and CrazyBee F405; Flywoo F405S AIO; GEPRC F405; Matek F405 Wing V2 |
| **STM32F411** (5) | BETAFPV F411, HDZero AIO5, Happymodel CrazyBee F4 DX, T-Motor F411, GEPRC Taker F411 |
| **STM32F722** (2) | Flywoo F722 Pro V2, GEPRC F722 AIO |
| **STM32G473** (5) | Happymodel CrazyBee G473, BETAFPV G473 (first revision), GEPRC Taker G473 AIO, HDZero Gamma 45A, HDZero AIO15 |
| **STM32H743** (7) | HDZero Halo, GEPRC Taker H743, Sequre H7 V1 and V2, Matek H743, T-Motor Pacer H743, iFlight Blitz H7 Pro |

> **BETAFPV Air65 II / Air75 II owners:** the `betafpv_g473` image in v0.3.3 is for the **first** BETAFPV G473 board revision and uses different pins. **Do not flash it to a Matrix 1S 5IN1 II.** That board gets its own target, `betafpv_g473_v2`, in the next release.

### NexusCore (Library)

The core flight algorithms as a standalone Rust crate: `no_std` compatible, usable in your own projects.

```toml
# Cargo.toml (available upon source access request)
[dependencies]
nexus-core = { git = "https://github.com/AutomataNexus/NexusFlight.git", branch = "main" }
```

---

## The Suite

### NexusFlight Firmware

**Core Flight Stack:**
- **Rust firmware**: NexusFlight and the 32-bit CoreDrive targets are written in Rust with no C dependencies, memory-safe by default (CoreDrive-8051 is C and 8051 assembly, since no Rust toolchain targets the 8051)
- **Embassy async runtime**: cooperative multitasking with zero-cost state machines on a single stack
- **Per-board builds**: every board compiles from its own pin definition, with pin conflicts caught at compile time
- **Gyro auto-detection**: BMI270, ICM-42688-P, ICM-42622-P and LSM6DSK320X, detected at boot, with boot-time bias calibration and the loop rate taken from the detected gyro *(F4 and G4 targets, in review)*
- **7 flight modes**: Acro, Angle, Horizon, Position Hold, Waypoint Mission, Turtle (flip-over-after-crash), Launch Control
- **Protocol support**: MSP v2, CRSF/ELRS, S.BUS, DShot (150/300/600), SmartAudio, Tramp IRC, UBX GPS
- **Bidirectional DShot**: real-time eRPM telemetry via GCR decoding, RPM-driven dynamic notch filters
- **OSD**: MAX7456 analog + MSP DisplayPort digital (DJI/HDZero/Walksnail)
- **Blackbox**: 96-byte v3 frames with dual gyro (raw+filtered), separated PID terms, debug channels, delta compression
- **Safety**: staged failsafe (hold, ramp, disarm), arming pre-checks, watchdog, stack guard, hard fault handler, boot guard *(in review)*

**Advanced Control (beyond Betaflight):**
- **Adaptive Kalman gyro filter**: per-axis 1D Kalman with adaptive measurement noise R. Replaces the PT1+biquad lowpass chain.
- **ADRC rate controller**: Extended State Observer estimates total disturbance and cancels it. Roll/pitch ADRC with PID yaw hybrid mode. A single bandwidth parameter tunes all observer gains.
- **Cross-axis decoupling feedforward**: pre-compensates gyroscopic precession during yaw maneuvers.
- **Model-based gain scheduling**: thrust-curve-aware PID scaling (linear/sqrt/model-based) + battery voltage compensation. Replaces simple TPA.
- **Anti-gravity**: throttle change rate detection with temporary I-term boost for punch response.
- **RC smoothing**: auto-tuned PT1 filter that detects RC frame rate and sets cutoff at 2x.
- **NexusTune in-flight AI tuning** *(in review)*: see [above](#nexustune--in-flight-ai-tuning).

**Navigation:**
- **9-state Extended Kalman Filter**: GPS-IMU sensor fusion: position (NED), velocity (NED), wind (NE), vertical accel bias
- **Position Hold**: cascaded PID (position, velocity, lean angle) with heading rotation
- **Waypoint Mission**: autonomous multi-point navigation state machine (transit, hold, RTH, landing)
- **GPS Rescue**: wind-aware and battery-aware return-to-home via EKF or raw GPS fallback

**Sensor Fusion & Filtering:**
- **Mahony AHRS**: complementary filter with gyro + accelerometer fusion for attitude estimation
- **256-point FFT**: fixed-point radix-2 with peak detection for dynamic notch frequency identification
- **Dynamic notch**: FFT-based and RPM-based, auto-tracking motor noise harmonics
- **Configurable filter chain**: PT1, biquad lowpass, biquad notch, per-axis configuration

### Flashing Safety

A flight controller that crashes before USB starts can only be recovered with the BOOT button, and some whoop boards don't have one. NexusFlight is built so that doesn't happen *(boot guard and reboot-to-bootloader are in review for the F4 and G4 targets)*:

- **Boot guard**: the firmware counts its own failed starts. After **three failed starts in a row** it jumps straight into the MCU's USB DFU bootloader, so you can flash a fixed image with no button and no debug probe.
- **Reboot to bootloader over USB**: NexusGround can send one command (`MSP_REBOOT` with the bootloader option) and the FC restarts into DFU, ready to flash.
- **Early watchdog and HardFault reset**: a hang or fault resets the board instead of leaving it dead, and each such reset counts toward the boot guard.
- **Boot simulator**: every image is started in an emulated STM32F411 or STM32G473 (`tools/boot-sim`) before release. It checks gyro detection, the main loop, crash-loop recovery and the bootloader jump. It exists because an earlier image passed every unit test and still reset-looped on a real board.
- **Config-safe flashing**: NexusGround backs up the configuration before flashing and never mass-erases the chip.

Recommended for every first flash: **props off**, save the stock CLI `dump` and a full flash backup, and flash **one board** before the rest of your fleet. On analog VTX boards like the Air65 II, never power the board without the VTX antenna fitted.

### NexusGround Configurator

- **15 configuration tabs**: Setup, Firmware Flasher, PID, Rates, Receiver, Motors, Gyro/Filters, OSD, VTX, GPS, Blackbox, CLI, ESC/CoreDrive, Auto-Tune, Debug
- **Bundled firmware**: all 29 board images built in; pick your board and flash, no build tools needed
- **USB DFU flasher**: STM32 DFU flashing with driver install on Windows, plus the AN3155 UART bootloader protocol, chip auto-detection, and automatic config backup before flash
- **Frequency-domain auto-tune**: load blackbox logs, system identification via Welch's method, Bode plot visualization, automatic PID gain design for target bandwidth/phase margin
- **Live debug telemetry**: 20 Hz streaming of gyro, PID output, motors, attitude, CPU load, battery, RSSI, and 4 debug channels with time-series charts and a scrolling log console
- **ESC/CoreDrive FOC tab**: per-motor detection, D/Q-axis PI tuning, motor model parameters, protection thresholds, startup sequence editor
- **Config profiles**: save/load/compare full FC + ESC configurations via Aegis-DB
- **Cross-platform**: Windows (NSIS installer) and Linux (.deb, .rpm, .AppImage)
- **Light and dark themes**: cream/teal/copper light theme (default) with dark toggle, persisted to DB
- **Built with Tauri 2**: React 19 + TypeScript + Vite frontend, Rust backend

### NexusCore Library

- **`no_std` compatible**: runs on bare metal, WASM, or desktop
- **460+ unit tests** across 36 modules
- **Modular**: use only the algorithms you need (PID, ADRC, Kalman, AHRS, EKF, filters, RC, MSP, mixer, etc.)
- **Benchmarked**: sub-10 ns PID loop, ~1.8 µs FFT, ~54 ns CRSF parse (Criterion benchmarks)
- **`serde` feature flag**: optional serialization support for Tauri/WASM reuse
- **`#[repr(C)]` config**: deterministic memory layout with CRC32 integrity for direct flash serialization

---

## Supported Hardware

NexusFlight v0.3.3 builds for **29 flight controller boards** across 5 STM32 families. The BETAFPV Air65 II board is the 30th target and the one **currently in development** (see [above](#-currently-developing-betafpv-air65-ii)). **Hardware verification is in progress; no board is marked flight-proven yet.**

| MCU Family | Clock | Boards | Status |
|------------|-------|--------|--------|
| **STM32F405** | 168 MHz | SpeedyBee F405 V3/V4/Mini/AIO/Wing, Happymodel SuperF405 and CrazyBee F405, Flywoo F405S AIO, GEPRC F405, Matek F405 Wing V2 | Builds, awaiting hardware test |
| **STM32F411** | 96 MHz | BETAFPV F411, HDZero AIO5, Happymodel CrazyBee F4 DX, T-Motor F411, GEPRC Taker F411 | Bench bring-up in progress (T-Motor F411) |
| **STM32F722** | 216 MHz | Flywoo F722 Pro V2, GEPRC F722 AIO | Builds, awaiting hardware test |
| **STM32G473** | 170 MHz | Happymodel CrazyBee G473, BETAFPV G473, GEPRC Taker G473 AIO, HDZero Gamma 45A, HDZero AIO15 | Builds, awaiting hardware test |
| **STM32G473/G474** | 170 MHz | 📌 **BETAFPV Air65 II / Matrix 1S 5IN1 II** (`betafpv_g473_v2`) | **Currently developing**: boot-simulator tested, first flash next |
| **STM32H743** | 480 MHz | HDZero Halo, GEPRC Taker H743, Sequre H7 V1/V2, Matek H743, T-Motor Pacer H743, iFlight Blitz H7 Pro | Builds, awaiting hardware test |
| **AT32F435** | 288 MHz | iFlight Blitz F4 F435 | Configurator board database only; no firmware target yet |

> See [docs/SUPPORTED_HARDWARE.md](docs/SUPPORTED_HARDWARE.md) for the full board list with pinouts and features.

### Supported ESCs

| ESC | MCU | Firmware | Status |
|-----|-----|----------|--------|
| 📌 **BETAFPV Matrix 1S 5IN1 II, 4 × 12A** (Air65 II) | EFM8BB51 (8051) | **CoreDrive-8051**, layout A_X_05 | **Currently developing**: simulator tested, never flashed |
| Other EFM8BB51 Bluejay layouts A to E | EFM8BB51 (8051) | CoreDrive-8051 | Build and pass the simulator, no hardware target yet |
| 245 32-bit ESC board configs | STM32G071, STM32F051, GD32E230, AT32F421 and more | CoreDrive (FOC / six-step) | Host-tested, not yet run on a real ESC |

### Supported Gyros

| Gyro | Driver | Notes |
|------|--------|-------|
| Bosch BMI270 | ✓ | Full Bosch configuration blob loaded at boot |
| TDK ICM-42688-P | ✓ | |
| TDK ICM-42622-P | ✓ *(in review)* | Handled by the ICM-42688 driver |
| ST LSM6DSK320X | ✓ *(in review)* | New driver, fitted to some Air65 II batches |

On the F4 and G4 targets the gyro is identified at boot from its ID registers, so one firmware image covers every variant of a board.

### Supported Aircraft

| Frame | Motors | Recommended MCU | Gyro |
|-------|--------|----------------|------|
| 65mm whoop (e.g. BETAFPV Air65 II) | 4 | F411 / G473 | BMI270, ICM-42688-P, ICM-42622-P or LSM6DSK320X |
| 75mm whoop | 4 | F411 / G473 | BMI270 |
| 5" freestyle/racing | 4 | F405/F722/G473 | ICM-42688-P |
| 5" HD (digital VTX) | 4 | G473/H743 | ICM-42688-P |
| 7-8" long range | 4 | F405/F745/H743 | ICM-42688-P |

---

## Quick Start

### 1. Install NexusGround

Download the installer for your platform from the [Releases](https://github.com/AutomataNexus/NexusFlight-Suite/releases) page, or use the direct links above.

### 2. Back Up Your Stock Firmware

Before flashing anything, save your current setup: in your existing configurator's CLI, run `dump` and save the output. If you can, also take a full flash backup over DFU so the board can be restored exactly.

### 3. Connect Your Flight Controller

Plug in your FC via USB with **props off**. NexusGround will auto-detect the board, MCU, and current firmware version.

### 4. Flash NexusFlight Firmware

Use the **Firmware** tab in NexusGround:
1. Select your board (auto-detected or manual). Check it matches your board revision.
2. Click **Backup Config & Prepare Flash**
3. Enter bootloader mode (hold BOOT + plug USB; on Windows, click **Install DFU Driver** the first time)
4. Select the DFU device and click **Flash Firmware**

### 5. Configure Everything — FC and ESC — in One Place

Use the configurator tabs to tune PIDs, set rates, configure your receiver, OSD, VTX, and GPS modes. Open the **ESC/CoreDrive** tab to tune FOC parameters, set protection thresholds, and configure motor startup. Use the **Auto-Tune** tab to analyze blackbox logs and compute PID gains. Monitor everything in real time with the **Debug** tab.

> See [docs/GETTING_STARTED.md](docs/GETTING_STARTED.md) for a detailed walkthrough.

---

## Architecture

```
NexusFlight Suite
│
├── NexusFlight (FC Firmware) ............... v0.3.3
│   ├── nexus-core ........... Flight algorithms: PID, ADRC, Kalman, AHRS, EKF,
│   │                          filters, FFT, mixer, MSP, GPS, OSD, VTX, blackbox,
│   │                          navigation, waypoints, 36 modules, 460+ tests
│   │   └── nexustune ........ In-flight AI tuning: 75-feature extractor, RLS
│   │                          system ID, int8 GRU kernel + NXTM loader,
│   │                          supervisor, tuner (in review)
│   ├── nexus-hal ............ Hardware abstraction traits (gyro, motor, RC, serial,
│   │                          storage, ADC, watchdog, beeper, LED strip, servo)
│   ├── nexus-drivers ........ Device drivers: BMI270, ICM-42688-P/42622-P,
│   │                          LSM6DSK320X, MAX7456, CRSF, SBUS, DShot, u-blox GPS,
│   │                          SPI flash, VTX
│   ├── nexus-board .......... Board definitions and pin mappings (29 boards)
│   ├── targets/ ............. MCU-specific entry points
│   │   ├── stm32f4 .......... STM32F405 / F411 (Cortex-M4F)
│   │   ├── stm32f7 .......... STM32F745 / F722 (Cortex-M7F)
│   │   ├── stm32g4 .......... STM32G473 / G431 (Cortex-M4F, DMAMUX)
│   │   ├── stm32h7 .......... STM32H743 / H723 (Cortex-M7F, 480 MHz)
│   │   └── sitl ............. Software-In-The-Loop (host testing and
│   │                          NexusTune training data generation)
│   └── tools/boot-sim ....... Emulated STM32F411/G473 boot smoke test
│
├── CoreDrive (ESC Firmware) ................ v0.3.2, 366 tests
│   ├── coredrive-core ....... FOC engine (Clarke/Park/SVPWM), D-Q PI controllers,
│   │                          six-step commutation, sensorless SMO observer,
│   │                          startup FSM, protection, telemetry, autotune,
│   │                          Q15 fixed-point math, config serialization
│   ├── coredrive-dshot ...... DShot 150/300/600 + bidirectional EDT telemetry
│   ├── coredrive-hal ........ Hardware abstraction traits (ADC, PWM, GPIO, flash, serial)
│   ├── coredrive-board ...... 245 ESC board configs across 7 MCU families
│   ├── coredrive-passthrough  4-way passthrough protocol (CRC-16/XMODEM)
│   ├── coredrive-bootloader . AM32-compatible bootloader protocol
│   ├── coredrive-flasher .... PC-side firmware flasher (std, serialport)
│   └── targets/ ............. 32-bit MCU targets + bootloaders, and CoreDrive-8051
│       ├── stm32g0 .......... STM32G071 (Cortex-M0+, 64 MHz, FOC + six-step)
│       ├── at32f4 ........... AT32F421 (Cortex-M4, 120 MHz, FOC)
│       ├── stm32f0 .......... STM32F051 (Cortex-M0, 48 MHz, six-step)
│       ├── gd32e2 ........... GD32E230 (Cortex-M23, 72 MHz, six-step)
│       └── efm8 ............. CoreDrive-8051: EFM8BB51 (8051, six-step, C + asm,
│                              whole-board simulator, in development)
│
├── NexusGround (Configurator) .............. v0.4.3
│   ├── src/ ................. React 19 + TypeScript + Vite (15 tabs)
│   └── src-tauri/ ........... Rust backend: MSP bridge, serial, DFU + UART flasher,
│                              ESC passthrough, auto-tune (FFT system ID), board DB,
│                              bundled firmware, Aegis-DB client
│
├── NexusTune Training ...................... in development
│   ├── nxtune-datagen ....... Simulated flights → .nxtd training data
│   ├── Oxiryn ............... Rust ML framework (onboard): trains Vireo with
│   │                          int8 quantization-aware training, exports NXTM
│   │                          weights for the FC kernel
│   └── nxtune-check ......... Runs a model through the firmware kernel: parity
│                              with Oxiryn, accuracy and risk gates
│
└── Aegis-DB ................. Configuration database (FC + ESC backup/restore/profiles)
```

### Performance

Hot-path benchmarks (Criterion, Cortex-M7 equivalent):

| Operation | Time |
|-----------|------|
| Full 3-axis PID loop + mixer + filters | ~9 ns |
| Single-axis PID (P+I+D+FF) | ~3 ns |
| 256-point FFT | ~1.8 µs |
| Gyro filter chain (LP + notch + D-LP) | ~3.5 ns |
| CRSF RC frame parse | ~54 ns |
| DShot frame encode (per motor) | ~1.1 ns |
| MSP frame parse | ~73 ns |

---

## Roadmap to Beta

1. **📌 Air65 II first boot** (currently developing): NexusFlight on one Air65 II, props off, VTX antenna on, stock firmware backed up: USB, gyro, receiver, DShot output, motor and stick directions, arming and failsafe.
2. **Boot guard proven on the bench**: reboot to DFU with no button.
3. **📌 CoreDrive-8051 bench test** (currently developing) on one Air65 II ESC, with all four stock ESCs already backed up.
4. **Air65 II flight features**: angle and horizon modes, turtle, beeper, VTX pit mode, RPM filter and dynamic notch in the loop.
5. **T-Motor F411 AIO recovery and bring-up**, and the boot guard and gyro auto-detect on the F7 and H7 targets.
6. **First flights**, then **beta releases**.
7. **NexusTune**: keep training Vireo in Oxiryn until it clears every `nxtune-check` gate, bench-test the supervisor, then fly as an opt-in feature.

---

## Request Source Access

The NexusFlight source code is maintained in private repositories during pre-1.0 development. We welcome contributors, hardware partners, testers and community members who want to get involved.

**Open-sourcing NexusCore:** We are working toward open-sourcing the `nexus-core` algorithms crate (PID, ADRC, Kalman, AHRS, EKF, filters, mixer: the pure math with no hardware dependencies) so the underlying implementations can be independently reviewed. This is planned for the v1.0 release.

**To request early access:**

1. Visit [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com) and reach out via the contact form
2. Email us at **devops@automatanexus.com** with:
   - Your GitHub username
   - What you'd like to contribute (firmware, FOC/ESC, drivers, ground station, NexusTune/Oxiryn, docs, hardware testing)
   - Your experience with flight controllers, motor control, machine learning or embedded Rust
3. Open an [Issue](https://github.com/AutomataNexus/NexusFlight-Suite/issues/new?template=source-access.md) in this repo using the "Source Access Request" template

We typically respond within 48 hours.

---

## Community

- **Website:** [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com)
- **Email:** devops@automatanexus.com
- **Issues & Requests:** [GitHub Issues](https://github.com/AutomataNexus/NexusFlight-Suite/issues)

---

## License

NexusFlight Suite is licensed under the **GNU General Public License v3.0**. See [LICENSE](LICENSE) for details. CoreDrive-8051 builds on the GPL-3.0 Bluejay ESC firmware.

Commercial licensing is available for the AutomataNexus-authored components (not CoreDrive-8051): contact us at [NexusFlight.AutomataNexus.com](https://NexusFlight.AutomataNexus.com).

---

<p align="center">
  <strong>Built with Rust. Built for flight. FC, ESC and tuning, designed as one system.</strong><br/><br/>
  <a href="https://NexusFlight.AutomataNexus.com">NexusFlight.AutomataNexus.com</a>
</p>
