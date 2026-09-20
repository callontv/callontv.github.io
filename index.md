---
layout: home
title: "Home"
description: "Turn your living room TV into a dedicated, hands-free video calling portal using Raspberry Pi 500 / Pi 5, HDMI-CEC automation, and Google Meet."
---

<!-- Hero Section with Setup Showcase Image -->
<section class="hero-section">
  <div class="hero-content">
    <div class="hero-grid">
      <div>
        <div class="hero-badge">
          <i class="fas fa-shield-alt"></i> Open Source & Self-Hosted
        </div>
        <h1 class="hero-title">
          Turn your living room TV into a <span class="gradient-text">hands-free video portal</span>
        </h1>
        <p class="hero-desc">
          A 55″+ TV at home and still squinting at small phones or laptops? CallOnTV harnesses the power of <strong>Raspberry Pi (Pi 500 or Pi 5)</strong>, <strong>HDMI-CEC automation</strong>, and <strong>Google Meet</strong> to bring life-sized, crystal-clear video calls to your living room.
        </p>
        <div class="hero-actions">
          <a href="{{ '/hardware' | relative_url }}" class="btn-cta-primary">
            <i class="fas fa-microchip"></i> Hardware Guide
          </a>
          <a href="{{ '/software' | relative_url }}" class="btn-cta-secondary">
            <i class="fas fa-terminal"></i> Software Setup
          </a>
          <a href="{{ '/extension' | relative_url }}" class="btn-cta-secondary">
            <i class="fab fa-chrome"></i> Chrome Extension
          </a>
        </div>
      </div>

      <!-- Real Living Room Setup Photo -->
      <div class="hero-image-card">
        <img src="{{ '/assets/img/home.jpg' | relative_url }}" alt="CallOnTV living room setup with wide-angle webcam mounted on television">
        <div class="hero-image-badge">
          <i class="fas fa-tv"></i> Living Room Setup with 90° FOV Camera
        </div>
      </div>
    </div>
  </div>
</section>

<!-- How It Works Flow Banner -->
<section class="flow-banner">
  <h2 class="flow-title">How CallOnTV Works</h2>
  <div class="flow-steps">
    <div class="flow-step-box">
      <div class="flow-step-icon"><i class="fas fa-tv"></i></div>
      <div class="flow-step-label">Living Room TV</div>
      <small style="color: var(--text-muted); font-size: 0.75rem;">HDMI-CEC Enabled</small>
    </div>
    <div class="flow-arrow"><i class="fas fa-arrow-right"></i></div>
    <div class="flow-step-box">
      <div class="flow-step-icon"><i class="fas fa-microchip"></i></div>
      <div class="flow-step-label">Raspberry Pi 500 / 5</div>
      <small style="color: var(--text-muted); font-size: 0.75rem;">CEC Daemon + Script</small>
    </div>
    <div class="flow-arrow"><i class="fas fa-arrow-right"></i></div>
    <div class="flow-step-box">
      <div class="flow-step-icon"><i class="fas fa-camera"></i></div>
      <div class="flow-step-label">Logitech MX Brio</div>
      <small style="color: var(--text-muted); font-size: 0.75rem;">90° FOV & Beamforming Mic</small>
    </div>
    <div class="flow-arrow"><i class="fas fa-arrow-right"></i></div>
    <div class="flow-step-box">
      <div class="flow-step-icon"><i class="fas fa-video"></i></div>
      <div class="flow-step-label">Google Meet</div>
      <small style="color: var(--text-muted); font-size: 0.75rem;">Chromium Browser</small>
    </div>
    <div class="flow-arrow"><i class="fas fa-arrow-right"></i></div>
    <div class="flow-step-box">
      <div class="flow-step-icon"><i class="fas fa-users"></i></div>
      <div class="flow-step-label">Lifelike Presence</div>
      <small style="color: var(--text-muted); font-size: 0.75rem;">Talk Face-to-Face</small>
    </div>
  </div>
</section>

