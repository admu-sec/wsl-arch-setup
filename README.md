# Arch Linux WSL Setup

A quick setup guide for installing Arch Linux on WSL (Windows Subsystem for Linux) with terminal tools like fastfetch & cmatrix.

---

## Prerequisites

Make sure WSL is installed and enabled on your machine.

Open **PowerShell as Administrator** and verify WSL:

```powershell
wsl --version
```

Check available distributions:

```powershell
wsl --list --online
```

> 💡 Arch Linux should appear in the list as `archlinux`. If WSL is not installed, run: `wsl --install`

---

## Installation

### 1. Install Arch Linux

```powershell
wsl --install archlinux
```

Installation takes a few minutes. Once complete, Arch Linux launches automatically.

> 💡 Arch opens as root by default — this is normal. A user account is created in the next step.

---

### 2. Update the System

```bash
pacman -Syu
```

Confirm with `Y` when prompted.

---

### 3. Create a User

```bash
useradd -m -G wheel yourusername
passwd yourusername
```

Replace `yourusername` with your own username.

---

### 4. Install Terminal Tools

```bash
pacman -S fastfetch cmatrix cava
```

> 💡 If cava asks for a jack provider, select **2) pipewire-jack** for best WSL compatibility.

---

### 5. Autostart fastfetch

```bash
echo "fastfetch" >> ~/.bashrc
echo "source ~/.bashrc" >> ~/.bash_profile
```

Restart the terminal — fastfetch will now appear automatically on startup.

> 💡 If you accidentally added fastfetch twice, remove the duplicate with:
> ```bash
> sed -i '0,/fastfetch/!{/fastfetch/d}' ~/.bashrc
> ```

---

## Automated Setup

Clone the repo and run the setup script:

```bash
chmod +x setup.sh
./setup.sh
```

Or run directly:

```bash
curl -s https://raw.githubusercontent.com/admu-sec/wsl-arch-setup/main/setup.sh | bash
```

---

## Opening Arch Linux WSL

- Search for **Arch Linux** in the Start menu
- Or run in PowerShell:
  ```powershell
  wsl -d archlinux
  ```
- Add it as a profile in **Windows Terminal** for quick access

---

## Uninstall

```powershell
wsl --unregister archlinux
```

> ⚠️ **Warning:** This removes the entire filesystem and all files within Arch. Windows files are not affected.

---

## Quick Reference

| Command | Description |
|---|---|
| `pacman -Syu` | Update all packages |
| `pacman -S packagename` | Install a package |
| `pacman -R packagename` | Remove a package |
| `fastfetch` | Display system info |
| `cmatrix` | Matrix animation (exit: `Ctrl+C`) |
| `wsl --list --verbose` | List installed WSL distributions |
| `wsl --unregister archlinux` | Uninstall Arch WSL |
