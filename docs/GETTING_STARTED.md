# Getting Started with NexusFlight

This guide walks you through setting up NexusFlight on your flight controller from scratch.

## Prerequisites

- A supported flight controller board (see [Supported Hardware](SUPPORTED_HARDWARE.md))
- USB cable (micro-USB or USB-C, depending on your FC)
- A computer running Windows 10+ or Linux

## Step 1: Install NexusGround

Download the installer for your operating system from the [Releases](https://github.com/AutomataNexus/NexusFlight-Suite/releases) page:

| Platform | Package |
|----------|---------|
| Windows 10/11 | `NexusGround_0.1.0_x64-setup.exe` |
| Ubuntu / Debian | `NexusGround_0.1.0_amd64.deb` |
| Fedora / RHEL | `NexusGround-0.1.0-1.x86_64.rpm` |
| Any Linux | `NexusGround_0.1.0_amd64.AppImage` |

### Windows
Run the `.exe` installer and follow the prompts. NexusGround will be available in your Start menu.

### Linux (.deb)
```bash
sudo dpkg -i NexusGround_0.1.0_amd64.deb
```

### Linux (.rpm)
```bash
sudo rpm -i NexusGround-0.1.0-1.x86_64.rpm
```

### Linux (.AppImage)
```bash
chmod +x NexusGround_0.1.0_amd64.AppImage
./NexusGround_0.1.0_amd64.AppImage
```

## Step 2: Connect Your Flight Controller

1. Plug your FC into your computer via USB
2. Open NexusGround
3. Select the serial port from the dropdown in the top connection bar
4. Click **Connect**

NexusGround will communicate with your FC over MSP v2 and auto-detect the board name, MCU type, and current firmware version.

## Step 3: Flash NexusFlight Firmware

If your FC is running Betaflight or another firmware, you can flash NexusFlight using the built-in firmware flasher:

1. Navigate to the **Firmware** tab in the sidebar
2. Your board should be auto-detected. If not, select it manually from the dropdown
3. Choose your firmware source:
   - **Build from Source** — Compiles NexusFlight for your exact board (requires source access + Rust toolchain)
   - **Browse .bin** — Select a pre-built firmware binary downloaded from the Releases page
4. Click **Backup Config & Prepare Flash** — Your current configuration is saved to Aegis-DB
5. Follow the bootloader instructions:
   - Disconnect the FC from NexusGround
   - Hold the **BOOT** button on the FC
   - While holding BOOT, plug in USB (or press RESET)
   - Release BOOT after 1 second
6. Click **Detect Bootloader & Flash**
7. Wait for the flash to complete (progress bar will show status)
8. Reconnect to the FC via the top bar

## Step 4: Initial Configuration

After flashing, configure your FC through the NexusGround tabs:

### Essential Setup

| Tab | What to Configure |
|-----|-------------------|
| **Setup** | Verify board info, sensor orientation, accelerometer calibration |
| **Receiver** | Select protocol (CRSF/ELRS recommended), verify channel mapping |
| **Motors** | Verify motor order and direction, set idle throttle |
| **Rates** | Choose rate profile (Actual, Betaflight, KISS) and adjust curves |

### Tuning

| Tab | What to Configure |
|-----|-------------------|
| **PID Tuning** | Adjust PID gains per axis (Roll, Pitch, Yaw) |
| **Gyro / Filters** | Configure lowpass filters, notch filters, dynamic notch FFT |

### Optional

| Tab | What to Configure |
|-----|-------------------|
| **OSD** | Enable/position OSD elements (battery, RSSI, flight time, etc.) |
| **VTX** | Set band, channel, and power level (SmartAudio or Tramp) |
| **GPS** | Configure GPS rescue, satellite display |
| **Blackbox** | Enable onboard logging, set sample rate divider |
| **ESC / CoreDrive** | ESC telemetry and configuration |
| **CLI** | Advanced settings via command line interface |

## Step 5: First Flight

1. **Arm your quad** using your configured arm switch
2. NexusFlight will run pre-arm checks (accelerometer calibrated, receiver connected, throttle low)
3. Fly and enjoy!

## Troubleshooting

### FC not detected
- Make sure you have the correct USB drivers installed (STM32 VCP driver for Windows)
- Try a different USB cable (some cables are charge-only)
- Check that the correct serial port is selected

### Bootloader not detected
- Ensure you're holding the BOOT button while plugging in USB
- Some boards require holding BOOT + pressing RESET instead
- Try a different USB port (avoid hubs)

### Motors spin in wrong direction
- Use the Motors tab to test individual motors
- Swap any two of the three motor wires to reverse direction, or configure in BLHeli/AM32

## Need Help?

- Visit [AutomataNexus.com](https://NexusFlight.AutomataNexus.com)
- Email: devops@automatanexus.com
- Open an issue: [GitHub Issues](https://github.com/AutomataNexus/NexusFlight-Suite/issues)
