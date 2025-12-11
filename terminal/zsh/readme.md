# **Zsh & .zshrc – Quick README**

## **What is Zsh?**

Zsh (**Z Shell**) is an improved shell that replaces Bash.  
It provides:

- Better auto-completion

- Suggestions

- Custom prompts

- Plugins & themes

- Aliases & functions

---

## **Install Zsh**

### Linux (Debian/Ubuntu)

```bash
sudo apt install zsh
```

### Set it as default shell

```bash
chsh -s $(which zsh)
```

---

## **What is `.zshrc`?**

`~/.zshrc` is the **main configuration file** for Zsh.  
It runs every time you open a terminal.

You can create it if it does not exist:

```bash
touch ~/.zshrc
```

---

## **Common `.zshrc` Settings**

### PATH

```bash
export PATH="$HOME/bin:/usr/local/bin:$PATH"
```

### Aliases

```bash
alias ll="ls -la"
alias gs="git status"
```

### Enable auto-completion

```bash
autoload -Uz compinit
compinit
```

### Basic prompt

```bash
PROMPT="%n@%m:%~ %# "
```

---

## **Using Oh-My-Zsh (optional)**

Install:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Enable plugins in `.zshrc`:

```bash
plugins=(git)
```

Change theme:

```bash
ZSH_THEME="agnoster"
```

---

## **Apply changes**

```bash
source ~/.zshrc
```


