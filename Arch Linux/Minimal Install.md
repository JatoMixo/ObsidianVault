Download the ISO from [Arch Linux Downloads](https://archlinux.org/download/) and plug it into the computer. After booting it select `Arch Linux Install Medium x86_64`
# Connect to wifi
You can use `iwctl` to connect to wifi.
```bash
iwtcl
```
Now you will presented with a prompt.
```bash
station wlan0 show # Show state of iwtcl
station wlan0 scan # Start scanning the network

station wlan0 connect WIFI_NAME # Connect to the wifi

quit
```
# Set up temporary keymap
Set a temporary keymap for changing keyboard layout, this is only temporary and we'll have to change other files later to make it permanent.
```bash
loadkeys LANG
```
Change `LANG` to your language for example `es` (Spanish)

# Define system partitions
To define the system partitions use `cfdisk`.
```bash
cfdisk
```

Now select the label type, for basic usage you should select:
- `GPT`: In case you have a disk bigger than 2TB and your machine uses UEFI
- `DOS`: Otherwise

Now create 3 partitions:
## /dev/sda1
This will be the partition containing the bootloader, create it with 512MB of space as a primary partition.
## /dev/sda2
This will be the main partition, create it with as big as you want, making sure to leave space for the SWAP. Create it as a primary partition.
## /dev/sda3
This will be used as the SWAP. Create it the remaining space as a primary partition, then go into type and change it to `82. Linux Swap / Solaris`.

Now write the changes to the disk and exit the application.
# Formatting the partitions
The partitions will be formated as:
- `/dev/sda1`: Vfat
- `/dev/sda2`: EXT4
- `/dev/sda3`: SWAP

```bash
mkfs.vfat -F 32 /dev/sda1
```
```bash
mkfs.ext4 /dev/sda2
```
```bash
mkswap /dev/sda3
swapon
```

# Mount the partitions
Mount `/dev/sda2` on `/mnt` and `/dev/sda1` on `/mnt/boot`.
```bash
mount /dev/sda2 /mnt
```
```bash
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
```
# Install important packages
```bash
pacstrap /mnt linux linux-firmware base base-devel networkmanager wpa_supplicant grub
```
# Create the fstab file
An fstab file contains data regarding system partitions. It should be stored on `/etc/fstab` (`/mnt/etc/fstab` during the installation).

To generate the fstab file and store it in the proper file type.
```bash
genfstab -U /mnt > /mnt/etc/fstab
```
# Enter into the system
To enter into your actual Arch Linux machine you can use the following command
```bash
arch-chroot /mnt
```
# Define passwords and users
To define a password for the root user you can type
```bash
passwd
```

After that you should create a user, give a password to it and the corresponding groups.
```bash
useradd -m NAME # Create a user with a personal folder
passwd NAME # Give the user a password

usermod -aG GROUP NAME # Give the user a determined group
```

You user has to be in the `wheel` group for general administration actions or changing to another user.

Some recommended groups are:
- `tty`: Access to serial ports and devices connected to them.
- `audio`: Direct access to sound hardware.
- `storage`: To access the content of external USB devices
- `video`: To access video capture devices
# Install the sudo package
It should be installed with the latest version, but just in case type
```bash
pacman -S sudo
```
# Install nano as a temporary text editor
We'll need to modify some files, easiest way is to install the nano text editor.
```bash
pacman -S nano
```
# Modify /etc/sudoers
Open it with nano (`nano /etc/sudoers`) and uncomment the following line:
```
%wheel ALL=(ALL:ALL) ALL
```

This will allow the users of the `wheel` group to type `sudo su`, enter the password and become root.
# Configure regions
Edit the file `/etc/locale.gen` and enable your corresponding locations.
In my case I'm going to enable `en_US` and `es_ES` with UTF-8.

Now run the following command to generate the necessary files.
```bash
locale-gen
```
# Modify the keymap of the console permanently
Create a file `/etc/vconsole.conf` and type
```
KEYMAP=es
```
To set the keymap to spanish.
# Install grub
```bash
grub-install /dev/sda
```

Now create a config file for it.
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```
# Set the hostname
Write the hostname in `/etc/hostname`, or you can use the command
```bash
echo NAME > /etc/hostname
```
# Writing several hosts
Edit `/etc/hosts` and type
```
127.0.0.1        localhost
::1              localhost
127.0.0.1        HOSTNAME HOSTNAME.localhost
```
# Reboot
```bash
exit # Back to install medium
poweroff # Shut down your machine
```
Remove the live USB and boot again your machine.
# Enable network services
```bash
systemctl start NetworkManager
systemctl enable NetworkManager

systemctl enable wpa_supplicant
```
# Install git
```bash
pacman -S git
```
# Set your timezone
To check your current time use `timedatectl`.
```bash
timedatectl
```

If you want to list the possible timezones use the command.
```bash
timedatectl list-timezones
```

And to set a specific timezone use
```bash
timedatectl set-timezone ZONE/SUBZONE
```