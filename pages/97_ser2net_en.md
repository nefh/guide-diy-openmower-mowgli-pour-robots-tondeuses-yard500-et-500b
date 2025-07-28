---
title: "🛠️ Ser2Net"
nav_order: 97
permalink: /97_ser2net_en/
parent: "🏠 OpenMower Guide"
layout: default
---

# 🛠️ Exposing Mowgli Robot Serial Ports with **Ser2Net**

> 🙏 *This tutorial was written by **Julien Guy**, based on the great work of [cedbossneo](https://github.com/cedbossneo/mowgli-docker.git) (original Docker‑Compose and documentation). Huge thanks to them for their invaluable contribution!*

---

## 📑 Quick Table of Contents

- [Objective](#-objective)
- [Prerequisites](#-prerequisites)
- [Observed Advantages](#-observed-advantages)
- [Implementation on the Raspberry Pi](#-1️⃣-on-the-raspberry-pi)
- [Implementation on the Remote Server](#-2️⃣-on-the-remote-server-vm-debianubuntu)
- [Bonus : Configure the GPS in U‑center](#-bonus--configure-your-f9p-in-u-center)
- [Conclusion](#-✅-conclusion)

---

<div class="alert-red">
  <div class="alert-title">⚠️ Important Warning</div>
  <p><strong>Wi‑Fi connection:</strong> Poor Wi‑Fi reception can cause serial drop‑outs or RTK packet loss. Make sure you have a stable connection before using this method.</p>
</div>

---

# 🛠️ Objective

Run the OpenMower Docker containers on another machine (e.g. a Proxmox server) while **exposing the `/dev/gps` and `/dev/mowgli` serial ports over the network** thanks to **Ser2Net**.

---

# 📋 Prerequisites

- ✅ Comfortable with Linux, SSH and the command line  
- ✅ A dedicated machine or VM available (Debian/Ubuntu recommended)  
- ✅ Able to transfer files (SFTP/SCP)

---

# 🚀 Observed Advantages

- ⚡ Lower power consumption (possible to use a Pi Zero – in testing)  
- 🖥️ ROS computations off‑loaded to a more powerful machine  
- 💾 Less wear on the SD card  
- 🌐 Easier access to GPS configuration (e.g. U‑center)  
- 📦 Improved container management via Portainer or Dozzle  
- 🔁 Ultra‑fast container restarts (< 10 seconds)

---

# 🛠️ 1️⃣ On the Raspberry Pi

## ⏹️ Stop existing Docker containers

```bash
docker compose down
```

---

## 📂 Back up your mowing map

```bash
sudo cp ./ros/map.bag ~/backup_map.bag
```

---

## 🛠️ Create UDEV rules to name the devices

Edit or create `/etc/udev/rules.d/50-mowgli.rules` :

```bash
SUBSYSTEM=="tty" ATTRS{product}=="Mowgli", SYMLINK+="mowgli"
SUBSYSTEM=="tty" ATTRS{idVendor}=="1546" ATTRS{idProduct}=="01a9", SYMLINK+="gps"
SUBSYSTEM=="tty" ATTRS{idVendor}=="303a" ATTRS{idProduct}=="4001", SYMLINK+="gps"
```

---

## ⚙️ Install Ser2Net

```bash
sudo apt update
sudo apt install -y ser2net
sudo systemctl enable ser2net
```

---

## ✏️ Configure `/etc/ser2net.yaml`

```yaml
connection: &mowgli01
  accepter: tcp,4001
  enable: on
  options:
    banner: "ser2net - MOWGLI"
    kickolduser: false
    telnet-brk-on-sync: true
  connector: serialdev, /dev/mowgli, 115200n81,local

connection: &gps01
  accepter: tcp,4002
  enable: on
  options:
    banner: "ser2net - GPS"
    kickolduser: false
    telnet-brk-on-sync: true
  connector: serialdev, /dev/gps, 460800n81,local
```

---

## 🔄 Reboot the Raspberry Pi

```bash
sudo reboot
```

---

# 🛠️ 2️⃣ On the Remote Server (VM Debian/Ubuntu)

## 📥 Install Docker

```bash
curl -sSL https://get.docker.com | sh
```

---

## 📂 Clone *mowgli-docker*

```bash
git clone https://github.com/cedbossneo/mowgli-docker.git
cd mowgli-docker
```

---

## ⚙️ Edit the `.env` file

```env
ROS_IP=127.0.0.1
MOWER_IP=192.168.1.66
IMAGE=ghcr.io/cedbossneo/mowgli-docker:cedbossneo
```

---

## 🛠️ Add OpenMower‑GUI to `docker-compose.ser2net.yaml`

```yaml
gui:
  container_name: openmower-gui
  image: ghcr.io/cedbossneo/openmower-gui:master
  restart: unless-stopped
  network_mode: host
  privileged: true
  environment:
    ROS_IP: ${ROS_IP}
    ROS_MASTER_URI: http://${ROS_IP}:11311
    MOWER_CONFIG_FILE: /config/mower_config.sh
    DOCKER_HOST: unix:///var/run/docker.sock
    DB_PATH: /db
  depends_on:
    - roscore
  volumes:
    - /dev:/dev
    - ./config/db:/db
    - ./config/om:/config
    - /var/run/docker.sock:/var/run/docker.sock
```

---

## 🚀 Start the containers

```bash
docker compose -f docker-compose.ser2net.yaml up -d
```

---

# 🎯 Bonus : Configure your F9P via U‑center

To reconfigure your GPS :

1. **Stop the Docker containers** :

```bash
docker compose down
```

2. **Use U‑center** to connect to the Pi’s IP on port `4002`.

---

<div class="alert-red">
  <div class="alert-title">⚠️ Important</div>
  <p>After any GPS modification, make sure to reload the configuration in the firmware if needed!</p>
</div>

---

# ✅ Conclusion

This solution lightens the load on your Raspberry Pi, improves network performance, and delivers more reliable robot management.

---

<div style="text-align: center;">
<a href="{{ '/' | relative_url }}">⬅️ Back to Home</a>  
<br>
<a href="{{ '/pages/sommaire/' | relative_url }}">📑 Go to Table of Contents</a>
</div>