<!-- Key Feature Cards -->
<section class="feature-grid">
  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-magic"></i>
    </div>
    <h3 class="feature-title">Automatic Power & Switching</h3>
    <p class="feature-text">
      With HDMI-CEC integration, your TV automatically wakes from standby and switches to the correct HDMI input when a call starts. No need to hunt for remote controls.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-heart"></i>
    </div>
    <h3 class="feature-title">Ideal for Parents & Elders</h3>
    <p class="feature-text">
      Designed with zero technical friction. Elderly parents or family members do not need to operate small touchscreens or remember logins—it just works right on their television.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-couch"></i>
    </div>
    <h3 class="feature-title">Truly Hands-Free Calling</h3>
    <p class="feature-text">
      Never hold a phone up to your face again. Relax on the sofa, cook dinner, or play with kids while enjoying crystal-clear room audio and a wide 90° living room camera view.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fab fa-google"></i>
    </div>
    <h3 class="feature-title">Standard Google Meet Quality</h3>
    <p class="feature-text">
      Utilizes Google Meet inside hardware-accelerated Chromium on Raspberry Pi OS. Anyone with a phone, laptop, or Google account can connect to your TV instantly.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-lock"></i>
    </div>
    <h3 class="feature-title">100% Private & Open Source</h3>
    <p class="feature-text">
      Runs entirely on hardware you own in your living room. No proprietary cloud tracking, subscription fees, or vendor lock-in. Full control over your setup.
    </p>
  </div>

  <div class="feature-card">
    <div class="feature-icon-wrapper">
      <i class="fas fa-leaf"></i>
    </div>
    <h3 class="feature-title">Ultra-Low Power Usage</h3>
    <p class="feature-text">
      Consumes only ~4W in idle standby mode and ~11W during active HD video calls. Keep it running 24/7 as an always-ready communication appliance for pennies a month.
    </p>
  </div>
</section>

<!-- Quick Setup Roadmap -->
<section style="margin-bottom: 3rem;">
  <div style="text-align: center; margin-bottom: 2rem;">
    <h2 style="font-size: 2rem; font-weight: 800; letter-spacing: -0.02em; margin-bottom: 0.5rem;">Quick Start Guide</h2>
    <p style="color: var(--text-muted); font-size: 1.05rem;">Three simple steps to build your living room video terminal</p>
  </div>

  <div class="row g-4">
    <div class="col-md-4">
      <div class="step-card h-100">
        <div class="step-header">
          <div class="step-number">1</div>
          <h3 class="step-title">Get the Hardware</h3>
        </div>
        <p style="color: var(--text-muted); font-size: 0.95rem;">
          Pick a Raspberry Pi 500 (integrated cooling) or Pi 5, a Logitech MX Brio 90° FOV webcam, a microHDMI cable, and check your TV for HDMI-CEC support.
        </p>
        <a href="{{ '/hardware' | relative_url }}" class="btn-cta-secondary" style="font-size: 0.875rem; padding: 0.5rem 1rem;">
          View Hardware Guide &rarr;
        </a>
      </div>
    </div>

    <div class="col-md-4">
      <div class="step-card h-100">
        <div class="step-header">
          <div class="step-number">2</div>
          <h3 class="step-title">Install Software</h3>
        </div>
        <p style="color: var(--text-muted); font-size: 0.95rem;">
          Flash Raspberry Pi OS Bookworm 64-bit, configure display and HDMI-CEC utilities (`cec-utils`, `wtype`), and set up the `/usr/local/bin/tv` automation daemon.
        </p>
        <a href="{{ '/software' | relative_url }}" class="btn-cta-secondary" style="font-size: 0.875rem; padding: 0.5rem 1rem;">
          View Software Guide &rarr;
        </a>
      </div>
    </div>

    <div class="col-md-4">
      <div class="step-card h-100">
        <div class="step-header">
          <div class="step-number">3</div>
          <h3 class="step-title">Automate & Call</h3>
        </div>
        <p style="color: var(--text-muted); font-size: 0.95rem;">
          Install the CallOnTV Chrome extension to automatically join your scheduled Google Meet sessions and enjoy seamless hands-free calling.
        </p>
        <a href="{{ '/extension' | relative_url }}" class="btn-cta-secondary" style="font-size: 0.875rem; padding: 0.5rem 1rem;">
          View Extension Guide &rarr;
        </a>
      </div>
    </div>
  </div>
</section>
