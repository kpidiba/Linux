# 📌 How to Create a Desktop Shortcut & System Launcher on Linux

This guide explains how to:

- Create a **desktop shortcut** for any program

- Create a **system-wide launcher** (`.desktop` entry) so your app appears in the application menu and global search

- Make the shortcut executable and recognized by the system

Works on **Ubuntu, Pop!_OS, Linux Mint**, and most Linux distributions using GNOME or similar desktops.

---

## 🚀 1. Create a `.desktop` File

A Linux application shortcut is a **`.desktop` file**.  
It describes:

- The program name

- The icon

- The executable command

- The categories (optional)

### Example shortcut file

Create a file:

```md
myapp.desktop
```

Add the following:

```ini
[Desktop Entry]
Type=Application
Name=My App
Comment=My custom application
Exec=/path/to/your/app
Icon=/path/to/icon.png
Terminal=false
Categories=Utility;
```

---

## 🖥️ 2. Add the Shortcut to the Desktop

1. Copy your `.desktop` file to your Desktop:

```bash
cp myapp.desktop ~/Desktop/
```

2. Make it executable:

```bash
chmod +x ~/Desktop/myapp.desktop
```

3. Right-click → **Allow Launching** (GNOME/Pop!_OS)

You now have a clickable desktop shortcut.

---

## 🗂️ 3. Add the Shortcut to the System Menu (Application Launcher)

Place the `.desktop` file in one of these directories:

### **For your user only:**

```bash
mkdir -p ~/.local/share/applications
cp myapp.desktop ~/.local/share/applications/
```

### **For all users (system-wide):**

```bash
sudo cp myapp.desktop /usr/share/applications/
```

Then refresh the desktop database:

```bash
update-desktop-database ~/.local/share/applications/
```

(or skip — GNOME usually detects changes automatically)

Your program will now appear when you:

- Press **Super (Windows Key)** and search

- Open **Show Applications**

- Use **rofi**, **Albert**, **Ulauncher**, etc.

---

## 🎨 4. Finding Icons for Your Shortcut

Icons can be:

- PNG or SVG files

- System icons located under:
  
  - `/usr/share/icons/`
  
  - `/usr/share/pixmaps/`
  
  - `~/.local/share/icons/`

Example:

```ini
Icon=/usr/share/pixmaps/myapp.png
```

---

## 🔧 5. Testing the Shortcut

Run:   

```bash
gtk-launch myapp
```

f `Name=` or the filename is “myapp.desktop”, this command should launch it.

---

## ✔️ Summary

| Task              | Location                       | Notes                                |
| ----------------- | ------------------------------ | ------------------------------------ |
| Desktop Shortcut  | `~/Desktop/myapp.desktop`      | Needs `chmod +x` + “Allow Launching” |
| User Menu Entry   | `~/.local/share/applications/` | Appears in search for this user      |
| System Menu Entry | `/usr/share/applications/`     | Requires sudo; visible to all users  |
| Update Cache      | `update-desktop-database`      | Optional                             |

---

If you want, I can generate a **template `.desktop` file**, or write a version of this README customized for your specific application.
