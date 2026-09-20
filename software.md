---
layout: content
title: "Software & Setup Guide (Bookworm & Wayland)"
description: "Complete setup guide for Raspberry Pi OS Bookworm with Wayland, HDMI-CEC control via wtype, audio configuration, and Google Meet kiosk mode."
---

# Software & Setup Guide

This guide covers setting up **Raspberry Pi OS (Bookworm 64-bit with Wayland / labWC)**, automating your television with HDMI-CEC, configuring audio output, and launching Google Meet in kiosk mode.

<div class="callout callout-info">
  <div class="callout-title"><i class="fas fa-history"></i> Legacy OS Support</div>
  <p>Running the older Debian Bullseye release? Refer to our <a href="{{ '/software-bullseye' | relative_url }}">Legacy Bullseye Setup Guide</a>.</p>
</div>

---

## Step 1: Display & Kernel Configuration (Bookworm)

Edit `/boot/firmware/cmdline.txt` and `/boot/firmware/config.txt` to optimize display stability and route audio to HDMI.

### 1.1 Prevent labWC Crashes (Force HDMI Active)
To prevent labWC/Wayland from crashing when the TV is turned off, add the following parameter to the beginning of the line in `/boot/firmware/cmdline.txt`:

```ini
video=HDMI-A-1:1920x1200@60D
```

<div class="callout callout-tip">
  <div class="callout-title"><i class="fas fa-mouse"></i> Bluetooth Mouse Lag Fix</div>
  <p>If you experience lag with wireless mice, append <code>usbhid.mousepoll=0</code> to the end of <code>/boot/firmware/cmdline.txt</code> separated by a space.</p>
</div>

### 1.2 Disable 3.5mm Analog Audio (Force HDMI Audio Sink)
To prevent Raspberry Pi from routing audio to the 3.5mm AV headphone jack (`snd_bcm2835`), edit `/boot/firmware/config.txt`:

```bash
sudo nano /boot/firmware/config.txt
```

Add or update the following parameter under `[all]`:

```ini
dtparam=audio=off
```

Also disable CEC auto-init to prevent the TV from turning on upon system restart:

```ini
hdmi_ignore_cec_init=1
```

---

## Step 2: Audio & Locale Configuration

1. **System Locale**: Set the default system locale to `en_US.utf-8` using the configuration utility:
   ```bash
   sudo raspi-config
   ```
   Navigate to **Localisation Options &rarr; Locale &rarr; en_US.UTF-8**.

2. **Select HDMI Audio Output**:
   - Right-click the **Sound/Speaker** icon in the desktop top toolbar.
   - Under **Device Profiles**, set **Audio Jack** to `Off`. This instructs Wayland to use the connected HDMI display as the primary audio sink.
   - Select **HDMI** from the list of available audio output devices.
   - Right-click the **Microphone** icon to select your Logitech Brio webcam as the default input device.

3. **Audio Driver (PipeWire vs PulseAudio)**:
   - Bookworm uses PipeWire by default. If your television speakers do not produce sound, open `sudo raspi-config`, go to **Advanced Options &rarr; Audio Config**, and switch the audio subsystem from **PipeWire** to **PulseAudio**.

4. **Disable Screen Blanking**:
   - In **Raspberry Menu &rarr; Preferences &rarr; Raspberry Pi Configuration &rarr; Display**, turn **Screen Blanking** to **Disabled**.

---

## Step 3: Install HDMI-CEC & Wayland Input Utilities

Install `cec-utils` for TV control and `wtype` (the Wayland virtual keystroke tool that replaces X11's `xautomation`):

```bash
sudo apt-get update
sudo apt-get install -y cec-utils wtype
```

### Grant Non-Root Permissions for CEC
Create `/etc/udev/rules.d/50-udev-default.rules` so the `pi` user can access the CEC hardware bus:

```bash
echo 'KERNEL=="cec*", GROUP="pi", OWNER="pi"' | sudo tee -a /etc/udev/rules.d/50-udev-default.rules
sudo udevadm control --reload-rules && sudo udevadm trigger
```

---

## Step 4: Create the TV Automation Script

Create `/usr/local/bin/tv` to control television power and input switching via simple terminal commands:

```bash
sudo nano /usr/local/bin/tv
```

Paste the following script:

```bash
#!/bin/bash
# /usr/local/bin/tv - HDMI-CEC Control Script for CallOnTV

case $1 in
  on)
    echo 'Waking TV from standby...'
    echo 'on 0' | cec-client -s -d 1
    ;;
  hdmi)
    echo 'Switching TV to Raspberry Pi HDMI input...'
    echo 'as' | cec-client -s -d 1
    ;;
  status)
    echo 'Checking TV power status...'
    echo 'pow 0' | cec-client -s -d 1
    ;;
  off)
    echo 'Putting TV in standby...'
    echo 'standby 0' | cec-client -s -d 1
    ;;
  scan)
    echo 'Scanning HDMI-CEC devices on the bus...'
    echo 'scan' | cec-client -s -d 1
    ;;
  *)
    echo "Usage: tv {on|hdmi|off|status|scan}"
    exit 1
    ;;
esac
```

Make the script executable:

```bash
sudo chmod +x /usr/local/bin/tv
```

### Test Your TV Script
Verify CEC communication with your TV:

```bash
tv scan    # Verify communication with the TV CEC bus
tv on      # Powers on the television
tv hdmi    # Switches active video input to the Raspberry Pi
tv status  # Reports power status (standby vs on)
tv off     # Powers off the TV into standby mode
```

---

## Step 5: Python Virtual Environment & Kiosk Autostart

Raspberry Pi OS Bookworm enforces PEP 668 managed Python environments. Create a dedicated virtual environment for automation scripts:

```bash
python3 -m venv /home/pi/python
/home/pi/python/bin/pip install pychrome requests
```

### Chromium Kiosk Autostart
Configure Chromium to open your Google Meet room automatically on boot in kiosk mode:

Create `~/.config/autostart/callontv.desktop`:

```ini
[Desktop Entry]
Type=Application
Name=CallOnTV
Exec=chromium-browser --noerrdialogs --disable-infobars --kiosk "https://meet.google.com/your-room-id"
```

For official Raspberry Pi kiosk tutorials, see the [Raspberry Pi Kiosk Mode Documentation](https://www.raspberrypi.com/tutorials/how-to-use-a-raspberry-pi-in-kiosk-mode/).

---

## Step 6: Install CallOnTV Chrome Extension

To automate joining Google Meet calls without requiring a mouse, install the [CallOnTV Chrome Extension]({{ '/extension' | relative_url }}) (source available on [GitHub](https://github.com/callontv/googlemeet-extension)).
