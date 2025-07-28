---
title: "🧰 Required hardware"
nav_order: 2
parent: "🏠 OpenMower Guide"
layout: default
---

# 🧰 Required hardware

This project is based on using the **original** mainboard from the **Yardforce 500 / 500B** models, without any deep hardware modification to it. Below is the equipment I have personally used, tested and validated to build my autonomous mower robot.

---

### 🧰 Recommended parts list

| Equipment | References / Useful links | Remarks |
|-----------|----------------------------|-----------|
| 🧠 **Raspberry Pi 4** | [Kubii](https://www.kubii.com/fr/370-raspberry-pi-4-pi-400/)<br>[Amazon](https://amzn.eu/d/hwgFRWU) | Pi 4 recommended for performance |
| ⚡ **LM2596S Power Module** | [Amazon](https://amzn.eu/d/jhNev6j)<br>[AliExpress](https://fr.aliexpress.com/item/32991657981.html)<br>[Conrad](https://www.conrad.fr/) | Converts 24 V to 5 V |
| 📡 **F9P RTK GPS (Ardusimple)** | [Ardusimple](https://fr.ardusimple.com/product/simplertk2b/?attribute_pa_header-options=without-headers)<br>[AliExpress](https://fr.aliexpress.com/item/1005004690761874.html)<br>[Tindie](https://www.tindie.com/) | Essential for centimetric accuracy |
| 📶 **GNSS antenna (BT560 or BT603)** | [AliExpress BT560](https://fr.aliexpress.com/item/32991527632.html)<br>[AliExpress BT603](https://fr.aliexpress.com/item/32991527632.html) | BT603 offers higher gain |
| 🔌 **SMA antenna cable** | [AliExpress](https://fr.aliexpress.com/item/1005004690761874.html)<br>[Amazon](https://www.amazon.fr/) | Connects GPS to antenna |
| 🔗 **ST‑Link V2 (for firmware)** | [Amazon](https://www.amazon.fr/)<br>[AliExpress](https://fr.aliexpress.com/)<br>[Kubii](https://www.kubii.fr/) | Flashes the STM32 board |
| 🖥️ **Mobaxterm (SSH)** | [Mobaxterm](https://mobaxterm.mobatek.net/download-home-edition.html)<br>[Pi Connect](https://connect.raspberrypi.com) | Controls the Raspberry Pi |

---

<div class="alert-orange">
  <div class="alert-title">💡 Recommendation</div>
  Don’t forget to provide **stable Wi‑Fi coverage over the whole mowing area**. OpenMower Mowgli needs to stay permanently connected to the local network in order to operate properly.
</div>

---

## 🖨️ Custom 3D‑printed parts

Custom‑made parts (RPi mount, F9P mount, weighted wheels, beacon, etc.) have been **specially designed** for this project.

They are available **for free** on my MakerWorld profile:

👉 [Juditech3D MakerWorld profile](https://makerworld.com/en/@juditech3d)

For more details about the recommended files and prints:  
📦 [See the Bonus section]({{ '/07_bonus/' | relative_url }})

---

## 🖼️ Wiring diagram

Here is an overview of Mowgli’s complete wiring, created from the <a href="https://github.com/cedbossneo/mowgli-docker" target="_blank">cedbossneo</a> diagram, which I have **adapted for greater clarity**:

![Mowgli wiring diagram](../images/Diagramme%20sans%20nom.drawio.png)

> ✅ This diagram is also editable in `.drawio` format in the *schema* directory of the project: [See the interactive diagram]({{ '/schema/' | relative_url }})

---

<div class="alert-green">
  <div class="alert-title">🧠 Tip</div>
  If you don’t have a 3D printer, I can print the required parts for your project. Contact me on <a href="https://t.me/+mOlwROGsP3AyYTlk" target="_blank">Telegram</a> or via <a href="mailto:juditech3d@gmail.com">email</a>.
</div>
