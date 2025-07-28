---
title: "⚙️ OpenMower Configuration"
nav_order: 6
permalink: /06_configuration_openmower/
parent: "🏠 OpenMower Guide"
layout: default
---

# ⚙️ OpenMower Configuration

---

## Initial robot start‑up configuration

Congratulations—your OpenMower Mowgli robot mower is now pre‑configured and almost ready to roll! All that remains is to set up the GPS, adjust the application settings and create your mowing maps.

---

<div class="alert-red">
  <div class="alert-title">⚠️ Important</div>
  <p>Only change the parameters explicitly mentioned in this guide. Any undocumented change may cause the apps—or the robot itself—to malfunction.</p>
</div>

---

## 📡 1. GPS configuration (RTK F9P or similar)

Follow the <a href="https://openmower.de/docs/robot-assembly/prepare-the-parts/prepare-the-gps/" target="_blank">official OpenMower instructions</a> to configure your GPS board.

**TODO :** For the UM982 module, follow <a href="https://wiki.openmower.de/index.php?title=Unicore_GPS_modules" target="_blank">this specific documentation</a>.

---

## 🖥️ 2. Robot configuration via the OpenMower App

You should now have access to both of these interfaces:

```plaintext
Advanced interface (PC):
http://raspberry‑pi‑ip:4006
```

```plaintext
Simplified interface (Smartphone/Tablet):
http://raspberry‑pi‑ip:4005
```

<div class="alert-red">
  <div class="alert-title">⚠️ Important</div>
  <p>To minimise errors, do the configuration on the “4006” page using a computer rather than a phone.</p>
</div>

![OpenMower app screenshot]({{ '/assets/img/openmower_app_capture1.png' | relative_url }})

### 2.1 Enter the GPS coordinates of your property (Datum)

Use a site like <a href="https://www.coordonnees-gps.fr/" target="_blank">Coordonnées‑GPS.fr</a> to obtain your latitude and longitude.

![OpenMower GPS coordinates]({{ '/assets/img/coordonnees_gps_openmower.png' | relative_url }})

### 2.2 NTRIP configuration (real‑time GPS correction)

Change **only** the **“NTRIP server endpoint”** field.

Use this site to find a base station near you: <a href="https://lvawebprojects.ovh/rtk/rtk.php" target="_blank">Available RTK bases</a>.

![NTRIP configuration]({{ '/assets/img/ntrip_config_openmower.png' | relative_url }})

<div class="alert-red">
  <div class="alert-title">⚠️ Privacy</div>
  <p>For your own safety, never share your actual GPS position.</p>
</div>

---

## 🛠️ TODO : Remaining OpenMower configuration

### 🛠️ “Mower” section
> ***To be completed...***

![Image placeholder]({{ '/assets/img/mower_section_placeholder.png' | relative_url }})

### 🛠️ “Positioning” section
> ***To be completed...***

![Image placeholder]({{ '/assets/img/positioning_section_placeholder.png' | relative_url }})

### 🛠️ “Docking” section
> ***To be completed...***

![Image placeholder]({{ '/assets/img/docking_section_placeholder.png' | relative_url }})

---

## 🗺️ 3. Creating and saving the mowing map

Refer to the official OpenMower documentation:

➡️ <a href="https://openmower.de/docs/software-setup/record-a-map/" target="_blank">Create and record a map (record‑a‑map)</a>

> ***A concise, step‑by‑step summary is being added here...***

<div class="alert-red">
  <div class="alert-title">⚠️ Key tip</div>
  <p>If you edit your map after the first mow, restart the Docker containers so the changes are taken into account.</p>
  <p>💾 Back up your map regularly if you make major modifications.</p>
</div>

---

# 📚 Navigation

<div style="display: flex; justify-content: space-between; margin-top: 2rem;">
  <a href="{{ '/pages/sommaire/' | relative_url }}" class="btn">⬅️ Back to Table of Contents</a>
  <a href="{{ '/07_bonus/' | relative_url }}" class="btn">➡️ Next : 3D Parts & Firmware Bonus</a>
</div>

---
