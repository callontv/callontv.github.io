---
layout: content
title: "Chrome Extension"
description: "Overview and installation instructions for the CallOnTV Chrome Extension to automate Google Meet joining and meeting management."
---

# CallOnTV Chrome Extension

The **CallOnTV Chrome Extension** automates meeting interactions inside the Chromium browser on your Raspberry Pi, removing the need for a keyboard or mouse during daily operation.

---

## Key Features

<div class="feature-grid">
  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-sign-in-alt"></i>
    </div>
    <h3 class="feature-title">One-Click Auto-Join</h3>
    <p class="feature-text">
      Automatically clicks "Join Now" as soon as your designated Google Meet room is reached, completely eliminating the pre-meeting waiting screen.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-user-check"></i>
    </div>
    <h3 class="feature-title">Auto-Admit Participants</h3>
    <p class="feature-text">
      Automatically admits recognized family members and callers knocking on the meeting door without requiring manual confirmation.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-tv"></i>
    </div>
    <h3 class="feature-title">TV Power Trigger</h3>
    <p class="feature-text">
      Coordinates with the local `/usr/local/bin/tv` automation daemon to ensure the television is awake and switched to HDMI when an active session begins.
    </p>
  </div>
</div>

---

## Installation Instructions

Follow these steps to install the extension on your Raspberry Pi's Chromium browser:

### Step 1: Download or Clone the Extension
Clone or download the extension from our [GitHub repository](https://github.com/callontv/googlemeet-extension) into a folder on your Raspberry Pi:

```bash
mkdir -p ~/callontv-extension
cd ~/callontv-extension
# Clone the extension repository
git clone https://github.com/callontv/googlemeet-extension.git .
```

### Step 2: Open Chromium Extensions
1. Launch the **Chromium Web Browser** on your Raspberry Pi.
2. In the URL address bar, enter:
   ```text
   chrome://extensions
   ```
3. Press **Enter**.

### Step 3: Enable Developer Mode
In the top-right corner of the Extensions page, toggle the **Developer mode** switch to **ON**.

### Step 4: Load Unpacked Extension
1. Click the **Load unpacked** button in the top-left toolbar.
2. Browse to and select the `~/callontv-extension` directory.
3. Click **Select Folder** (or **Open**).

The CallOnTV extension icon will appear in your browser's toolbar, confirming successful installation.

---

## Configuration & Testing

1. Click on the **CallOnTV** extension icon in the toolbar.
2. Ensure the **Auto-Join** and **Auto-Admit** toggles are switched **ON**.
3. Navigate to a test Google Meet room:
   ```text
   https://meet.google.com/new
   ```
4. Observe that the extension detects the pre-join screen, configures your preferred audio/video defaults, and automatically enters the call without clicking.

<div class="callout callout-tip">
  <div class="callout-title"><i class="fas fa-lightbulb"></i> Persistent Google Login</div>
  <p>Make sure you log into your Google Account once on Chromium and check <em>"Remember this device"</em> so credentials persist across system reboots.</p>
</div>