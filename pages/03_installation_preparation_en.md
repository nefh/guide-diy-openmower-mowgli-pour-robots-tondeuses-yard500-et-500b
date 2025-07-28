---
title: "💾 Installation & Preparation"
nav_order: 3
parent: "🏠 OpenMower Guide"
layout: default
permalink: /03_installation_preparation/
---

# 💾 Raspberry Pi Installation and Preparation

This section will guide you step‑by‑step through configuring your Raspberry Pi so it is ready to run the services required by OpenMower.

---

## 📀 Preparing the SD/SSD

First, you need to prepare your SD card or SSD with **Raspberry Pi OS Lite (64‑bit)**.

### 🔧 Steps:
- Use [**Raspberry Pi Imager**](https://www.raspberrypi.com/software/) to flash Raspberry Pi OS Lite (64‑bit).
- You can watch the video below to see how it’s done:

![Raspberry Pi Imager tutorial](https://github.com/juditech3D/Guide-DIY-OpenMower-Mowgli-pour-Robots-Tondeuses-Yard500-et-500B/blob/main/M%C3%A9dia/Tuto%20raspberry%20pi%20imager%20%E2%80%90%20R%C3%A9alis%C3%A9e%20avec%20Clipchamp.gif)

---

## 📡 Wi‑Fi and SSH configuration

To automatically connect your Raspberry Pi to a Wi‑Fi network and enable SSH at first boot, you have two options:

✅ Via Raspberry Pi Imager (easiest, shown in the GIF above)  
🔧 Or manually by editing files on the SD card

---

### ⚙️ Manual configuration: Wi‑Fi & SSH
<details>
<summary>📂 Click to expand</summary>

#### 1. Prepare the SD card

1. Flash the Raspberry Pi OS (64‑bit) image to the SD card using **Raspberry Pi Imager** or **Balena Etcher**  
2. Insert the card into your computer  
3. Open the `boot` partition (visible from Windows/macOS/Linux)  
4. Open a text editor (Notepad++, TextEdit, Nano…)

#### 2. Create the `wpa_supplicant.conf` file

```sh
country=FR
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="Your_SSID"
    psk="Your_Password"
    key_mgmt=WPA-PSK
}
```

#### 💡 For multiple networks:
```sh
network={
    ssid="First_SSID"
    psk="First_Password"
    key_mgmt=WPA-PSK
    priority=2
}

network={
    ssid="Second_SSID"
    psk="Second_Password"
    key_mgmt=WPA-PSK
    priority=1
}
```

---

#### 3. Enable SSH

Create an empty file named `ssh` (with no extension) in the `boot` partition.

---

#### 4. Save and eject

- Save the files  
- Properly eject the SD card or SSD  

</details>

---

## 🚀 Boot the Raspberry Pi and connect via SSH

Once the card is ready, insert it into the Raspberry Pi and connect the power supply (and Ethernet, optionally).

---

### 🔍 Find the Raspberry Pi’s IP address
<details>
<summary>📡 Click to expand</summary>

#### 🌐 Method 1 – From your router

- Open your router’s admin page (e.g. `192.168.1.1`)  
- Look for a device named **raspberrypi**

#### 🛠️ Method 2 – With [Advanced IP Scanner](https://www.advanced-ip-scanner.com/en/)

- Download it and scan your network  
- Look for a device named Raspberry Pi

![Advanced IP Scanner](https://github.com/juditech3D/Guide-DIY-OpenMower-Mowgli-pour-Robots-Tondeuses-Yard500-et-500B/blob/main/images/Advanced%20ip%20scanner/Advanced%20ip%20scanner.png)

</details>

---

### 🔑 Connect via SSH

Once you have the IP, connect via SSH using MobaXTerm, PuTTY or the command line:

```sh
ssh pi@192.168.X.XX
```

By default, the password is `raspberry`.

---

✅ Once connected, proceed to the software configuration of the system.
