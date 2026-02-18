# Building from Source

This guide covers how to build NexusFlight firmware and NexusGround from source.

> **Note:** Source access is required. See [Request Source Access](../README.md#request-source-access) to get started.

## Prerequisites

### Rust Toolchain

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add thumbv7em-none-eabihf   # For all STM32 targets (F4/F7/G4/H7)
```

### Embedded Tools

```bash
cargo install probe-rs-tools   # For debugging via SWD
cargo install flip-link         # Stack overflow protection
sudo apt install gcc-arm-none-eabi  # For objcopy (ELF -> BIN)
```

### NexusGround Dependencies

```bash
# Node.js 20+
node --version

# Tauri 2 system dependencies (Linux)
sudo apt install libwebkit2gtk-4.1-dev build-essential curl wget file \
  libxdo-dev libssl-dev libayatana-appindicator3-dev librsvg2-dev \
  libudev-dev pkg-config xdg-utils

# Windows: Install Visual Studio Build Tools + WebView2
```

## Building NexusFlight Firmware

### Clone the Repository

```bash
git clone https://github.com/AutomataNexus/NexusFlight.git
cd NexusFlight
```

### Build for a Specific MCU

All targets use `thumbv7em-none-eabihf`:

```bash
# STM32F405 (default for stm32f4 crate)
cargo build --release -p nexus-stm32f4 --target thumbv7em-none-eabihf

# STM32F411
cargo build --release -p nexus-stm32f4 --target thumbv7em-none-eabihf \
  --no-default-features --features stm32f411

# STM32F745 (default for stm32f7 crate)
cargo build --release -p nexus-stm32f7 --target thumbv7em-none-eabihf

# STM32G473 (default for stm32g4 crate)
cargo build --release -p nexus-stm32g4 --target thumbv7em-none-eabihf

# STM32H743 (default for stm32h7 crate)
cargo build --release -p nexus-stm32h7 --target thumbv7em-none-eabihf
```

### Convert ELF to BIN for Flashing

```bash
arm-none-eabi-objcopy -O binary \
  target/thumbv7em-none-eabihf/release/nexus-stm32f4 \
  nexusflight_stm32f405.bin

# H7 targets need section-specific copy (avoids sparse binary):
arm-none-eabi-objcopy -O binary \
  -j .vector_table -j .text -j .rodata -j .data \
  target/thumbv7em-none-eabihf/release/nexus-stm32h7 \
  nexusflight_stm32h7.bin
```

### Run Tests

```bash
# Core library tests (458 tests, runs on host)
cd crates/nexus-core && cargo test --lib

# Driver tests (84 tests)
cd crates/nexus-drivers && cargo test --lib

# HAL tests (2 tests)
cd crates/nexus-hal && cargo test --lib

# SITL tests (7 tests)
cd targets/sitl && cargo test

# NOTE: Do NOT use `cargo test --workspace` — STM32 targets
# conflict on stm32-metapac. Test crates individually.
```

### SITL (Software-in-the-Loop)

```bash
cargo run -p nexus-sitl
```

## Building NexusGround

### Install Dependencies

```bash
cd nexus-ground
npm install
```

### Development Mode

```bash
npx tauri dev
```

### Production Build

```bash
# Linux (produces .deb, .rpm, .AppImage)
npx tauri build

# Windows (cross-compile from Linux — requires MinGW + NSIS)
npx tauri build --target x86_64-pc-windows-gnu
```

Output locations:
- `.deb` — `src-tauri/target/release/bundle/deb/`
- `.rpm` — `src-tauri/target/release/bundle/rpm/`
- `.AppImage` — `src-tauri/target/release/bundle/appimage/`
- `.exe` (NSIS) — `src-tauri/target/x86_64-pc-windows-gnu/release/bundle/nsis/`

### Run Tests

```bash
# Frontend unit tests
npm test

# Rust backend tests
npm run test:rust

# All tests
npm run test:all
```

## Project Structure

```
NexusFlight/
├── Cargo.toml ................ Workspace root
├── crates/
│   ├── nexus-core/ ........... Flight algorithms (no_std, 458 tests)
│   ├── nexus-hal/ ............ Hardware abstraction layer
│   ├── nexus-drivers/ ........ Device drivers (84 tests)
│   └── nexus-board/ .......... Board pin definitions (27 boards)
├── targets/
│   ├── stm32f4/ .............. STM32F405/F411 entry point
│   ├── stm32f7/ .............. STM32F745/F722 entry point
│   ├── stm32g4/ .............. STM32G473/G431 entry point
│   ├── stm32h7/ .............. STM32H743/H723 entry point
│   └── sitl/ ................. Software-in-the-loop simulator
└── nexus-ground/ ............. Desktop configurator (Tauri 2)
    ├── src/ .................. React 19 + TypeScript frontend (15 tabs)
    └── src-tauri/ ............ Rust backend (MSP bridge, flasher, auto-tune)
```

## Troubleshooting

### `probe-rs` can't find the target
Make sure your debug probe (ST-Link, J-Link, or DAPLink) is connected and the correct chip is specified:
```bash
probe-rs info
```

### Tauri build fails on Linux
Ensure all system dependencies are installed. The most commonly missing packages are `libudev-dev` and `libwebkit2gtk-4.1-dev`.

### Cross-compilation to Windows fails
Install the MinGW toolchain and NSIS:
```bash
sudo apt install gcc-mingw-w64-x86-64 nsis
rustup target add x86_64-pc-windows-gnu
```

### AppImage build fails
Make sure `xdg-utils` is installed:
```bash
sudo apt install xdg-utils
```
