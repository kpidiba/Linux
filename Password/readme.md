# 🔐 Password Management on Linux

### GNOME Keyring • KDE Wallet • Bitwarden / Vaultwarden • KeePassXC

This README explains how to manage passwords securely on Linux using common desktop and cross-platform tools. It covers:

- What each tool is

- When to use which solution

- How to install and configure them

- Pros & cons of each

- Security considerations

# 📌 Table of Contents

1. Overview

2. Which tool should I use?

3. GNOME Keyring

4. KDE Wallet

5. Bitwarden

6. Vaultwarden (self-hosted Bitwarden)

7. KeePassXC

8. Security Best Practices

9. Conclusion

---

# 🧩 Overview

Linux offers multiple password management options depending on your workflow:

| Tool              | Type                   | Best For               | Sync?                   | Desktop Integration |
| ----------------- | ---------------------- | ---------------------- | ----------------------- | ------------------- |
| **GNOME Keyring** | Built-in key store     | GNOME users            | No                      | Excellent           |
| **KDE Wallet**    | Built-in key store     | KDE/Plasma users       | No                      | Excellent           |
| **Bitwarden**     | Cloud password manager | Multi-device sync      | Yes (cloud)             | Good                |
| **Vaultwarden**   | Self-hosted Bitwarden  | Privacy, organizations | Yes (self-hosted)       | Good                |
| **KeePassXC**     | Local encrypted vault  | Offline users, USB use | Optional via cloud file | Medium              |

---

# 🤔 Which Tool Should I Use?

### ✅ Use **GNOME Keyring** if:

- You use **GNOME**, Ubuntu, Pop!_OS, Fedora Workstation…

- You want tight system integration (SSH keys, Wi-Fi, app secrets)

- You do **not** need multi-device password syncing

### ✅ Use **KDE Wallet** if:

- You use **KDE Plasma** (Kubuntu, Manjaro KDE, openSUSE KDE…)

- You want native integration with KDE apps

- You store secrets for desktop applications only

### ✅ Use **Bitwarden** if:

- You want a **full cloud password manager**

- You need mobile + browser extension + desktop sync

- You prefer ready-to-use hosted service

### ✅ Use **Vaultwarden** if:

- You want **Bitwarden but self-hosted**

- You already have a private server/VPS/NAS

- You want zero monthly fees but full sync

### ✅ Use **KeePassXC** if:

- You want **offline/local-only password storage**

- You prefer a portable database (`.kdbx`)

- You want maximum control over your password file

- You want to sync via your own method (Syncthing, Nextcloud, USB)

---

# 🟦 GNOME Keyring

GNOME Keyring is the default secret storage for GNOME environments.

## ⭐ Features

- Stores passwords, Wi-Fi keys, SSH keys, certificates

- Unlocks automatically on login

- Integrates with GNOME apps (Chrome, VSCode, NetworkManager)

- No cloud sync

## 🛠 Installation

On GNOME-based distros, it is **preinstalled**.

If missing:

```bash
sudo apt install gnome-keyring
```

Or on Fedora:

```bash
sudo dnf install gnome-keyring
```

## 🔧 Using GNOME Keyring

- Opens automatically when logging in

- Use *Passwords and Keys* (formerly Seahorse):

- ```bash
  sudo apt install seahorse
  ```

Run:

```bash
seahorse
```

You can:

- Add passwords

- Manage SSH keys

- View saved Wi-Fi passwords

- Create new keyrings

## 📌 When to use GNOME Keyring

Use it if you’re a **GNOME desktop user** and only need local secrets for apps — not a full-fledged password manager.

---

# 🟪 KDE Wallet

KDE Wallet is the KDE Plasma equivalent of GNOME Keyring.

## ⭐ Features

- Native Plasma integration (Konqueror, KMail, NetworkManager)

- Uses the *KWallet* standard

- Protects secrets with GPG or a password

## 🛠 Installation

Preinstalled on KDE Plasma.  
If needed:

```bash
sudo apt install kwalletmanager
```

## 🔧 Using KDE Wallet

Launch Wallet Manager:

```bash
kwalletmanager5
```

- Create a new wallet

- Set GPG or passphrase protection

- Allow apps to store credentials

## 📌 When to use KDE Wallet

Use it if you're on **KDE Plasma** and want system-level secret storage.

---

# 🟩 Bitwarden

Bitwarden is a fully featured cloud password manager.

## ⭐ Features

- Automatic multi-device sync

- Browser extensions (Chrome, Edge, FF)

- Command-line interface

- Sharing & organization vaults

- Mobile apps

- Encrypted cloud storage

## 🛠 Installation

### Desktop App:

```bash
sudo snap install bitwarden
```

Or using AppImage:

```bash
wget https://vault.bitwarden.com/download/?app=desktop&platform=linux
chmod +x Bitwarden*.AppImage
```

### Browser Extension:

Find “Bitwarden” in Firefox/Chrome extensions store.

### CLI:

```bash
npm install -g @bitwarden/cli
```

## 🔧 Using Bitwarden

- Create a Bitwarden account

- Add and organize passwords into collections

- Enable autofill in browser extension

- Sync devices automatically

## 📌 When to use Bitwarden

Choose Bitwarden if you want **easy sync, mobile apps, and cloud convenience**.

---

# 🟧 Vaultwarden (Self-hosted Bitwarden)

Vaultwarden is a lightweight Bitwarden-compatible server written in Rust.

## ⭐ Features

- All Bitwarden features

- Host on your own server

- Very lightweight (runs on Raspberry Pi, VPS, Synology)

- Compatible with official Bitwarden clients

## 🛠 Installation (Docker Example)

```bash
docker run -d \
  --name vaultwarden \
  -v /vw-data:/data \
  -p 8080:80 \
  --restart always \
  vaultwarden/server:latest
```

Access your server at:  
`http://your-server-ip:8080`

## 📌 When to use Vaultwarden

Perfect if you want a **self-hosted, privacy-friendly password manager** with Bitwarden features.

---

# 🟨 KeePassXC

KeePassXC is a local password manager using `.kdbx` encrypted vaults.

## ⭐ Features

- Completely offline

- Open source

- Cross-platform (Linux/Windows/Mac)

- Supports Yubikey, Argon2, SSH agent

- Portable database file

## 🛠 Installation

### Ubuntu/Debian:

```bash
sudo apt install keepassxc
```

### Fedora:

```bash
sudo dnf install keepassxc
```

### Arch:

```bash
sudo pacman -S keepassxc
```

## 🔧 Using KeePassXC

1. Open KeePassXC

2. Create a new database

3. Choose a strong master password

4. Add entries using Categories

5. Enable browser integration (optional)

6. Set up auto-lock and clipboard timeout

## Optional Sync Methods

- Syncthing

- Nextcloud

- Dropbox

- Git (encrypted vault only – not recommended if careless)

- USB key

## 📌 When to use KeePassXC

Pick KeePassXC if you want **full control**, **offline security**, or **portability**.

---

# 🛡 Security Best Practices

✔ Use a **strong master password**  
✔ Enable **2FA** (Bitwarden/Vaultwarden)  
✔ Keep **system auto-lock** enabled  
✔ Use **Argon2** encryption parameters for KeePassXC  
✔ Do **not** store your password database in email/unencrypted cloud  
✔ Enable browser password autofill only when necessary

---
