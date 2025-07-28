---
title: "🔗 Options"
nav_order: 11
permalink: /11_options_en/
parent: "🏠 OpenMower Guide"
layout: default
---

# 🔗 AVAILABLE OPTIONS

{: .toc }
* TOC
{:toc}

<div class="alert-red">
  <strong style="font-size: 1.2em;">⚠️ WARNING: Advanced Handling</strong><br>
  This page covers the modification of **critical** robot parameters. 
  <br><br>
  ❗ An incorrect configuration can cause malfunctions, damage your hardware, or compromise safety.  
  <br><br>
  👉 Only change these parameters if you fully understand their impact.
</div>

> ℹ️ This document gathers various **advanced options** that you can manually enable in the file `mowgli-docker/config/om/mower_config.sh`.
>
> ⚠️ **Caution**: Some options were collected from Telegram discussions. **They have not all been personally tested**.

---

## 🌧️ Rain Management

```bash
# Rain mode
#  0 - Ignore (Ignore rain)
#  1 - Dock (Return to dock as soon as rain is detected)
#  2 - Dock Until Dry (Dock + wait until dry)
#  3 - Pause Automatic Mode (Pause automatic mode until manual restart)
export OM_RAIN_MODE=0

# Waiting time after rain if mode "Dock Until Dry"
export OM_RAIN_DELAY_MINUTES=30
```

- **1** → Returns to the dock immediately upon rain detection. Leaves again when the battery is full *and* rain has stopped.
- **2** → Returns to the dock with a waiting time after rain.
- **3** → Pauses mowing; requires a manual restart.

---

## ⚙️ Other Known Options (untested)

| Variable | Description | Example |
|:---------|:------------|:--------|
| `OM_NO_CUTTING` | If set to **1**, the blade never spins | `export OM_NO_CUTTING=1` |
| `OM_BATTERY_CUT_OFF_VOLTAGE` | Automatic shutdown voltage | `export OM_BATTERY_CUT_OFF_VOLTAGE=21.5` |
| `OM_SPEED_NORMAL` | Normal speed in m/s | `export OM_SPEED_NORMAL=0.5` |
| `OM_SPEED_MAPPING` | Speed during map recording | `export OM_SPEED_MAPPING=0.4` |
| `OM_SPEED_DOCKING` | Speed while approaching the dock | `export OM_SPEED_DOCKING=0.3` |
| `OM_SPEED_MOWING` | Speed while mowing | `export OM_SPEED_MOWING=0.5` |
| `OM_TRACTION_CONTROL` | Enable/disable automatic slip management | `export OM_TRACTION_CONTROL=1` |

---

## 🔋 Charging & Battery Settings

<div class="alert-red">
  <div class="alert-title">⚠️ Important Warning</div>
  <p>Changing these settings can affect battery life or cause damage. Use with <strong>extreme caution</strong>.</p>
</div>

```bash
export MAX_CHARGE_CURRENT=1.0
export LIMIT_VOLTAGE_150MA=29.05
export MAX_CHARGE_VOLTAGE=29.2
export BAT_CHARGE_CUTOFF_VOLTAGE=29.15
export CHARGE_END_LIMIT_CURRENT=0.08
export MIN_CHARGE_CURRENT=0.1
```

---

## 🛞 Kinematic Parameters (robot movement)

```bash
export WHEEL_BASE=0.325
export MAX_MPS=0.5        # Max metres per second
export PWM_PER_MPS=300.0  # PWM per metre/second
export TICKS_PER_M=300.0  # Ticks per metre
```

---

## 🚨 Safety & Timeout

<div class="alert-red">
  <div class="alert-title">⚠️ Extreme Warning</div>
  <p>These settings manage robot safety (emergency stop, tilt detection, etc.). A wrong configuration can create dangerous situations. Use with <strong>extreme caution</strong>.</p>
</div>

```bash
export I_DONT_NEED_MY_FINGERS=0 # If set, disables motor safety (DANGER!)
export IMU_ONBOARD_INCLINATION_THRESHOLD=56  # Tilt threshold
export ONE_WHEEL_LIFT_EMERGENCY_MILLIS=10000  # One‑wheel lift time before alarm
export BOTH_WHEELS_LIFT_EMERGENCY_MILLIS=1000 # Two‑wheel lift time before alarm
export TILT_EMERGENCY_MILLIS=500
export STOP_BUTTON_EMERGENCY_MILLIS=100
export PLAY_BUTTON_CLEAR_EMERGENCY_MILLIS=2000
```

---

## 🔧 Additional Options

```bash
export EMERGENCY_DEBUG=0   # Enable emergency debug mode
export OPTION_BUMPER=0     # Enable bumper if sensor installed
export OPTION_ULTRASONIC=0 # Enable ultrasonic sensors if present
```

---

## 💡 Practical Examples

### ➡️ Example 1 : Force the mower to dock at the slightest rain

```bash
export OM_RAIN_MODE=1
export OM_RAIN_DELAY_MINUTES=0
```
The robot immediately returns to the dock if rain is detected.

---

### ➡️ Example 2 : Reduce speed while recording the map

```bash
export OM_SPEED_MAPPING=0.3
```
This enables more precise mapping by driving slowly.

---

### ➡️ Example 3 : Disable the blade during tests

```bash
export OM_NO_CUTTING=1
```
Useful for validating navigation without starting the blade motor.

---

📢 **Remember to save your `mower_config.sh` file after any modification to avoid data loss!** 🚀

👉 These advanced options let you further customise your robot—**use them with extreme caution** according to your hardware! 🚜

Feel free to check back, this page will be updated if more options are discovered!
