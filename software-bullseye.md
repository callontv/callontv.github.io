---
layout: content
title: "Software & Setup Guide (Legacy Bullseye)"
description: "Legacy setup guide for Raspberry Pi OS Bullseye (X11), cec-utils, and xautomation."
---

# Software & Setup Guide (Legacy Bullseye)

This page provides the configuration instructions for older Raspberry Pi OS **Bullseye (X11)** installations. For the current release, see our [Bookworm & Wayland Setup Guide]({{ '/software' | relative_url }}).

---

## 1. Display & Boot Configuration

Add the following to `/boot/config.txt`:

```ini
# Fix HDMI Audio and set HDMI to always active
hdmi_force_hotplug=1
hdmi_drive=2

# Disable CEC init to prevent TV turning on during reboot
hdmi_ignore_cec_init=1

# Optional overclocking for Raspberry Pi 4
over_voltage=6
arm_freq=2000
gpu_freq=700
```

Disable `xcompmgr` composition manager to reduce screen tearing:

```bash
sudo mv /etc/xdg/autostart/xcompmgr.desktop /home/pi/backup.xcompmgr.desktop
```

---

## 2. Install HDMI-CEC & X11 Automation

```bash
sudo apt-get update
sudo apt-get install -y cec-utils xautomation
```

Grant permissions in `/etc/sudoers.d/pi`:

```bash
echo "pi ALL=(ALL) NOPASSWD:SETENV: /usr/bin/xte" | sudo tee /etc/sudoers.d/pi
```

And in `/etc/udev/rules.d/50-udev-default.rules`:

```bash
echo 'KERNEL=="cec*", GROUP="pi", OWNER="pi"' | sudo tee -a /etc/udev/rules.d/50-udev-default.rules
sudo udevadm control --reload-rules && sudo udevadm trigger
```

---

## 3. TV Control Script

Create `/usr/local/bin/tv`:

```bash
#!/bin/bash
case $1 in
  on)     echo 'on 0' | cec-client -s -d 1 ;;
  hdmi)   echo 'as' | cec-client -s -d 1 ;;
  status) echo 'pow 0' | cec-client -s -d 1 ;;
  off)    echo 'standby 0' | cec-client -s -d 1 ;;
  scan)   echo 'scan' | cec-client -s -d 1 ;;
  *)      echo "Usage: tv {on|hdmi|off|status|scan}" ;;
esac
```

```bash
sudo chmod +x /usr/local/bin/tv
```

---

## 4. Python Dependencies

```bash
pip3 install selenium pychrome requests
```

Set Chromium's default page to your designated Google Meet URL and configure the [CallOnTV Chrome Extension]({{ '/extension' | relative_url }}).
