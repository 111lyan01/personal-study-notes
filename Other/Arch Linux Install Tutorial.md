In case I need to reinstall it

>[!WARNING]
>This only works for devices that use modern UEFI/GPT filesystem tables instead of legacy BIOS. If you don't know what any of this means, as long as your laptop was made after like 2015 you should be okay.
# Setup
## Boot into the Live CD
1. Go to the [Arch Linux download website](https://archlinux.org/download/) to download a minimal installation image
2. Use [ventoy](https://github.com/ventoy/Ventoy) to put the ISO onto a USB
3. Put your USB onto the computer of choice you want to install Arch Linux to
4. Boot into the live environment. This usually involves hitting F12 or DEL while the computer is turning on, and booting into the USB
## Connecting to the Internet
1. Check to see if your computer has blocked networking by running `rfkill`. If anything under the list of `SOFT` and `HARD` says `blocked`, run `rfkill unblock all.
2. Enter networking tools with `iwctl`. The command line should now should `[iwd]` instead of the usual `root@archiso`.
3. Check the name of your wifi device by typing `device list`. It should show a table with `Name   Address   Powered   Adapter   Mode`. If it says on, this next step is optional.
4. Enable the network device by running `device <name> set-property Powered on`.
5. Check the wifi status by running `station list`. If it does not say it's scanning, run `station <name> scan`.
6. Search for a network to connect to. Run `station <name> get-networks`.
7. The previous command will output a list of networks. Choose one to connect to and connect with `station <name> connect <network-name>`. It may prompt you to enter the wifi password.
8. Finally, exit out of iwctl by simply running `exit`. Check if you are connected by running `ping wikipedia.org`. If it says something like, `64 bytes from...` you are connected. Hit Ctrl + C to stop pinging.
# Setup Partition
1. Check the partitions on your computer. Run `lsblk` to view them. It should output a table of partitions and drives that the system can read. You want to use the drive of the computer and NOT the USB that the live environment is running in. The partition that the USB is using might look something like 
   ```
   ├─sda
     ├─ventoy
     └─sda1 
   ```
2. Run `cfdisk`.