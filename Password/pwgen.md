# README — `pwgen`

`pwgen` is a command-line utility to generate random passwords on Linux (and other Unix-like systems). It aims to create passwords that are both secure and, by default, somewhat “human-friendly” (pronounceable) — or, if you prefer, fully random and complex. [LinuxConfig+2Opensource.com+2](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)

---

## Table of Contents

- Overview

- Installation

- Basic Usage

- Command-line Options

- Examples

- Security Considerations

- Use Cases & Tips

---

## Overview

- By default, `pwgen` outputs pronounceable (i.e. easier-to-remember) passwords. [ServerWatch+2Linux Documentation+2](https://www.serverwatch.com/guides/generate-secure-passwords-with-pwgen/?utm_source=chatgpt.com)

- It also offers many flags to customize the generated passwords: length, number of passwords, inclusion of uppercase letters, numbers, symbols, exclusion of ambiguous characters, and more. [LinuxConfig+2UbuntuMint+2](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)

- While default output is “user-friendly,” `pwgen` can produce truly random, harder-to-guess passwords suitable for sensitive usage. [Linux Tips+2ServerWatch+2](https://linux-tips.us/how-to-generate-sufficiently-complex-passwords-in-the-terminal/?utm_source=chatgpt.com)

---

## Installation

You can install `pwgen` via your Linux distribution’s package manager. For example:

```bash
# Debian / Ubuntu / Mint
sudo apt install pwgen

# RHEL / CentOS / Fedora
sudo yum install pwgen
# or (on newer Fedora / RHEL)
sudo dnf install pwgen

# Arch Linux
sudo pacman -S pwgen

# Alpine Linux
sudo apk add pwgen

# OpenSUSE
sudo zypper install pwgen

# Gentoo
sudo emerge -a sys-apps/pwgen
```

Once installed, the `pwgen` command becomes available in your shell. [LFCS Certification Guide+2UbuntuMint+2](https://www.tecmint.com/generate-random-password-linux/?utm_source=chatgpt.com)

---

## Basic Usage

The general syntax is:

```css
pwgen [options] [pw_length] [pw_count]
```

- `pw_length`: desired length (in characters) of each password.

- `pw_count`: number of passwords to generate.

If you omit both, `pwgen` produces default-length (8-character) passwords (one per line, by default). [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)

---

## Command-line Options

Here are some of the most useful options/flags:

| Flag(s)              | Description                                                                                                                                                                                                                                                 |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-s`, `--secure`     | Generate completely random, “hard” passwords (less pronounceable) — more secure. [Opensource.com+2ServerWatch+2](https://opensource.com/article/21/7/generate-passwords-pwgen?utm_source=chatgpt.com)                                                       |
| `-y`, `--symbols`    | Include special characters (symbols) in the password. [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)                                                                    |
| `-n`, `--numerals`   | Include numeric digits. [UbuntuMint+1](https://www.ubuntumint.com/generate-random-passwords-linux/?utm_source=chatgpt.com)                                                                                                                                  |
| `-c`, `--capitalize` | Include at least one uppercase letter. [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)                                                                                   |
| `-B`                 | Avoid ambiguous characters (like `l`, `1`, `O`, `0`) — useful to reduce confusion when reading/typing. [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)                   |
| `-r` `<chars>`       | Exclude specific characters from the password. (e.g. exclude visually similar letters) [UbuntuMint+1](https://www.ubuntumint.com/generate-random-passwords-linux/?utm_source=chatgpt.com)                                                                   |
| `-v`                 | Include vowels (or — in some documentation — generate passwords excluding vowels). Behavior may vary; check `man pwgen`. [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com) |
| `-1`                 | Force output of one password per line. Helpful when generating multiple passwords. [LinuxConfig+1](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)                                       |

You can combine these flags to tailor password characteristics (length, complexity, readability) to your needs. [LinuxConfig+2UbuntuMint+2](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)

---

## Examples

Here are some practical examples of using `pwgen`:

- Generate a single default (8-character) password:
  
  ```bash
  pwgen
  ```

- Generate 5 passwords, each 8 characters (default):
  
  ```bash
  pwgen 8 5
  ```

- Generate a single 12-character password:
  
  ```bash
  pwgen 12 1
  ```

- Generate 10 passwords, each 16 characters:
  
  ```bash
  pwgen 16 10
  ```

- Generate a secure (non-pronounceable) 12-character password (no symbols):
  
  ```bash
  pwgen -s 12 1
  ```

- Generate a 20-character password including at least one capital letter:
  
  ```bash
  pwgen -c 20 1
  ```

- Generate 3 passwords of 15 characters each including symbols and capital letters:
  
  ```bash
  pwgen -sc 15 3
  ```

- Generate a 14-character password avoiding ambiguous characters:
  
  ```bash
  pwgen -B 14 1
  ```

- Generate a 10-character password including at least one number:
  
  ```bash
  pwgen -0 -n 10 1
  ```

- Generate 4 passwords, each 8 characters long, containing only numerals:
  
  ```bash
  pwgen -n 8 4
  ```

These examples illustrate the flexibility of `pwgen` — you can quickly produce passwords ranging from “easy to remember” to “complex and secure.” [LinuxConfig+2UbuntuMint+2](https://linuxconfig.org/how-to-use-a-command-line-random-password-generator-pwgen-on-linux?utm_source=chatgpt.com)

---

## Security Considerations

- Using default mode (pronounceable passwords) may produce passwords that are easier to memorize — but potentially less random and more vulnerable to targeted attacks than fully random passwords. [ServerWatch+2Linux Documentation+2](https://www.serverwatch.com/guides/generate-secure-passwords-with-pwgen/?utm_source=chatgpt.com)

- For more security-sensitive tasks (such as system passwords, root passwords, database credentials, etc.), prefer using flags like `-s`, `-y`, `-n`, `-c`, `-B`, and a sufficiently long length (e.g. 12–32 characters). [LinuxBlog.io+2ServerWatch+2](https://linuxblog.io/generating-secure-passwords-for-your-linux-server/?utm_source=chatgpt.com)

- `pwgen` output can be scripted — making it useful for automation (e.g. creating user accounts, generating many passwords at once, etc.). [ServerWatch+1](https://www.serverwatch.com/guides/generate-secure-passwords-with-pwgen/?utm_source=chatgpt.com)

---

## Use Cases & Tips

- **Quick manual password creation** — when you need a password fast for a user account, database, etc.

- **Bulk password generation** — generate many passwords at once (with desired complexity) for multiple accounts.

- **Scripting / automation** — integrate `pwgen` into shell scripts for provisioning servers/accounts.

- **Balancing memorability vs. security** — by default `pwgen` tries to make passwords somewhat pronounceable; with options, you can dial up security as needed.

- **Avoid ambiguous characters** when readability or manual typing is required (e.g. avoid `l` vs `1`, `O` vs `0`).

---

## Conclusion

`pwgen` is a versatile, lightweight, and widely available tool for generating passwords directly from the command line. With a few simple options, you can produce anything from easy-to-remember passwords to highly secure, complex passwords suitable for servers and sensitive services. Whether you need one password or dozens, `pwgen` gives you the flexibility — and the convenience — to generate them quickly.

If you like, I can also provide a **sample shell script** (or alias) that wraps `pwgen` into a “one-command” password generator for you (e.g. `newpass`) — would you like me to build that for you now?
