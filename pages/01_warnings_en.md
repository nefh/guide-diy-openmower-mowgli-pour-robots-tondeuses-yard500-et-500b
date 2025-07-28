---
title: "⚠️ Warnings"
nav_order: 1
permalink: /01_avertissements/
parent: "🏠 OpenMower Guide"
layout: default
---

# ⚠️ Warnings ⚠️

<div class="alert-blue">
  <div class="alert-title">ℹ️ Introduction</div>
  Welcome to this detailed French‑language guide for configuring and assembling your OpenMower robot. Please note that it reflects my personal experience building the Yardforce 500B model.
</div>

---

## 🧩 Compatibility

This guide is specifically intended for:

- Yardforce 500 ✅
- Yardforce 500B ✅

These models must still use their original mainboard **(STM32 F103 or F402)**.  
It may also be partially compatible with other models that share the same board.

---

## 🚨 Limited functionality depending on the model

<div class="alert-orange">
  <div class="alert-title">🛑 Reduced functionality</div>
  The keyboard and the LEDs on the robot’s top cover <strong>may not work</strong> with this configuration, except in some cases noted below.
</div>

### Yardforce 500 :

- ✅ Lift sensor LED
- ✅ Low‑battery LED
- ✅ Charging LED  
These elements remain functional **without any firmware modification**.

### Yardforce 500B :

- 🆕 ✅ **Since Nekraus’s Mowgli firmware (25/04/2025)** :
  - Fully functional keypad ✅
  - Fully functional LEDs ✅

> If you use firmware other than Nekraus’s, panel functions may be limited.

---

## 🖥️ Yardforce panel silk‑screen (new)

You will soon find:

- 📷 A visual overview of the panel and button layout.
- 🖨️ A 3‑D printable model of the silk‑screen to modernise your robot.

[🔗 Go to the Wiring Diagram section]({{ '/pages/schema/' | relative_url }})

---

## ⚠️ Disclaimer

<div class="alert-red">
  <div class="alert-title">⚠️ Modifications at your own risk</div>
  Any software or hardware modification is performed <strong>at your own risk</strong>.  
  This may lead to:
  <ul>
    <li>Hardware degradation or failure</li>
    <li>Loss of the manufacturer’s warranty</li>
    <li>Unexpected robot behaviour</li>
  </ul>
  I accept no responsibility for any malfunction or damage resulting from the application of this guide.
</div>

---

## 📢 Continuous updates

<div class="alert-orange">
  <div class="alert-title">🔁 Guide in constant evolution</div>
  This guide is updated regularly. Some steps may change depending on new firmware versions or the components you are using.
  <br>
  👉 Remember to check the <a href="{{ '/mise_a_jour/' | relative_url }}">📝 Guide updates</a> page so you don’t miss anything.
</div>

[⬅ Back to home]({{ '/' | relative_url }}) | [📑 Go to the Table of Contents]({{ '/pages/sommaire/' | relative_url }})
