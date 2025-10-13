# 🎮 Linux Gaming Guide — Play Windows Games on Linux Like a Pro!

Welcome to the **ultimate guide for gaming on Linux**!  
Here you’ll learn how to **install, configure, and use** tools like **Wine**, **ProtonUp-Qt**, and **Lutris** to play your favorite **Windows games** seamlessly on Linux.

---

## 🧩 Table of Contents

1. [Introduction](#-introduction)
2. [Requirements](#-requirements)
3. [Install Wine](#-install-wine)
4. [Install ProtonUp-Qt](#-install-protonup-qt)
5. [Install Lutris](#-install-lutris)
6. [Configure and Manage Runners](#-configure-and-manage-runners)
7. [Add and Play Windows Games](#-add-and-play-windows-games)
8. [Optional: Vulkan Drivers (For Better Performance)](#-optional-vulkan-drivers-for-better-performance)
9. [Troubleshooting](#-troubleshooting)
10. [Resources](#-resources)

---

## 🚀 Introduction

Linux gaming has evolved tremendously — thanks to **Proton**, **Wine**, and **Lutris**, you can now play thousands of Windows games directly on Linux with minimal setup.

These tools work together to give you the best possible experience:

- **Wine** → Translates Windows API calls into Linux system calls.  
- **ProtonUp-Qt** → Manages custom **Proton-GE** or **Lutris-GE** builds (enhanced compatibility).  
- **Lutris** → A powerful open gaming platform that integrates Steam, Epic Games, GOG, and manual installations.

---

## 🧰 Requirements

Make sure you have the following before proceeding:

- 🐧 A Linux distribution (e.g. Ubuntu, Pop!_OS, Fedora, Arch, etc.)
- ⚙️ GPU Drivers (NVIDIA or AMD)
- 🌐 Internet connection
- 🎮 A passion for gaming 😄

---

## 🍷 Install Wine

Wine allows you to run Windows executables (`.exe`) directly on Linux.

### 🔹 On Ubuntu / Pop!_OS:

```bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install wine64 wine32
```

### 🔹 Check version:

```bash
wine --version
```

If you see something like `wine-9.0` or newer, you’re ready to go!

---

## 🧙‍♂️ Install ProtonUp-Qt

**ProtonUp-Qt** lets you easily install and manage **custom Proton** and **Lutris runners** like **Proton-GE** (GloriousEggroll build) which improves compatibility and performance.

### 🛠️ Install on Ubuntu / Pop!_OS:

```bash
sudo apt install flatpak
flatpak install flathub net.davidotek.pupgui2
```

### ▶️ Launch:

```bash
flatpak run net.davidotek.pupgui2
```

You’ll see a clean interface where you can:

- Select **Lutris** or **Steam**

- Click **“Install Version”**

- Choose the latest **Proton-GE** or **Lutris-GE**

These custom builds appear automatically in **Lutris** or **Steam**.

## 🐉 Install Lutris

Lutris is your **gaming library manager** — it centralizes all your games, no matter where they come from.

### 🔹 Installation (Ubuntu / Pop!_OS):

```bash
sudo add-apt-repository ppa:lutris-team/lutris
sudo apt update
sudo apt install lutris
```

### 🔹 Check installation:

```bash
lutris --version
```

## ⚙️ Configure and Manage Runners

Once Lutris is installed:

1. Open **Lutris**.

2. Go to **Preferences → Runners**.

3. Enable **Wine**, **Proton**, or **Lutris-GE** runners.

4. Use **ProtonUp-Qt** to install the latest custom versions.

> 💡 Tip: “Runners” are like engines that make your games work — always keep them updated.

## 🎮 Add and Play Windows Games

You can add Windows games manually or from supported stores.

### 🧭 Method 1: Add a Local Installer

If you’ve downloaded a `.exe` or `.msi`:

1. Open **Lutris** → Click ➕ **Add Game**

2. Under **Game Info**, set:
   
   - **Name:** Your game’s name
   
   - **Runner:** `Wine`

3. Under **Game options**:
   
   - **Executable:** Browse to your `.exe` installer

4. Click **Save** → Then **Play**

Lutris will launch the Windows installer under Wine!

---

### 🧩 Method 2: Add from Lutris.net Library

1. Visit https://lutris.net/games/

2. Search your game (e.g., *Monster Hunter World* or *Genshin Impact*)

3. Click **Install** → It will open directly in Lutris with a preconfigured setup

---

### 🕹️ Method 3: Add Steam Games (Non-Native)

If your Steam version is Linux-based:

1. Open Steam → Go to **Settings → Compatibility**

2. Check **“Enable Steam Play for all titles”**

3. Choose your installed **Proton-GE** version

4. Install any Windows-only game — it’ll work!

---

## 🧠 Optional: Vulkan Drivers (For Better Performance)

Vulkan provides faster, low-level GPU performance and is **strongly recommended** for modern gaming.

### 🔹 Install Vulkan (NVIDIA):

```bash
sudo apt install nvidia-driver-535 nvidia-vulkan-icd
```

### 🔹 Install Vulkan (AMD):

```bash
sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

### 🔹 Verify:

```bash
vulkaninfo | less
```

---

## 🧰 Troubleshooting

| Issue             | Solution                                                          |
| ----------------- | ----------------------------------------------------------------- |
| Game won’t start  | Try a different **Proton-GE** or **Wine** version via ProtonUp-Qt |
| Black screen      | Check **Vulkan drivers** or disable DXVK in settings              |
| Crashes / freezes | Enable **esync/fsync** in Lutris runner options                   |
| No audio          | Run `winecfg` → Audio tab → Select `PulseAudio`                   |
