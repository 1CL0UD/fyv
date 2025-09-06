# fyv — Smart AUR Package Manager Wrapper for Arch Linux

> **“Forget what you installed. `fyv` remembers for you.”**

`fyv` is a lightweight, intelligent wrapper around `yay` or `paru` that **automatically logs every successfully installed package** to a persistent list (`~/pkglist.txt` by default). Perfect for Arch Linux users who want to:

- ✅ Never lose track of manually installed packages
- ✅ Reinstall their entire setup with one command
- ✅ Keep a clean, auto-updated manifest of their system

---

## 🚀 Features

- 🧠 **Auto-logging**: Every successful `fyv -S <pkg>` adds the package to your log file.
- 📦 **Bulk install**: `fyv -flist pkglist.txt` installs everything + logs successes (skips failures gracefully).
- 🔄 **No duplicates**: Packages already in the log are not added again.
- 💪 **Robust**: Failed installs are skipped — script continues.
- 🎨 **Colorized output** (optional): Clear visual feedback.
- ⚙️ **Configurable**: Set `FYV_PKG_LIST` to change log location.
- 🆘 **Help included**: `fyv --help` shows usage.

---

## 🛠️ Installation

1. **Save the script** to `~/bin/fyv`:

   ```bash
   mkdir -p ~/bin
   curl -o ~/bin/fyv https://gist.githubusercontent.com/.../fyv.sh  # or copy-paste from your editor
   ```

2. **Make it executable**:

   ```bash
   chmod +x ~/bin/fyv
   ```

3. **Add `~/bin` to your PATH** (if not already):

   Add this to your `~/.zshrc` or `~/.bashrc`:

   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

   Then reload:

   ```bash
   source ~/.zshrc
   ```

4. **(Optional) Bootstrap your package list**:

   ```bash
   pacman -Qqen > ~/pkglist.txt
   ```

---

## 🧪 Usage

### Install & Auto-Log a Package

```bash
fyv -S zen-browser-bin
```

→ Installs the package and adds it to `~/pkglist.txt` (if not already there).

### Bulk Install from File

```bash
fyv -flist ~/pkglist.txt
```

→ Installs each package in the file.  
→ **Only logs successfully installed packages.**  
→ **Skips failed packages — does not stop.**

### Show Help

```bash
fyv --help
```

### Customize Log File Path

```bash
export FYV_PKG_LIST="$HOME/.config/fyv/packages.txt"
fyv -S some-package  # → logs to custom path
```

---

## 📂 Default Log File

By default, packages are logged to:

```
~/pkglist.txt
```

You can change this by setting the `FYV_PKG_LIST` environment variable.

---

## 💡 Pro Tips

- Run `fyv -flist pkglist.txt` after a fresh Arch install to restore your entire setup.
- Add comments to your `pkglist.txt` — `fyv` ignores lines starting with `#`.
- Re-run `fyv -flist pkglist.txt` anytime — it’s safe and idempotent.
- Use with dotfiles repos or backup systems for full system reproducibility.

---

## 🧩 Example `pkglist.txt`

```txt
# Browsers
brave-bin
firefox
zen-browser-bin

# Dev Tools
visual-studio-code-bin
docker-compose
lazygit

# Communication
discord
telegram-desktop-bin
```

---

## 🤝 Contributing / Extending

Want to add features?

- `fyv -R <pkg>` → uninstall + auto-remove from log
- `fyv --sync` → regenerate pkglist from current system
- `fyv --export-clean` → export sorted, comment-free list
- Git auto-commit on change

Open an issue or fork and customize!

---

## 🧑‍💻 Author

Built by you — for you.  
Because Arch should remember what you installed.

---

> “I don’t trust my memory. I trust `fyv`.” — You, probably.
