---
layout: content
title: "Hardware Guide"
description: "Recommended hardware checklist, HDMI-CEC television compatibility, power consumption, and camera selection for CallOnTV."
---

# Hardware Requirements

To build a dedicated CallOnTV terminal, you need a single-board computer (Raspberry Pi), a wide-angle webcam, and an HDMI-CEC compatible television. Below is the complete hardware guide and purchasing recommendations.

---

## 1. Hardware Checklist

| Item | Component | Specification | Estimated Price | Notes |
|:---|:---|:---|:---|:---|
| **1** | **Raspberry Pi** | Raspberry Pi 4B (4GB or 8GB) or Pi 5 | ~$55 – $80 | 4GB RAM minimum required for smooth 1080p Google Meet video decoding. |
| **2** | **Webcam** | **Logitech Brio 4K** (or wide 90°+ FOV webcam) | ~$130 – $180 | **Critical**: Wide 90° FOV captures the whole sofa; dual noise-canceling mics pick up room voices. |
| **3** | **MicroSD Card** | 32GB+ SanDisk Extreme or Samsung EVO Plus | ~$10 – $15 | High read/write IOPS ensures responsive OS operation. |
| **4** | **Power Supply** | Official 15W (Pi 4) or 27W (Pi 5) USB-C Adapter | ~$10 – $15 | Avoid cheap unbranded phone chargers to prevent under-voltage throttling. |
| **5** | **HDMI Cable** | Micro-HDMI to HDMI 2.0 Cable | ~$8 – $12 | Connects Pi micro-HDMI port to your TV's CEC-enabled HDMI port. |
| **6** | **Cooling Case** | Aluminum Case or Heatsink + Quiet Fan | ~$10 – $20 | Keeps temperatures low during extended 1080p video calls. |
| **7** | **Powered USB Hub** *(Optional)* | TP-Link UH700 or similar powered hub | ~$25 – $35 | Recommended if powering multiple USB devices to avoid exceeding Pi port power limits. |

---

## 2. Webcam Selection: Why 90° FOV Matters

<div class="callout callout-tip">
  <div class="callout-title"><i class="fas fa-video"></i> Living Room Camera Recommendation</div>
  <p>We <strong>strongly recommend the Logitech Brio 4K</strong> (or any certified webcam with a true 90° or higher diagonal field of view and omnidirectional far-field microphones). Standard desktop webcams (65° to 78° FOV) are designed for a single user sitting 2 feet away from a desk; when mounted on top of a TV, they create a "tunnel vision" effect that cuts off everyone sitting on the sofa.</p>
</div>

| Camera Model | Field of View (FOV) | Far-Field Microphones | Living Room TV Suitability |
|:---|:---|:---|:---|
| **Logitech Brio 4K** | **90° / 78° / 65° adjustable** | Dual omnidirectional mics with noise suppression | <span class="badge-pill badge-success">Highly Recommended</span> |
| **Logitech C930e** | **90° wide FOV** | Dual stereo omnidirectional mics | <span class="badge-pill badge-success">Recommended (Budget)</span> |
| **Logitech C920 / C922** | 78° narrow FOV | Standard stereo mics | <span class="badge-pill badge-neutral">Usable for small rooms</span> |
| **Entry-level Webcams (C270/C310)** | 55° – 60° narrow | Basic mic | <span class="badge-pill badge-danger">Not Recommended</span> |

---

## 3. Television & HDMI-CEC Compatibility

CallOnTV uses **HDMI-CEC (Consumer Electronics Control)** via the `cec-utils` library. This protocol allows the Raspberry Pi to automatically wake your TV from standby and switch the video input to HDMI when a call starts.

### HDMI-CEC Brand Names
Different TV manufacturers use proprietary brand marketing names for HDMI-CEC. Look for this setting in your TV's system or inputs menu:
- **Sony**: BRAVIA Sync / BRAVIA Link
- **Samsung**: Anynet+
- **LG**: SimpLink
- **Philips**: EasyLink
- **Panasonic**: VIERA Link / EZ-Sync
- **Sharp**: Aquos Link
- **Toshiba**: Regza Link / CE-Link
- **TCL / Hisense**: CEC / HDMI Control

### Tested TV Compatibility Matrix

| Brand | Model | HDMI-CEC Support | Status |
|:---|:---|:---|:---|
| **Sony** | KD-49X8300C | Full Power & Input Switch | <span class="badge-pill badge-success"><i class="fas fa-check"></i> Supported</span> |
| **Samsung** | UA-55KU7970 | Full Power & Input Switch | <span class="badge-pill badge-success"><i class="fas fa-check"></i> Supported</span> |
| **Samsung** | UA-46F6450AMSHD | Full Power & Input Switch | <span class="badge-pill badge-success"><i class="fas fa-check"></i> Supported</span> |
| **Samsung** | UA-40D5950RM | Full Power & Input Switch | <span class="badge-pill badge-success"><i class="fas fa-check"></i> Supported</span> |
| **LG** | 43LK5730PVC | Full Power & Input Switch | <span class="badge-pill badge-success"><i class="fas fa-check"></i> Supported</span> |
| **Samsung** | UA-49K5890AWCHD | Firmware lacks CEC standby control | <span class="badge-pill badge-danger"><i class="fas fa-times"></i> Not Supported</span> |
| **Daewoo** | DLE-49H1800U | CEC hardware absent | <span class="badge-pill badge-danger"><i class="fas fa-times"></i> Not Supported</span> |

---

## 4. Power & Bandwidth Requirements

### Measured Power Consumption
CallOnTV is highly energy-efficient compared to keeping a dedicated PC or smart display on at all times.

<div class="stat-grid">
  <div class="stat-card">
    <div class="stat-val">~4 W</div>
    <div class="stat-label">Idle / Standby Mode</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">~11 W</div>
    <div class="stat-label">Active 1080p Google Meet Call</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">&lt; $0.50</div>
    <div class="stat-label">Estimated Monthly Electricity Cost</div>
  </div>
</div>

### Bandwidth Guidelines for Google Meet
Google Meet automatically adjusts video bitrate based on network conditions:

| Video Quality | Minimum Outbound Bandwidth | Minimum Inbound Bandwidth | Ideal Latency |
|:---|:---|:---|:---|
| **High Definition (1080p)** | 3.2 Mbps | 3.2 Mbps | &lt; 50 ms to 8.8.8.8 |
| **Standard Definition (720p)** | 1.5 Mbps | 2.0 Mbps | &lt; 100 ms |
| **Audio-Only Fallback** | 0.5 Mbps | 0.5 Mbps | &lt; 150 ms |

---

## Next Step: Software Setup
Once your hardware is assembled, proceed to the [Software Guide]({{ '/software' | relative_url }}) to configure Raspberry Pi OS, HDMI-CEC control scripts, and Google Meet integration.