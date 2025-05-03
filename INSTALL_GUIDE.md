## RetroPie on Raspberry Pi 5 — Step-by-Step Installation Guide

### Overview

This guide walks you through installing RetroPie on the Raspberry Pi 5, which currently does not have an official prebuilt image. By manually installing RetroPie on top of Raspberry Pi OS (64-bit Bookworm), users can still enjoy emulation on the latest Pi hardware.

---

### 🧰 Requirements

* Raspberry Pi 5
* MicroSD card (32GB+ recommended, Class 10 or better)
* USB-C Power supply for Pi 5
* USB or Bluetooth game controller
* USB keyboard (for setup)
* HDMI display/TV
* Ethernet or Wi-Fi connection
* MicroSD card reader for your PC

---

### Step 1: Prepare the SD Card

1. **Download Raspberry Pi OS**
   Visit [Raspberry Pi OS downloads](https://www.raspberrypi.com/software/operating-systems/) and download:

   * **Raspberry Pi OS (64-bit) with desktop**

2. **Flash the OS to the SD card**
   Use [Raspberry Pi Imager](https://www.raspberrypi.com/software/) or [Balena Etcher](https://etcher.io).

3. **Initial Boot & System Update**
   Insert the SD card, power up the Pi, and open a terminal:

   ```bash
   sudo apt update && sudo apt full-upgrade -y
   ```

---

### Step 2: Install RetroPie Manually

1. **Install required packages**:

   ```bash
   sudo apt install -y git dialog unzip xmlstarlet
   ```

2. **Clone the RetroPie setup script**:

   ```bash
   git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
   cd RetroPie-Setup
   ```

3. **Run the setup**:

   ```bash
   sudo ./retropie_setup.sh
   ```

   * Choose `Basic Install`
   * Alternatively, install components individually under `Manage Packages`

---

### Step 3: Configure Controller & Load ROMs

1. On first boot into **EmulationStation**, follow the prompt to configure your controller.
2. Add your ROMs to `/home/pi/RetroPie/roms/[system_name]` using:

   * USB drive
   * SFTP/SSH (enable via `raspi-config`)

---

### Step 4: Auto-Boot into EmulationStation

1. Run:

   ```bash
   sudo raspi-config
   ```
2. Navigate to **System Options > Boot / Auto Login > Desktop Autologin**
3. Add to `.bashrc` to auto-start RetroPie:

   ```bash
   echo 'emulationstation' >> ~/.bashrc
   ```

---

### Step 5: Optional Enhancements

* Overclock the Pi 5 via `raspi-config` (if using active cooling)
* Install `xpadneo` for Xbox wireless controller support
* Add bezels, overlays, and shaders via RetroArch
* Backup your setup using tools like `rsync` or image the SD card with Win32 Disk Imager

---

### Notes

* Raspberry Pi 5 introduces a new architecture; some emulators may require additional tweaks
* Performance is excellent for most 8-bit and 16-bit systems, and good for many 32-bit

---

### Coming Soon

* Prebuilt RetroPie image for Pi 5
* GPU driver improvements
* Optimized emulator packages for the new SoC

---

*Last updated: May 2025*

For questions or contributions, contact \[[yourname@example.com](mailto:yourname@example.com)] or visit our GitHub page.
