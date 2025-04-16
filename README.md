### 🖥️ Arch Linux + i3 via `archinstall` (Terminal-Only Log)

```bash
# 1. Check internet
ping archlinux.org

# 2. Start guided installer
archinstall
```

---

### 📋 Inside `archinstall` (pick these)

```text
Language:             en_US
Keyboard layout:      us
Drive:                /dev/sda (or your disk)
Disk Use:             Use entire disk (ext4)
Bootloader:           systemd-boot
Swap:                 file (or none)
Hostname:             archi3
Root password:        [your password]
User account:         yourname (add to wheel group)
User password:        [your password]
Profile:              Desktop
Desktop environment:  i3
Audio:                PipeWire
Kernel:               linux
Networking:           NetworkManager
Extra packages:       firefox vim neofetch htop
Install bootloader:   Yes
Start installation:   Yes
```

---

### 💻 After install

```bash
# Reboot system
reboot

# Login as your user
# i3 will start after login
```
