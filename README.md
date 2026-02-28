Arch Linux WSL Setup Guide
1. Prerequisites
Make sure WSL is installed and enabled on your machine.

Open PowerShell as Administrator
Verify WSL version:

powershellwsl --version

Check available distributions:

powershellwsl --list --online

💡 Arch Linux should appear in the list as archlinux. If WSL is not installed, run: wsl --install


2. Install Arch Linux WSL
powershellwsl --install archlinux
Installation takes a few minutes. Once complete, Arch Linux launches automatically.

💡 Arch opens as root by default — this is normal. A user account is created in the next step.


3. Initial Configuration
3.1 Update the system
bashpacman -Syu
Confirm with Y when prompted by pacman.
3.2 Create a user
bashuseradd -m -G wheel yourusername
passwd yourusername
Replace yourusername with your own username.

4. Install Terminal Tools
bashpacman -S fastfetch cmatrix cava

If cava asks for a jack provider, select 2) pipewire-jack for best WSL compatibility.


5. Autostart fastfetch
bashecho "fastfetch" >> ~/.bashrc
echo "source ~/.bashrc" >> ~/.bash_profile
Restart the terminal — fastfetch should now appear automatically on startup.

💡 If you accidentally added fastfetch twice, remove the duplicate with:
sed -i '0,/fastfetch/!{/fastfetch/d}' ~/.bashrc


6. Opening Arch Linux WSL

Search for Arch Linux in the Start menu
Or run in PowerShell: wsl -d archlinux
Add it as a profile in Windows Terminal for quick access


7. Uninstall (if needed)
powershellwsl --unregister archlinux
⚠️ Warning: This removes the entire filesystem and all files within Arch. Windows files are not affected.

8. Quick Reference
CommandDescriptionpacman -SyuUpdate all packagespacman -S packagenameInstall a packagepacman -R packagenameRemove a packagefastfetchDisplay system infocmatrixMatrix animation (exit: Ctrl+C)wsl --list --verboseList installed WSL distributionswsl --unregister archlinuxUninstall Arch WSL

