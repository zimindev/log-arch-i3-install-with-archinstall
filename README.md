# log-arch-i3-install-use-archinstall

# **Arch Linux + i3 WM Installation with `archinstall`**  
*(Simplified guided setup for UEFI systems)*  

---

## **🔸 Step 1: Boot into Arch ISO**  
1. **Download** the latest Arch ISO from [archlinux.org](https://archlinux.org/download/).  
2. **Flash to USB**:  
   ```bash
   dd if=archlinux-2024.07.01-x86_64.iso of=/dev/sdX bs=4M status=progress
   ```  
   *(Replace `sdX` with your USB drive, e.g., `sdb`)*  
3. **Boot from USB**: Enter BIOS (usually `F2`/`Del`), disable Secure Boot, select USB.  

---

## **🔸 Step 2: Launch `archinstall`**  
1. **Connect to Internet**:  
   - **Ethernet**: Should work automatically.  
   - **Wi-Fi**: Run `iwctl` and connect:  
     ```bash
     iwctl  
     station wlan0 scan  
     station wlan0 connect "Your-WiFi"  
     exit  
     ```  
2. **Start Installer**:  
   ```bash
   archinstall
   ```  

---

## **🔸 Step 3: Guided Configuration**  
### **1. Disk Setup**  
- Select **"UEFI"** partitioning.  
- Choose your disk (e.g., `/dev/nvme0n1`).  
- Select **"Ext4"** for filesystem (or Btrfs if preferred).  

### **2. Core Settings**  
- **Hostname**: `arch-i3`  
- **Timezone**: `Europe/Kyiv` (or your region).  
- **Locales**: Uncheck all except `en_US.UTF-8`.  

### **3. User Account**  
- **Root Password**: Set a secure password.  
- **Create User**: Add your username with `sudo` privileges.  

### **4. Packages**  
- **Base**: `base linux linux-firmware`  
- **Additional**:  
  ```bash
  nano sudo networkmanager grub efibootmgr xorg i3-gaps dmenu alacritty feh picom firefox
  ```  

### **5. Bootloader**  
- Select **"GRUB"** (for UEFI).  

### **6. Network**  
- Enable **`NetworkManager`** for Wi-Fi/Ethernet.  

### **7. Profile (Optional)**  
- Skip profiles (we’re manually installing i3).  

---

## **🔸 Step 4: Install & Reboot**  
1. Confirm settings and start installation.  
2. After completion:  
   ```bash
   reboot
   ```  
3. Remove USB when prompted.  

---

## **🔸 Step 5: Post-Installation Setup**  
### **1. Login**  
- Use your username/password.  

### **2. Start i3**  
```bash
startx
```  
- i3 will prompt to generate a config. Press `Enter`.  
- Set `Win` (Mod) key as default.  

### **3. Autostart Apps**  
Edit `~/.config/i3/config`:  
```bash
exec --no-startup-id nm-applet  
exec --no-startup-id picom --daemon  
exec --no-startup-id feh --bg-scale ~/wallpaper.jpg  
```  

### **4. Optional Tools**  
```bash
sudo pacman -S neovim ranger pulseaudio  
```  

---

## **🔸 Key i3 Shortcuts**  
| Shortcut          | Action                     |  
|-------------------|----------------------------|  
| `Win + Enter`     | Open terminal (`alacritty`) |  
| `Win + d`         | Launch app (`dmenu`)        |  
| `Win + Shift + r` | Reload i3 config           |  

---

## **✅ Done!**  
Your **Arch Linux + i3** system is ready. Customize further with:  
- **Polybar** (`sudo pacman -S polybar`)  
- **Rofi** (replaces `dmenu`)  
- **Nitrogen** (wallpaper manager)  

For NVIDIA drivers:  
```bash
sudo pacman -S nvidia nvidia-utils
```  

Enjoy your minimal, blazing-fast setup! 🚀
