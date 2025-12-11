# Tilix with ZSH Configuration Guide

This guide explains how to configure Tilix terminal to use ZSH while keeping GNOME Terminal unaffected.

## 📋 Prerequisites

- Pop!_OS (or any Ubuntu/Debian-based distribution)

- Tilix terminal emulator installed

- ZSH shell

## 🚀 Installation

### 1. Install Tilix (if not already installed)

```bash
sudo apt update
sudo apt install tilix
```

### 2. Install ZSH and Oh My ZSH

```bash
# Install ZSH
sudo apt install zsh

# Install Oh My ZSH (optional but recommended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## ⚙️ Configuration Methods

### Method 1: Set ZSH only for Tilix (Recommended)

This method keeps GNOME Terminal completely unchanged.

1. **Open Tilix preferences:**
   
   - Right-click anywhere in Tilix
   
   - Select "Preferences"

2. **Configure profile:**
   
   - Go to **"Profile"** → **"Command"** tab
   
   - Check **"Run command as login shell"**
   
   - In the **"Command"** field, enter:
   
   ```bash
   /bin/zsh -l
   ```

3. **Apply changes:**
- Click "Apply" or "Close"

- Restart Tilix for changes to take effect

### Method 2: Set ZSH as Default Shell

Configure ZSH globally but with different settings per terminal.

1. **Set ZSH as default shell:**

```bash
chsh -s $(which zsh)
```

2. **Log out and log back in** for changes to take effect globally.

### Method 3: Terminal Detection in .zshrc

Create conditional configurations based on the terminal emulator.

Add this to your `~/.zshrc` file:

```bash
# Detect if running in Tilix
if [[ $TERM == "xterm-tilix" ]] || [[ $TILIX_ID ]]; then
    # Tilix-specific configurations
    export TILIX_CONFIG=1
    
    # Example: Set different theme for Tilix
    ZSH_THEME="agnoster"
    
    # Example: Enable specific plugins only for Tilix
    plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
    
    # Add any Tilix-specific aliases or functions
    alias tilix-info="echo 'Running in Tilix with ZSH'"
else
    # Default configurations for other terminals
    ZSH_THEME="robbyrussell"
    plugins=(git)
fi
```

## 🔧 Change Default Terminal (Optional)

If you want to make Tilix your default terminal emulator:

### Method A: Using update-alternatives

```bash
sudo update-alternatives --config x-terminal-emulator
```

Select Tilix from the list.

### Method B: Using GNOME Control Center

1. Open **Settings** → **Default Applications**

2. Set Tilix as the default terminal

### Method C: Using gsettings

```bash
gsettings set org.gnome.desktop.default-applications.terminal exec tilix
gsettings set org.gnome.desktop.default-applications.terminal exec-arg ""
```

## 🔄 Restore GNOME Terminal as Default

If you want to revert back:

```bash
gsettings set org.gnome.desktop.default-applications.terminal exec gnome-terminal
gsettings set org.gnome.desktop.default-applications.terminal exec-arg ""
```

## 🎨 Customizing Tilix with ZSH

### Theme Compatibility

Some ZSH themes work better with Tilix's features:

1. **Powerlevel10k:** Excellent for Tilix's split panes
   
   ```bash
   git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
   ```

        Then set `ZSH_THEME="powerlevel10k/powerlevel10k"` in your `.zshrc`

2. **Agnoster:** Clean and works well with Tilix

### Tilix-Specific ZSH Functions

Add to your `.zshrc` for Tilix enhancements:

```bash
# Tilix VTE configuration (fixes some issues)
if [ $TILIX_ID ] || [ $VTE_VERSION ]; then
    source /etc/profile.d/vte.sh
fi

# Quick session saving (Tilix feature)
alias save-session='tilix --session ~/.config/tilix/sessions/my-session.json'
```

## 🐛 Troubleshooting

### Issue: ZSH not launching in Tilix

**Solution:** Ensure the path is correct:

- Use `which zsh` to find your ZSH path

- Update Tilix command to use the correct path

### Issue: Colors look different

**Solution:** Set terminal type explicitly in `.zshrc`:

```bash
if [[ $TILIX_ID ]]; then
    export TERM=xterm-256color
fi
```

### Issue: GNOME Terminal also uses ZSH after changing default

**Solution:** This is expected if you use Method 2. Use Method 1 for terminal-specific configuration.

## 📝 Verification

To verify your setup:

1. **Check in Tilix:**
   
   ```bash
   echo $SHELL
   echo $0
   ```

2. **Check in GNOME Terminal:**
   
   ```bash
   echo $SHELL
   ```

3. **Verify terminal detection:**
   
   ```bash
   
   ```














