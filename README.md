# 🐧 Linux Setup & Software Guide

> A complete guide to setting up and configuring your Linux system — from the first installation to essential software, drivers, and tools.  
> 💡 Ideal for **Pop!_OS**, **Ubuntu**, and other Debian-based distributions.

---

## ⚙️ 1. Initial Configuration After Installation

Once your system is installed, open a terminal (`Ctrl + Alt + T`) and follow these essential setup steps.

### 🔄 Update & Upgrade the System

Keep your system up to date with the latest packages:

`sudo apt update sudo apt upgrade -y`

---

### 📦 Install Common and Recommended Packages

Install useful packages and multimedia codecs:

`sudo apt install ubuntu-restricted-extras -y`

---

### 🧩 Reinstall or Update System76 Drivers

(Useful for Pop!_OS or System76 machines to fix or refresh drivers.)

`sudo apt install --reinstall system76-driver system76-dkms -y`

---

### 🎮 Install Gaming & Testing Tools

These tools improve gaming controller support and provide simple system tests.

`sudo apt install gamepad jhort stest-gtk -y`

---

### 🧱 Install Build Tools

For compiling and building software from source:

`sudo apt install cmake -y`

---

## 🧰 2. Post-Setup Software Collection

After configuring your base system, explore and install your favorite Linux apps from the **Software Collection** included in this repository.

📚 **Available Tools:**

- 🎮 **Lutris** — Game launcher

- ⚙️ **ProtonUp-Qt** — Manage Proton versions

- 🍷 **Wine** — Run Windows apps

- 📝 **MarkText** — Markdown editor

- 💻 **Visual Studio Code** — Source code editor

- 🤖 **Android Studio** — Android development

- 📥 **ABDownloadManager** — Download manager

- ▶️ **MPV** — Media player

- 💿 **DVX Player** — Video player

📂 See the full list here:  
👉 `Linux-Software.md`

---

## 🧡 3. Tips & Best Practices

- 🔒 **Always update** your system weekly:
  
  `sudo apt update && sudo apt upgrade -y`

- 🧹 **Clean up unused packages:**
  
  `sudo apt autoremove && sudo apt clean`

- 💾 **Backup regularly** using tools like **Timeshift** or **Deja Dup**.

- 🧰 **Check drivers and kernel updates** if hardware issues occur.

---

## 🧑‍💻 4. Contribution

Want to improve this repo or add your own setup steps?

- Fork this repository

- Add your configuration or software

- Submit a pull request 💪

---

## 📄 License

This repository is licensed under the **MIT License** — free to use and share.
