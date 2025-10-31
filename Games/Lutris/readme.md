# 🎮 Lutris on Linux - Installation & Game Setup Guide

## 🧩 Overview

**Lutris** is an open-source gaming platform for Linux that helps you install, configure, and launch games from different sources — including Steam, GOG, Epic Games, Battle.net, and more.  
It supports both **native Linux games** and **Windows games** through **Wine**, **Proton**, and **other emulators**.

Using **Lutris** with **ProtonUp-Qt**, you can easily install and manage **custom Proton or Wine builds** (like GE-Proton), improving game compatibility and performance.

---

## 🖥️ 1. Installation

### 🐧 For Ubuntu / Debian-based Systems

```bash
sudo add-apt-repository ppa:lutris-team/lutris
sudo apt update
sudo apt install lutris
```

### 🐧 For Fedora

```bash
sudo dnf install lutris
```

### 🐧 For Arch / Manjaro

```bash
sudo pacman -S lutris
```

### 🐧 For OpenSUSE

```bash
sudo zypper install lutris
```

Or visit the official site:  
🔗 [Download Lutris](https://lutris.net/downloads)Or visit the official site:  


---

## 🧰 2. Installing Dependencies (Optional but Recommended)

To ensure maximum compatibility for Wine/Proton games:

```bash
sudo apt install wine winetricks gamemode mangohud vulkan-utils
```

Make sure you have your GPU drivers properly installed:

- **NVIDIA:** Install proprietary drivers.

- **AMD/Intel:** Mesa drivers are usually sufficient.

---

## 🕹️ 3. Launching Lutris

You can launch Lutris from your applications menu or via terminal:

```bash
lutris
```

Sign in with your Lutris account (optional) to sync your games library.

---

## 🎮 4. Adding Games to Lutris

There are two main ways to add games:

### 🔹 Option 1 — From Lutris.net

1. Go to [Games | Lutris](https://lutris.net/games).

2. Search for the game you want.

3. Click **"Install"**, then **"Open with Lutris"**.
   
   - This will automatically launch Lutris and start the installation script.

### 🔹 Option 2 — Manually Add a Game

1. Click the **“+”** button in Lutris → **Add Game**.

2. Fill in:
   
   - **Name:** Game title
   
   - **Runner:** Choose (e.g., Wine, Steam, etc.)
   
   - **Executable:** Browse and select the `.exe` or script

3. Apply and **Launch**.

---

## ⚙️ 5. Installing ProtonUp-Qt (to manage Proton/Wine builds)

### 🧩 Install via Flatpak (Recommended)

If you have Flatpak set up:

```bash
flatpak install flathub net.davidotek.pupgui2
```

Run it:

```bash
flatpak run net.davidotek.pupgui2
```

Or launch it from your applications menu (**ProtonUp-Qt**).

### 🧩 Alternative: Manual Install (if needed)

```bash
git clone https://github.com/DavidoTek/ProtonUp-Qt.git
cd ProtonUp-Qt
python3 protonup-qt.py
```

## 🚀 6. Using ProtonUp-Qt with Lutris


1. Open **ProtonUp-Qt**.

2. Choose **Lutris** as the target.

3. Click **Install Version** → select **GE-Proton** or **Lutris-GE-Proton** (latest recommended).

4. It will download and install automatically.


Once done, open **Lutris**, edit your game, and select the installed **GE-Proton** version under the **Runner options → Wine version** dropdown.


---

## ⚙️ 7. Tips for Better Performance

Linux gaming can be smooth and optimized by enabling the right tools.  
This section explains how to enable **Feral GameMode**, **Vulkan**, **MangoHud**, and how to **tweak Wine/Proton settings** in Lutris for better FPS and stability.

---

### 🧠 7.1 Enable Feral GameMode

**GameMode** is a tool developed by **Feral Interactive** to optimize your system performance during gaming sessions.  
It temporarily adjusts CPU governor settings, I/O priority, and more.

#### 🧩 Installation

```bash
sudo apt install gamemode
```

#### 🧩 Verification

Check if it’s installed correctly:

```bash
gamemoded -t
```

It should output something like:

```bash
GameMode service is running
```



---

### 🧩 7.2 Enable Vulkan Support

**Vulkan** is a modern graphics API offering better performance than OpenGL, especially in games running through Wine or Proton.

#### 🧩 Check Vulkan Support

Run this command to verify your Vulkan installation:

```bash
vulkaninfo | less
```

If you see your GPU listed and no major errors, Vulkan is active.

#### 🧩 Install Vulkan Packages

**For NVIDIA:**

```bash
sudo apt install nvidia-driver-535 nvidia-vulkan-icd
```

**For AMD:**

```bash
sudo apt install mesa-vulkan-drivers
```

**For Intel:**

```bash
sudo apt install mesa-vulkan-drivers
```

After installing, restart your system.

#### 🧩 Enable Vulkan in Lutris

1. Open **Lutris**.

2. Right-click the game → **Configure** → **Runner options**.

3. Ensure **DXVK/VKD3D** is enabled (these use Vulkan to translate DirectX 9/10/11/12).

4. Under “DXVK version”, select a recent version (recommended: latest stable).

---

### 🎮 7.3 Use MangoHud for FPS, CPU, and GPU Monitoring

**MangoHud** is a lightweight performance overlay that displays FPS, CPU/GPU usage, temperature, frame times, and more while gaming.

#### 🧩 Installation

```bash
sudo apt install mangohud
```

#### 🧩 For Lutris Games

1. Open **Lutris**.

2. Right-click your game → **Configure**.

3. Go to **System options**.

4. In the **Environment variables** section, add:
   
   ```ini
   MANGOHUD=1
   ```

5. Save and launch the game — the overlay should appear on the top-left corner.

You can toggle MangoHud on/off in-game with `Shift + F12`.

#### 🧩 For Native Games (non-Lutris)

You can run native Linux games directly with MangoHud:

```bash
mangohud ./YourGameExecutable
```

#### 🧩 Customizing MangoHud

MangoHud can be customized using a config file.

Create or edit:

```bash
nano ~/.config/MangoHud/MangoHud.conf
```

Example settings:

```ini
fps
frametime
gpu_temp
cpu_temp
gpu_usage
cpu_usage
vram
ram
engine_version
version
```

o apply your config, just run MangoHud normally — it will use this file automatically.

---

### 🍷 7.4 Tweak Wine / Proton Settings in Lutris

Fine-tuning Wine or Proton helps with compatibility and performance.

#### 🧩 Accessing Settings

1. In **Lutris**, right-click your game → **Configure**.

2. Open the **Runner options** tab.

Here are the key options:

| Option                         | Description                                                                       |
| ------------------------------ | --------------------------------------------------------------------------------- |
| **Wine version**               | Choose the Wine or Proton build (GE-Proton recommended for better compatibility). |
| **DXVK/VKD3D**                 | Translates DirectX to Vulkan — keep it enabled.                                   |
| **Esync / Fsync**              | Reduces CPU overhead and improves performance (enable both if supported).         |
| **Enable VAAPI**               | Hardware video decoding — optional for some games.                                |
| **Windowed (virtual desktop)** | Useful for older games that don’t handle fullscreen well.                         |
| **Environment Variables**      | Add variables like `MANGOHUD=1`, `DXVK_HUD=1`, or tweak performance parameters.   |

Example useful environment variables:

```bash
DXVK_HUD=fps,frametimes
DXVK_ASYNC=1
PROTON_LOG=1
```

#### 🧩 Wine Configuration (Advanced)

You can open the Wine configuration panel used by Lutris:

```bash
winecfg
```

From there, you can:

- Set the Windows version (e.g., Windows 10).

- Configure audio and graphics drivers.

- Manage libraries (DLL overrides) for specific games.





## 📚 8. Useful Resources


- 🔗 Lutris official website: [https://lutris.net](https://lutris.net)

- 🔗 ProtonUp-Qt GitHub: [GitHub - DavidoTek/ProtonUp-Qt: Install and manage GE-Proton, Luxtorpeda & more for Steam and Wine-GE & more for Lutris with this graphical user interface.](https://github.com/DavidoTek/ProtonUp-Qt)

- 🔗 GE-Proton releases: [Releases · GloriousEggroll/proton-ge-custom · GitHub](https://github.com/GloriousEggroll/proton-ge-custom/releases)



## 🧩 9. Example Setup: Installing a Windows Game

Example: **The Witcher 3 (GOG)**

1. Download the GOG installer.

2. Open Lutris → “+” → Add Game → Runner = Wine.

3. Set the executable to the installer file.

4. Under “Runner options”, select your **GE-Proton** version.

5. Launch the installer → Install → Then run the game.

---

## 🏁 Conclusion

You now have a complete Linux gaming setup using **Lutris** and **ProtonUp-Qt**!  
This combination gives you the best of both worlds — **the freedom of Linux** and **the compatibility of Windows games**.

Happy gaming! 🕹️🐧


