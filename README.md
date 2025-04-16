# =============================================
# Arch Linux + i3-gaps Quick Install (archinstall)
# =============================================

# 1. Create Bootable USB (from Linux)
dd if=archlinux.iso of=/dev/sdX bs=4M status=progress && sync
reboot

# 2. Connect to Wi-Fi (in Arch ISO)
iwctl
> station wlan0 connect YOUR_SSID
> exit

# 3. Launch Automated Installer
archinstall

# --- Guided Setup ---
# [Disk]
# - Disk: /dev/nvme0n1 (UEFI)
# - Filesystem: ext4 (root), FAT32 (boot)

# [System]
# - Hostname: arch-i3
# - Locale: en_US.UTF-8
# - Keymap: us

# [User]
# - Root password: ********
# - Add user: yourname (sudo)

# [Packages] 
# base linux linux-firmware nano sudo networkmanager 
# grub efibootmgr xorg i3-gaps dmenu alacritty feh picom firefox

# [Services]
# - Bootloader: GRUB (UEFI)
# - Network: NetworkManager (enable)

# [Install]
# Proceed? [Y/n] Y

# 4. Reboot into New System
reboot

# 5. First Login & i3 Setup
startx  # Generates default config

# Edit i3 config:
nano ~/.config/i3/config
# Add these lines:
exec --no-startup-id nm-applet
exec --no-startup-id picom --daemon
exec --no-startup-id feh --bg-scale ~/wallpaper.jpg

# 6. Optional Tools
sudo pacman -S --needed neovim ranger pulseaudio pavucontrol
