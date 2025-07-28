---
title: "❓ FAQ"
nav_order: 8
permalink: /08_faq/
parent: "🏠 OpenMower Guide"
layout: default
---

# ❓ FAQ

Frequently asked questions, common bugs and suggested fixes.

---

## 📚 Quick Table of Contents

- [🔌 Raspberry Pi USB ports](#-reset-raspberry-pi-usb-ports-without-reboot)
- [🛠️ ST‑Link detection issues in VSCode](#-vscode-does-not-detect-my-st-link-what-to-do)
- [📈 GPS disconnects](#-i-have-frequent-gps-disconnections-what-to-do)
- [🗺️ Map‑merging crashes](#-openmower-gui-crashes-when-i-merge-several-mowing-maps-why)
- [🚨 Yardforce dashboard firmware update](#-can-we-update-or-modify-the-yardforce-500-500b-dashboard-firmware)
- [⚡ Precautions before firmware flashing](#-what-precautions-should-be-taken-before-flashing-custom-firmware)
- [🌱 Correct GPS setup](#-how-to-know-if-my-gps-configuration-is-correct)
- [🔧 Using other GPS modules](#-can-i-use-a-different-gps-module-than-the-recommended-f9p)
- [⚙️ ttyAMA5 or GPS detection issues](#-why-cant-i-detect-my-devttyama5-or-gps-after-reboot)
- [🧹 Cleaning the robot](#-how-to-clean-my-robot-after-mowing)
- [🚀 Operating without GPS](#-can-we-mow-without-rtk-gps-connected)

---

# 🔄 Reset Raspberry Pi USB ports without reboot

<div class="alert-blue">
  <div class="alert-title">ℹ️ Extra info</div>
  <p>You can reset the Raspberry Pi USB ports without rebooting the whole OS—super handy if a robot or peripheral stops responding.</p>
</div>

## ✅ Soft method: reload USB modules (recommended)

```bash
sudo modprobe -r usbserial cdc_acm
sudo modprobe usbserial cdc_acm
```

Then:

```bash
ls /dev/ttyA*
dmesg | tail -30
```

## 🧰 Hard method: restart the USB controller

<div class="alert-red">
  <div class="alert-title">⚠️ Warning</div>
  <p>This command will reset <em>all</em> USB devices on the Pi (keyboard, mouse included if you’re using a local setup).</p>
</div>

```bash
echo '1-1' | sudo tee /sys/bus/usb/drivers/usb/unbind
sleep 2
echo '1-1' | sudo tee /sys/bus/usb/drivers/usb/bind
```

---

# 🛠️ VSCode does not detect my ST‑Link, what to do?

**Answer:**  
- Fully restart VSCode.  
- Check that the ST‑Link drivers (STSW‑LINK009) are installed.  
- If the issue persists, flash directly using STM32CubeProgrammer.

---

# 📈 I have frequent GPS disconnections, what to do?

**Answer:**  
- Use a shielded USB cable.  
- Connect the GND between GPS and Raspberry Pi properly.  
- Verify stable power supply to the GPS.

---

# 🗺️ OpenMower GUI crashes when I merge several mowing maps, why?

**Answer:**  
This is a known bug (GitHub issue #51).

Solution – delete the `map.bag` file:

```bash
cd mowgli-docker
sudo rm ./ros/map.bag
```

Then recreate the map or restore from a backup.

---

# 🚨 Can we update or modify the Yardforce 500/500B dashboard firmware?

<div class="alert-red">
  <div class="alert-title">⚠️ Very important</div>
  <p><strong>Never modify or update the Yardforce 500/500B dashboard firmware!</strong><br>Always keep the stock firmware or you may brick your robot.</p>
</div>

---

# ⚡ What precautions should be taken before flashing custom firmware?

<div class="alert-blue">
  <div class="alert-title">💡 Safety tips</div>
  <ul>
    <li>Always back up the original firmware first.</li>
    <li>Double‑check all ST‑Link connections.</li>
    <li>Ensure the power supply is stable.</li>
  </ul>
</div>

---

# 🌱 How to know if my GPS configuration is correct?

**Answer:**  
- Ensure you have an RTK Fix (RTK Float or RTK Fix in OpenMower).  
- The displayed accuracy should be below 1 m.  
- If the fix is poor, check wiring, power or the antenna.

---

# 🔧 Can I use a different GPS module than the recommended F9P?

**Answer:**  
- Yes, but it <strong>must</strong> support RTK (Real‑Time Kinematic) mode to achieve the required precision for OpenMower.  
- Tested modules: Ardusimple F9P, UM982 (with specific setup).

---

# ⚙️ Why can’t I detect my /dev/ttyAMA5 or my GPS after reboot?

**Answer:**  
- The Raspberry Pi can sometimes remap ports.  
- Solution: check UART wiring, GPS power, and make sure `/boot/firmware/config.txt` contains `enable_uart=1` and `dtoverlay=uart5`.

---

# 🧹 How to clean my robot after mowing?

**Answer:**  
- Use a soft brush.  
- Never use a direct water jet on the motors or electronics.  
- Clean the weighted wheels and remove debris under the shell.

---

# 🚀 Can we mow without RTK GPS connected?

**Answer:**  
- No. OpenMower requires ultra‑precise GPS positioning to function correctly.  
- Without an RTK Fix, the trajectory will be inaccurate and unsafe for both robot and surroundings.

---

<div style="display: flex; justify-content: space-between; margin-top: 2rem;">
  <a href="{{ '/07_bonus/' | relative_url }}" class="btn">⬅️ Back : 3D Parts & Firmwares Bonus</a>
  <a href="{{ '/10_liens_utiles/' | relative_url }}" class="btn">➡️ Next : Useful Links</a>
</div>

---
