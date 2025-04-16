```bash
# 1. Boot into Arch ISO (UEFI)
dd if=archlinux.iso of=/dev/sdX bs=4M status=progress
reboot

# 2. Connect to internet (Wi-Fi)
iwctl
station wlan0 connect SSID
exit

# 3. Launch archinstall
archinstall

# 4. Guided Configuration
# - Disk: UEFI + ext4
# - Hostname: arch-i3
# - Locale: en_US.UTF-8
# - User: create with sudo
# - Packages: base linux linux-firmware nano sudo networkmanager grub efibootmgr xorg i3-gaps dmenu alacritty feh picom firefox
# - Bootloader: GRUB
# - Network: NetworkManager
# - Install

# 5. Post-install
reboot
login

# 6. Configure i3
startx  # Generate config
nano ~/.config/i3/config
# Add:
exec --no-startup-id nm-applet
exec --no-startup-id picom --daemon
exec --no-startup-id feh --bg-scale ~/wallpaper.jpg

# 7. Optional tools
sudo pacman -S neovim ranger pulseaudio

# Arch Linux + i3 WM Quick Install Guide

## 1. Boot & Prep
```bash
dd if=archlinux.iso of=/dev/sdX bs=4M status=progress
reboot


## 2. Network (Wi-Fi)

iwctl
station wlan0 connect SSID
exit


## 3. Run archinstall

archinstall

- Disk: UEFI + ext4
- Hostname: `arch-i3`
- Locale: `en_US.UTF-8`
- Packages: `base linux linux-firmware nano sudo networkmanager grub efibootmgr xorg i3-gaps dmenu alacritty feh picom firefox`
- Bootloader: GRUB
- Network: NetworkManager

## 4. Post-Install

reboot
startx
nano ~/.config/i3/config

Add:

exec --no-startup-id nm-applet
exec --no-startup-id picom --daemon
exec --no-startup-id feh --bg-scale ~/wallpaper.jpg


## 5. Optional

sudo pacman -S neovim ranger pulseaudio


## Keybinds
- Win+Enter: Terminal
- Win+d: App launcher
- Win+Shift+r: Reload config
```
