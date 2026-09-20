---
layout: content
title: "Hardware Guide"
description: "Recommended hardware checklist featuring Raspberry Pi 500 (integrated cooling), Logitech MX Brio 90° webcam, and HDMI-CEC television compatibility."
---

# Hardware Requirements

To build a dedicated CallOnTV terminal, you need a single-board computer (such as the all-in-one **Raspberry Pi 500** or **Raspberry Pi 5**), a high-quality wide-angle webcam (**Logitech MX Brio**), and an HDMI-CEC compatible television.

---

## 1. Computer Selection: Raspberry Pi 500 vs Pi 5 vs Pi 4

<div class="callout callout-success">
  <div class="callout-title"><i class="fas fa-star"></i> Top Recommendation: Raspberry Pi 500</div>
  <p>We strongly recommend the <strong>Raspberry Pi 500</strong> for the easiest living room setup. Its all-in-one keyboard design features a massive integrated internal cooling plate that <strong>completely eliminates the need for buying a separate case, heatsinks, or noisy cooling fans</strong>. It runs whisper-quiet under continuous 1080p Google Meet video calls and includes a built-in keyboard for hassle-free first-time Wi-Fi and account login.</p>
</div>

| Form Factor | Model | Cooling Setup Required | Why Choose It |
|:---|:---|:---|:---|
| **All-in-One (Recommended)** | **Raspberry Pi 500** | **None (Built-in passive heatsink)** | Plug-and-play ease of use; no case assembly, silent passive cooling, built-in keyboard. |
| **Modular Compact** | **Raspberry Pi 5** (4GB / 8GB) | Active Cooler or Aluminum Case required | Maximum raw computing power in a tiny credit-card footprint tucked behind the TV. |
| **Budget Modular** | **Raspberry Pi 4B** (4GB / 8GB) | Heatsink + Quiet 5V Fan | Inexpensive, widely available, easily handles 1080p Google Meet video playback. |

---

## 2. Hardware Checklist

| Item | Component | Recommendation | Estimated Price | Purpose |
|:---|:---|:---|:---|:---|
| **1** | **Computer** | **Raspberry Pi 500** (or Pi 5 / Pi 4B 4GB+) | ~$70 – $90 | Hardware video decode for 1080p Google Meet and HDMI-CEC automation. |
| **2** | **Webcam** | **Logitech MX Brio 4K** (or Brio 4K) | ~$170 – $199 | **90° FOV** captures the whole sofa; dual beamforming far-field mics pick up room audio. |
| **3** | **MicroSD Card** | 32GB+ SanDisk Extreme or Samsung EVO Plus | ~$10 – $15 | High random-write IOPS ensures responsive OS operation. |
| **4** | **Power Supply** | Official 27W (Pi 500/Pi 5) or 15W (Pi 4) USB-C Adapter | ~$12 – $15 | Stable power prevents under-voltage CPU throttling. |
| **5** | **HDMI Cable** | Micro-HDMI to HDMI 2.0 Cable | ~$8 – $12 | Carries high-definition video and digital HDMI-CEC control signals. |
| **6** | **Cooling** | Built-in on Pi 500; Passive case for Pi 5/4 | $0 (Pi 500) / ~$15 | Keeps thermals under 60°C during extended living room family calls. |

---

## 3. Webcam Selection: Why Logitech MX Brio is the Best

<div class="callout callout-tip">
  <div class="callout-title"><i class="fas fa-video"></i> Living Room Camera Recommendation: Logitech MX Brio</div>
  <p>The <strong>Logitech MX Brio</strong> is our top recommended webcam for CallOnTV. Standard desktop webcams (65° to 78° FOV) create a "tunnel vision" effect that cuts off people sitting on either end of the living room sofa. The MX Brio provides a true <strong>90° diagonal field of view</strong>, an advanced <strong>Sony STARVIS sensor</strong> for dim evening living room lighting, and <strong>dual beamforming noise-reducing microphones</strong> tuned for room acoustics.</p>
</div>

| Camera Model | Field of View (FOV) | Microphone Quality | Living Room TV Suitability |
|:---|:---|:---|:---|
| **Logitech MX Brio (4K)** | **90° / 78° / 65° adjustable** | Advanced dual beamforming noise-reducing mics | <span class="badge-pill badge-success">Top Recommendation (Best Optics & Audio)</span> |
| **Logitech Brio 4K** | **90° wide FOV** | Dual omnidirectional mics with noise suppression | <span class="badge-pill badge-success">Highly Recommended</span> |
| **Logitech C930e** | **90° wide FOV** | Dual stereo omnidirectional mics | <span class="badge-pill badge-success">Recommended (Budget 90° FOV)</span> |
| **Logitech C920 / C922** | 78° narrow FOV | Standard stereo mics | <span class="badge-pill badge-neutral">Usable for small rooms</span> |
| **Standard Webcams (C270/C310)** | 55° – 60° narrow | Basic mic | <span class="badge-pill badge-danger">Not Recommended (Too narrow)</span> |

---

## 4. Television & HDMI-CEC Compatibility

CallOnTV uses **HDMI-CEC (Consumer Electronics Control)** via `cec-utils` and Wayland input automation. This protocol allows the Raspberry Pi to automatically wake your TV from standby and switch the video input to HDMI when a call starts.

### HDMI-CEC Brand Names
Different TV manufacturers use proprietary marketing names for HDMI-CEC. Ensure this setting is enabled in your TV menu:
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

## 5. Power & Bandwidth Requirements

### Measured Power Consumption
CallOnTV is remarkably energy-efficient compared to keeping a PC or commercial meeting room device running.

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
With your hardware selected, proceed to the [Software Setup Guide]({{ '/software' | relative_url }}) to configure Raspberry Pi OS, HDMI-CEC control scripts, and Google Meet integration.