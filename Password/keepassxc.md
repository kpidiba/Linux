hs if needed.

---

# 🔐 KeePassXC Password Manager – Usage Guide

## 📌 Overview

This repository/document describes how I use **KeePassXC** to securely manage passwords, secrets, and sensitive information.

KeePassXC is an **open-source, offline-first password manager** that stores data in an encrypted `.kdbx` database file.

This guide covers:

- Database structure

- Security best practices

- Backup strategy

- Daily usage tips

---

## 🧩 Installation

### 🐧 Linux

KeePassXC is available on all major Linux distributions.

#### ✅ Ubuntu / Debian / Pop!_OS

```bash
sudo apt update
sudo apt install keepassxc
```

#### ✅ Fedora

```bash
sudo dnf install keepassxc
```

#### ✅ Arch Linux / Manjaro

```bash
sudo pacman -S keepassxc
```

#### ✅ Flatpak (Recommended for sandboxing)

```bash
flatpak install flathub org.keepassxc.KeePassXC
```

Run with :

```bash
flatpak run org.keepassxc.KeePassXC
```

---

### 🪟 Windows

#### Method 1: Official Installer (Recommended)

1. Go to the official website:  
   👉 [https://keepassxc.org](https://keepassxc.org)

2. Download the **Windows Installer (.exe)**

3. Run the installer

4. Follow the setup wizard

5. Launch **KeePassXC** from the Start Menu

✔ Auto-updates supported  
✔ Browser integration available

---

## 📁 Default Database Locations (Recommended)

### Linux

```bash
~/Documents/Passwords/
```

### Windows

```bash
C:\Users\<YourUser>\Documents\Passwords\
```

💡 Tip:  
Name your database clearly:

```ts
personal-passwords.kdbx
```

---

## 📂 Recommended Database Structure

```plsql
KeePass Database
│
├── 🔐 01_Personal
│   ├── Emails
│   ├── Social Media
│   ├── Devices
│   └── Private Notes
│
├── 💼 02_Development
│   ├── Git (GitHub, GitLab)
│   ├── Databases
│   ├── APIs & Tokens
│   ├── SSH Keys (references)
│   └── Cloud Services
│
├── 🌐 03_Websites_Owned
│   ├── Domain Registrars
│   ├── Hosting Providers
│   ├── Admin Panels
│   └── Email Servers
│
├── 🏦 04_Finance
│   ├── Bank Accounts
│   ├── Mobile Money
│   └── Subscriptions
│
└── 🗄️ 99_Archive
    └── Old / Unused Credentials
```

---

## 🔑 Entry Best Practices

Each entry should contain:

- **Title** → Clear and explicit

- **Username**

- **Password**

- **URL** (if applicable)

- **Notes**:
  
  - Account purpose
  
  - Linked email
  
  - 2FA status
  
  - Expiration date (tokens, APIs)

### Example

```md
Title: GitLab – Personal Account
Username: david@example.com
Password: ********
URL: https://gitlab.com
Notes:
- 2FA enabled (Authenticator)
- Used for personal projects
```

---

## 🔐 Security Settings (Recommended)

### Master Password

- Minimum **20–30 characters**

- Use a **passphrase**, not a single word

- Never reuse it anywhere else

### Database Security

- Encryption: **AES-256**

- Key derivation: **Argon2id**

- Increase memory & iterations if your PC allows it

### Auto-Lock

- Lock after **5–10 minutes**

- Lock when screen is locked or system sleeps

---

## 🔁 Backup Strategy (Very Important)

### Rule: **3–2–1 Backup Strategy**

- **3 copies**

- **2 different media**

- **1 off-site**

### Example

- Primary:
  
  ```bash
  ~/Documents/Passwords/keepass.kdbx
  ```

- Local encrypted backup (weekly):
  
  - External USB

- Off-site encrypted backup:
  
  - Cloud (Nextcloud / Google Drive / Proton Drive)
  
  - ZIP encrypted with a **different password**

⚠️ Never store the database unencrypted.

---

## 🧪 Versioning & Changes

- Do **not** sync the `.kdbx` file with Git

- Keep manual backups before:
  
  - Changing master password
  
  - Major cleanup
  
  - OS reinstall

---

## 🧰 Useful KeePassXC Features

- Password generator

- Password strength analysis

- Entry history (rollback)

- Auto-type

- Browser integration (optional)

- TOTP (2FA) storage

---

## ❗ Things to Avoid

- ❌ Storing master password anywhere

- ❌ Uploading database without encryption

- ❌ Using short or reused passwords

- ❌ Sharing the database file casually

---

## 📚 References

- Official site: [https://keepassxc.org](https://keepassxc.org)

- Documentation: https://keepassxc.org/docs/

---
