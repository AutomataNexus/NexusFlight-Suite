# Building from Source

This guide covers how to build NexusFlight firmware and NexusGround from source.

> **Note:** Source access is required. See [Request Source Access](../README.md#request-source-access) to get started.

## Prerequisites

### Rust Toolchain

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add thumbv7em-none-eabihf   # For STM32F4/F7
rustup target add thumbv7em-none-eabi      # For STM32H7
```

### Embedded Tools

```bash
cargo install probe-rs-tools   # For debugging via SWD
cargo install flip-link         # Stack overflow protection
```

### NexusGround Dependencies

```bash
# Node.js 20+
node --version

# Tauri 2 system dependencies (Linux)
sudo apt install libwebkit2gtk-4.1-dev build-essential curl wget file \
  libxdo-dev libssl-dev libayatana-appindicator3-dev librsvg2-dev \
  libudev-dev pkg-config

# Windows: Install Visual Studio Build Tools + WebView2
```

## Building NexusFlight Firmware

### Clone the Repository

```bash
git clone https://github.com/AutomataNexus/NexusFlight.git
cd NexusFlight
```

### Build for a Specific MCU

```bash
# STM32F405
cargo build --release -p nexus-stm32f4 --features stm32f405

# STM32F411
cargo build --release -p nexus-stm32f4 --features stm32f411

# STM32F722
cargo build --release -p nexus-stm32f7 --features stm32f722

# Convert ELF to BIN for flashing
cargo objcopy --release -p nexus-stm32f4 --features stm32f405 -- -O binary nexusflight.bin
```

### Run Tests

```bash
# Core library tests (runs on host)
cargo test -p nexus-core

# All library tests
cargo test --lib

# With coverage
cargo llvm-cov --lib
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
npm run tauri dev
```

### Production Build

```bash
# Linux (produces .deb, .rpm, .AppImage)
npm run tauri build

# Windows (cross-compile from Linux)
npm run tauri build -- --target x86_64-pc-windows-gnu
```

### Run Tests

```bash
# Frontend unit tests (58 tests)
npm test

# Rust backend tests (49 tests)
cd src-tauri && cargo test --lib

# E2E tests (requires built binary + display)
npm run test:e2e

# All tests
npm run test:all
```

## Project Structure

```
NexusFlight/
├── Cargo.toml ................ Workspace root
├── crates/
│   ├── nexus-core/ ........... Flight algorithms (no_std)
│   ├── nexus-hal/ ............ Hardware abstraction layer
│   ├── nexus-drivers/ ........ Device drivers
│   └── nexus-board/ .......... Board pin definitions
├── targets/
│   ├── stm32f4/ .............. STM32F4 entry point
│   ├── stm32f7/ .............. STM32F7 entry point
│   └── sitl/ ................. Software-in-the-loop simulator
└── nexus-ground/ ............. Desktop configurator (Tauri 2)
    ├── src/ .................. React frontend
    ├── src-tauri/ ............ Rust backend
    └── e2e/ .................. End-to-end tests
```

## Troubleshooting

### `probe-rs` can't find the target
Make sure your debug probe (ST-Link, J-Link, or DAPLink) is connected and the correct chip is specified:
```bash
probe-rs info
```

### Tauri build fails on Linux
Ensure all system dependencies are installed. The most commonly missing package is `libudev-dev`.

### Cross-compilation to Windows fails
Install the MinGW toolchain:
```bash
sudo apt install gcc-mingw-w64-x86-64
rustup target add x86_64-pc-windows-gnu
```
