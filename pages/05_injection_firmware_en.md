---
title: "📀 Firmware Injection"
nav_order: 5
permalink: /05_injection_firmware/
parent: "🏠 OpenMower Guide"
layout: default
---

# 📀 Mowgli Firmware Compilation & Injection

---

## 🗕️ Backup the original firmware

Before making any changes, back up your current firmware with an **ST‑LINK** (Optional – not necessary for Yardforce 500/500B).

<div class="alert-blue">
  <div class="alert-title">ℹ️ Original Yardforce 500/500B firmware</div>
  <p>Need the stock firmware? The official Yardforce 500/500B firmware is available here:<br>
  <a href="https://mega.nz/folder/icshEICL#QWDtu9Y2y_YmrNRwHSYzbA" target="_blank">🗕️ Download the Yardforce firmware</a></p>
</div>

**ST‑LINK wiring :**

<div style="text-align:center">
  <img src="{{ '/assets/img/branchement_stlink.jpg' | relative_url }}" alt="ST‑LINK wiring diagram" style="max-width: 400px; margin: auto;">
</div>

<div class="alert-blue">
  <div class="alert-title">🗕️ ST‑LINK Drivers (Windows) — STSW‑LINK009</div>
  <p>
    This USB driver is essential for ST‑LINK/V2, ST‑LINK/V2‑1 and STLINK‑V3 probes and their derivatives (Discovery kits, Nucleo boards, STM8/STM32 eval boards).<br><br>
    💻 It enables the system to recognise the ST‑LINK USB interfaces:<br>
    ✅ ST Debug<br>
    ✅ Virtual COM port<br>
    ✅ ST Bridge interfaces<br><br>
    ⚠️ Must be installed <strong>before</strong> connecting ST‑LINK/V2 and V2‑1.<br>
    🔹 Optional for STLINK‑V3 (but lets you customise virtual COM‑port names).<br><br>
    💎 <a href="https://mega.nz/folder/XEdGVTaB#KnQNzVhi9RzjMeEXjzvQ-g" target="_blank">Download link</a>
  </p>
</div>

<div class="alert-blue">
  <div class="alert-title">🛠️ Download STM32CubeProgrammer (STM32CubeProg)</div>
  <p>
    STM32CubeProgrammer is a cross‑platform all‑in‑one tool for programming STM32 products.<br><br>
    It offers an intuitive interface to read, write and verify MCU memory via:<br>
    🔹 Debug interfaces: JTAG & SWD<br>
    🔹 Bootloader interfaces: UART, USB DFU, I2C, SPI & CAN<br><br>
    With STM32CubeProgrammer you can:<br>
    ✅ Program internal (Flash, RAM, OTP) and external memories<br>
    ✅ Manage option bytes and verify content<br>
    ✅ Automate flashing via scripts<br><br>
    Available both as a GUI and CLI.<br><br>
    💎 <a href="https://mega.nz/folder/2ZMHjJhT#DXUiH4I_ma5rL42wuUkJ_Q" target="_blank">Download link</a>
  </p>
</div>

---

# 📀 1. Download the firmware

**For Yardforce 500**    
🧸 [GitHub – CEDBOSSNEO / Mowgli (main)](https://github.com/cedbossneo/Mowgli/tree/main)

**Direct link:** [ZIP](https://github.com/cedbossneo/Mowgli/archive/refs/heads/main.zip)

**For Yardforce 500B**    
🧸 [GitHub – Nekraus / Mowgli (yardforce‑500b)](https://github.com/Nekraus/Mowgli/tree/yardforce-500b)

**Direct link:** [ZIP](https://github.com/Nekraus/Mowgli/archive/refs/heads/yardforce-500b.zip)

<div class="alert-green">
  <div class="alert-title">✅ Note for Yardforce 500B users</div>
  <p>
    Nekraus’s firmware for the Yardforce 500B lets you use the mower’s original dashboard.<br>
    This keeps the display active and fully functional for a better user experience.
  </p>
</div>

---

# 🛠️ 2. Compile the firmware

<div class="alert-blue">
  <div class="alert-title">🎥 How‑to video: Compile the firmware</div>
  <p>Watch the video below :</p>

  <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; margin-top: 1rem;">
    <iframe src="https://www.youtube.com/embed/ID_COMPILATION_VIDEO" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position: absolute; top:0; left: 0; width: 100%; height: 100%;"></iframe>
  </div>
</div>

---

# 🚀 3. Flash the firmware

## 📁 Option 1 – Via Visual Studio Code

<div class="alert-blue">
  <div class="alert-title">🎥 How‑to video: Flash with VS Code</div>
  <p>Watch the video below :</p>

  <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; margin-top: 1rem;">
    <iframe src="https://www.youtube.com/embed/ID_VSCODE_VIDEO" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position: absolute; top:0; left: 0; width: 100%; height: 100%;"></iframe>
  </div>
</div>

## 📁 Option 2 – Via STM32CubeProgrammer

<div class="alert-blue">
  <div class="alert-title">🎥 How‑to video: Flash with STM32CubeProgrammer</div>
  <p>Watch the video below :</p>

  <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; margin-top: 1rem;">
    <iframe src="https://www.youtube.com/embed/ID_CUBEPROG_VIDEO" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position: absolute; top:0; left: 0; width: 100%; height: 100%;"></iframe>
  </div>
</div>

---

# 📚 Navigation

<div style="display: flex; justify-content: space-between; margin-top: 2rem;">
  <a href="{{ '/pages/sommaire/' | relative_url }}" class="btn">⬅️ Back to Table of Contents</a>
  <a href="{{ '/06_configuration_openmower/' | relative_url }}" class="btn">➡️ Next : OpenMower Configuration</a>
</div>

---
