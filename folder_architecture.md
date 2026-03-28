# 🐧 Linux Developer Folder Architecture Guide

A simple, scalable, and clean way to organize your Linux home directory as a developer.

---

# 🎯 Philosophy

Organize by **purpose**, not by file type.

- `apps/` → software you run

- `projects/` → things you build

- `learning/` → things you study

- `dev/` → reusable code/tools

Keep your `$HOME` clean and predictable.

---

# 🧱 Recommended Folder Structure

```
~
├── apps/          # manually installed applications
├── projects/      # all development work
├── dev/           # scripts, snippets, templates
├── tools/         # SDKs and large dev tools
├── learning/      # tutorials, courses, study material
├── notes/         # personal notes & documentation
├── dotfiles/      # config backups
├── Downloads/     # temporary files only
├── Documents/     # personal documents
```

---

# 📁 Folder Breakdown

## 📦 apps/ (Manual Software)

For apps you download manually (not via package manager).

Examples:

- JasperReports

- Postman

- AppImages

```
~/apps/
  jasperreports/
  postman/
  thunderbird/
```

👉 Tip: Keep each app in its own folder.

---

## 💻 projects/ (Your Code)

Main workspace.

```
~/projects/
  personal/
  work/
  experiments/
  archived/
```

Examples:

```
~/projects/personal/portfolio-site/
~/projects/work/api-server/
```

👉 Always use Git inside projects.

---

## 🛠 dev/ (Reusable Assets)

```
~/dev/
  scripts/
  snippets/
  templates/
```

Use for:

- automation scripts

- boilerplate code

- reusable utilities

---

## ⚙️ tools/ (SDKs & Heavy Tools)

```
~/tools/
  android-sdk/
  flutter/
  node/
```

👉 Avoid cluttering system directories.

---

## 📚 learning/ (Tutorials & Courses)

```
~/learning/
  topics/
    python/
    linux/
    devops/
  courses/
  notes/
  resources/
```

Examples:

```
~/learning/topics/python/
~/learning/courses/docker-mastery/
```

---

## 🧠 notes/ (Knowledge Base)

```
~/notes/
  dev/
  linux/
  debugging/
  ideas/
```

👉 Store:

- commands

- fixes

- architecture ideas

---

## ⚡ dotfiles/ (Config Backup)

```
~/dotfiles/
  .bashrc
  .gitconfig
  nvim/
```

👉 Version control this folder.

---

## 📥 Downloads/

Temporary storage only.

👉 Clean regularly.

---

# ⚙️ Software Installation Rules

## ✅ Package Manager (Preferred)

Example: Mozilla Thunderbird

- Installed via `apt`, `dnf`, etc.

- Lives in system directories (`/usr/bin`, `/opt`)

👉 You don’t manage its location.

---

## ✅ Manual Installations

Store in:

```
~/apps/
```

Example:

```
~/apps/jasperreports/
```

---

## ⚡ Optional: Make Apps Global

```
ln -s ~/apps/jasperreports/jasperreports /usr/local/bin/jasperreports
```

---

# 🧠 Best Practices

## 1. Keep Naming Clean

❌ bad:

```
project-final-v2-last
```

✅ good:

```
task-manager-api
```

---

## 2. Separate Concerns

- Don’t mix tutorials with projects

- Don’t store apps in Downloads

- Don’t mix personal and dev files

---

## 3. Use Git Everywhere

Track:

- projects/

- dotfiles/

- notes/

---

## 4. Archive Instead of Delete

```
~/projects/archived/
```

---

## 5. Backups Are Critical

Backup:

- projects/

- dotfiles/

- notes/

- KeePassXC database (.kdbx)

---

## 6. Clean Regularly

- `Downloads/`

- unused apps

- old experiments

---

# 🚀 Quick Setup

```bash
mkdir -p ~/apps \
         ~/projects/{personal,work,experiments,archived} \
         ~/dev/{scripts,snippets,templates} \
         ~/tools \
         ~/learning/{topics,courses,notes,resources} \
         ~/notes \
         ~/dotfiles
```

---

# 🧭 Summary

| Folder    | Purpose             |
| --------- | ------------------- |
| apps/     | Installed software  |
| projects/ | Development work    |
| dev/      | Reusable code/tools |
| tools/    | SDKs                |
| learning/ | Tutorials & courses |
| notes/    | Knowledge base      |
| dotfiles/ | Config backups      |

---

# 🏁 Final Rule

> If you don’t know where to put something:

- Is it code? → `projects/`

- Is it software? → `apps/`

- Is it learning material? → `learning/`

- Is it knowledge? → `notes/`

---

Keep it simple. Consistency beats complexity.
