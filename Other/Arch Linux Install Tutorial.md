In case I need to reinstall it. If you already experienced with this, scroll down to view the commands-only version.

>[!WARNING]
>This only works for devices that use modern UEFI/GPT filesystem tables instead of legacy BIOS. If you don't know what any of this means, as long as your laptop was made after like 2015 you should be okay.
# Setup
## Boot into the Live CD
1. Go to the [Arch Linux download website](https://archlinux.org/download/) to download a minimal installation image
2. Use [ventoy](https://github.com/ventoy/Ventoy) to put the ISO onto a USB
3. Put your USB onto the computer of choice you want to install Arch Linux to
4. Boot into the live environment. This usually involves hitting F12 or DEL while the computer is turning on, and booting into the USB
## Connecting to the Internet
1. Check to see if your computer has blocked networking 
   ```bash
   rfkill
   # If anything says "blocked" unblocked them
   rfkill unblock all
   ```

2. Enter networking tools
   ```bash
   iwctl
   ```
   
   The command line should now show `[iwd]` instead of the usual `root@archiso`.
3. Check the name of your wifi device
   ```bash
   device list
   ``` 

   It should show a table with `Name Address Powered Adapter Mode`. If it says on, this next step is optional.
4. Enable the network device
   ```bash
   device <name> set-property Powered on
   ```
   
5. Connect to the internet
   ```bash
   # See your wifi devices
   station list 
   # If it does not say it's scanning run
   station <name> scan
   # Search a network to connect to
   station <name> get-networks
   # Choose a network to connect to (you may need to enter the wifi password)
   station <name> connect <network-name>
   ```
 
6. Finally, exit out of iwctl by simply running `exit`. Check if you are connected. 
   ```bash
   ping wikipedia.org
   ``` 
   If it says something like, `64 bytes from...` you are connected. Hit Ctrl + C to stop pinging.
# Setup Partition
1. Check the partitions on your computer. Run `lsblk` to view them. It should output a table of partitions and drives that the system can read. You want to use the drive of the computer and NOT the USB that the live environment is running in. The partition that the USB is using might look something like 
   ```
   ├─sda
     ├─ventoy
     └─sda1 
   ```
   
2. Run cfdisk.
   ```bash
   cfdisk /dev/<disk-to-partition>
   ```

3. Set the partition scheme to look like this:

| Partition      | Size                         | Type               |
| -------------- | ---------------------------- | ------------------ |
| `/dev/<disk>1` | `1G`                         | `Linux Filesystem` |
| `/dev/<disk>2` | `4G`                         | `Linux Filesystem` |
| `/dev/<disk>3` | `<all remaining disk space>` | `Linux Filesystem` |
4. Format the partitions. The first partition will be your boot partition. The second disk will be your swap and third will be your root partition.
   ```bash
   mkfs.ext4 /dev/<root-partition>
   mkfs.fat -F 32 /dev/<boot-partition>
   mkswap /dev/<swap-partition>
   ```

5. Mount the partitions.
   ```bash
   mount /dev/<root-partition> /mnt
   mount --mkdir /dev/<boot-partition> /mnt/boot/efi
   swapon /dev/<swap-partition>
   ```
# System Installation and Setup
## Installation
1. Download your base system with pacstrap. If you have an computer using an AMD chip, replace `intel-ucode` with `amd-ucode`. Replace `nano` with your terminal text editor of choice, if you would like.
   ```bash
   pacstrap -K /mnt base base-devel linux linux-firmware sof-firmware intel-ucode nano networkmanager grub efibootmgr
   ```

2. Generate your system fstab.
   ```bash
   genfstab /mnt > /mnt/etc/fstab
   ```

3. Change root into your system.
   ```bash
   arch-chroot /mnt
   ```
## Setup
1. Set your timezone. List the timezones available with `timedatectl list-timezones`.
   ```bash
   ln -sf /usr/share/zoneinfo/<Area>/<Location> /etc/localtime
   ```

2. Sync system clock.
   ```bash
   hwclock --systohc
   ```

3. Use your text editor to edit `/etc/locale.gen` and uncomment the locale you want to use. Write the changes and load the locales.
   ```bash
   locale-gen
   ```

4. Use your text editor to create the `/etc/locale.conf` file and add `LANG=en_US.UTF-8` for english.

5. Set your hostname in `/etc/hostname` with your text editor.

6. Set your password
   ```bash
   passwd
   ```

7. Create your main user account
   ```bash
   useradd -m -G wheel -s /bin/bash <username>
   passwd <username>
   ```

8. Enable sudo for your user in the sudoers file. 
   ```bash
   EDITOR=nano visudo
   ```
   
   You will need to uncomment the line
   ```sh
   %wheel ALL=(ALL:ALL) ALL
   ```

9. Enable networkmanager
   ```bash
   systemctl enable NetworkManager
   ```

10. Install grub
   ```bash
   grub-install /dev/<disk>
   grub-mkconfig -o /boot/grub/grub.cfg
   ```

11. Exit the chroot with `exit` and unmount all partitions with `umount -a`. Then reboot.
# Commands-only
```bash
rfkill unblock all
iwctl station <name> connect <network>
ping wikipedia.org
lsblk
cfdisk /dev/<disk>
mkfs.ext4 /dev/<rtdsk>
mkfs.fat -F 32 /dev/<btdsk>
mkswap /dev/<swpdsk>
mount /dev/<rtdsk> /mnt
mount --mkdir /dev/<btdsk> /mnt/boot/efi
swapon /dev/<swpdsk>
pacstrap -K /mnt base base-devel linux linux-firmware sof-firmware intel-ucode neovim networkmanager grub efibootmgr
genfstab /mnt > /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/<Area>/<Location> /etc/localtime
hwclock --systohc
nvim /etc/locale.gen
locale-gen
# LANG=en.US_UTF-8
nvim /etc/locale.conf
nvim /etc/hostname
passwd
useradd -m -G wheel -s /bin/bash <name>
passwd <name>
# %wheel ALL=(ALL:ALL) ALL
EDITOR=nvim visudo
systemctl enable NetworkManager
grub-install /dev/<disk>
grub-mkconfig -o /boot/grub/grub.cfg
exit
umount -a
reboot
```
